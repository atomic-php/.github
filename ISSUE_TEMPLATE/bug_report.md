name: Bug report
description: Create a report to help us improve
labels: bug
body:
  - type: textarea
    id: description
    attributes:
      label: Description
      description: What happened and what did you expect?
    validations:
      required: true
  - type: input
    id: versions
    attributes:
      label: Versions
      description: PHP, package version, OS
  - type: textarea
    id: reproduction
    attributes:
      label: Reproduction
      description: Minimal, reproducible example (code + steps)

