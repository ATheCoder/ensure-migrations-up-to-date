# Ensure Migrations Up‑to‑Date

A GitHub Action that ensures your pull request branch includes all migration files present in a target branch (default: `staging`). It will fail if any migrations exist in the compare branch but are missing from your branch.

## Inputs

| Name              | Description                            | Required | Default             |
|-------------------|----------------------------------------|----------|---------------------|
| `migrations-dir`  | Path to your migrations folder         | false    | `src/migrations/`   |
| `compare-branch`  | Branch to compare against              | false    | `staging`           |

## Usage

Add this action to your workflow to automatically catch missing migrations before merging. For example, in `.github/workflows/ci.yml`:

```yaml
name: CI

on:
  pull_request:
    # optionally only run when migrations change
    paths:
      - 'src/migrations/**'
      - '.github/actions/ensure-migrations-up-to-date/**'

jobs:
  ensure-migrations:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Verify migrations sync
        uses: athecoder/ensure-migrations-up-to-date@v2.0
        with:
          migrations-dir: 'db/migrations/'      # override if your migrations live elsewhere
          compare-branch: 'main'                # override if not using 'staging'
```

### Minimal Example

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: athecoder/ensure-migrations-up-to-date@v2.0
```

## Output

This action does not set any outputs. It exits with a non-zero status if missing migrations are detected, causing your workflow to fail.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

# Ensure Migrations Up‑to‑Date

A GitHub Action that ensures your pull request branch includes all migration files present in a target branch (default: `staging`). It will fail if any migrations exist in the compare branch but are missing from your branch.

## Inputs

| Name              | Description                            | Required | Default             |
|-------------------|----------------------------------------|----------|---------------------|
| `migrations-dir`  | Path to your migrations folder         | false    | `src/migrations/`   |
| `compare-branch`  | Branch to compare against              | false    | `staging`           |

## Usage

Add this action to your workflow to automatically catch missing migrations before merging. For example, in `.github/workflows/ci.yml`:

```yaml
name: CI

on:
  pull_request:
    # optionally only run when migrations change
    paths:
      - 'src/migrations/**'
      - '.github/actions/ensure-migrations-up-to-date/**'

jobs:
  ensure-migrations:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Verify migrations sync
        uses: athecoder/ensure-migrations-up-to-date@v2.0
        with:
          migrations-dir: 'db/migrations/'      # override if your migrations live elsewhere
          compare-branch: 'main'                # override if not using 'staging'
```

### Minimal Example

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: athecoder/ensure-migrations-up-to-date@v2.0
```

## Output

This action does not set any outputs. It exits with a non-zero status if missing migrations are detected, causing your workflow to fail.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

