## Introduction

Python runtime CI checks.

## Usage

```yaml
name: Python CI

on: [push, pull_request]

jobs:
  format:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: NASA-ACROSS/github-actions-python-checks@latest
        with:
          check-type: format

  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: NASA-ACROSS/github-actions-python-checks@latest
        with:
          check-type: test
          ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}

  types:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: NASA-ACROSS/github-actions-python-checks@latest
        with:
          check-type: types
          ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}
```

## Inputs

| Name              | Description                                                     | Default | Required |
| ----------------- | --------------------------------------------------------------- | ------- | -------- |
| `check-type`      | Type of check to run. Options: `format`, `test`, `types`        | N/A     | Yes      |
| `ssh-private-key` | SSH private key for accessing private repositories during setup | N/A     | No       |
| `changed-files`   | Only check changed files for formatting (Python only)           | `true`  | No       |
