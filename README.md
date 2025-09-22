# Atomic

High‑performance, PSR‑friendly PHP building blocks. Our focus is on:

- Performance first: compile‑time optimizations and zero‑overhead execution paths
- Simplicity: small, focused libraries with clear responsibilities
- Interop: strict adherence to PSR standards (PSR‑7/11/12/15)
- Quality: comprehensive tests, static analysis, and consistent code style

Packages
- http-kernel — Ultra‑slim PSR‑15 kernel with compile‑time middleware pipelines
- router — Blazingly fast PSR‑7/15 router with static and parameterized routes
- container — Lightweight PSR‑11 DI container with compile‑time preparation

Quick start (container + router + kernel)

```php
<?php

use Atomic\Container\ContainerBuilder;
use Atomic\Http\Kernel as HttpKernel;
use Atomic\Http\MiddlewareStack;
use Atomic\Router\Router;
use Atomic\Router\Middleware\RouterMatchMiddleware;
use Atomic\Router\Middleware\RouteDispatchMiddleware;
use Nyholm\Psr7\Response;
use Psr\Container\ContainerInterface;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Server\MiddlewareInterface;
use Psr\Http\Server\RequestHandlerInterface;

// 1) Build container and register services/middleware
$builder = new ContainerBuilder();

// Router instance with a route
$router = new Router();
$router->add('GET', '/health', fn () => new Response(200, [], 'ok'));

$builder->set(Router::class, $router);

// Middleware registered as shared factories and resolved by class name
$builder->set(RouterMatchMiddleware::class, fn (ContainerInterface $c) => new RouterMatchMiddleware($c->get(Router::class)), shared: true);
$builder->set(RouteDispatchMiddleware::class, fn () => new RouteDispatchMiddleware(), shared: true);

// Example custom middleware
class AuthMiddleware implements MiddlewareInterface {
    public function process(ServerRequestInterface $request, RequestHandlerInterface $handler): ResponseInterface
    {
        // authorize...
        return $handler->handle($request);
    }
}

$builder->set(AuthMiddleware::class, fn () => new AuthMiddleware(), shared: true);

$container = $builder->compile();

// 2) Compile middleware pipeline with container-backed resolution
$stack = new MiddlewareStack($container);
$stack->add(RouterMatchMiddleware::class);
$stack->add(AuthMiddleware::class);
$stack->add(RouteDispatchMiddleware::class);

// 3) Create kernel; final handler is unused because dispatch ends pipeline
$fallback = new class implements RequestHandlerInterface {
    public function handle(ServerRequestInterface $request): ResponseInterface { return new Response(500); }
};

$kernel = new HttpKernel($fallback, $stack);

// 4) Handle PSR-7 request
// $response = $kernel->handle($request);
```

Guiding principle
“An idiot admires complexity, a genius admires simplicity.” — Terry A. Davis
