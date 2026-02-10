# {{ cookiecutter.project_name }}
A _Python_ [what am i?] that [what do i do?] build with uv.

## Prerequisites
* Python >= 3.13, you can use for example [uv](https://docs.astral.sh/uv/guides/install-python/) to manage that
* [uv](https://docs.astral.sh/uv/getting-started/installation/)

## Installing dependencies
```bash
make install
```

## Tests and checks
To run all tests and checks:
```bash
make check
```

To run all tests (unit and integration):
```bash
make test
```

### unit-tests
To just run unit-tests:
```bash
make unit-test
```

### integration-tests
To just run integration-tests:
```bash
make integration-test
```

### Auto-formatting
```bash
make auto-format
```

### Linting
```bash
make lint
```

### Check types
```bash
make type-check
```
