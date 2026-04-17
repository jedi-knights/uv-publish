# uv-publish

[![Coverage](https://img.shields.io/badge/Coverage-0%25-red)](https://jedi-knights.github.io/uv-publish/)

A GitHub Action that publishes a Python package to any PyPI-compatible registry using [uv](https://github.com/astral-sh/uv), with configurable retry logic for transient network failures.

## Usage

```yaml
- uses: jedi-knights/uv-publish@v0
  with:
    publish-url: https://your-registry.example.com/pypi/simple
    username: ${{ secrets.REGISTRY_USER }}
    password: ${{ secrets.REGISTRY_TOKEN }}
```

## Inputs

| Input | Required | Default | Description |
|---|---|---|---|
| `publish-url` | yes | — | PyPI-compatible registry URL |
| `username` | yes | — | Registry username |
| `password` | yes | — | Registry password or API token |
| `dist-dir` | no | `dist` | Directory containing `.whl` and `.tar.gz` artifacts |
| `max-attempts` | no | `3` | Maximum publish attempts before failing |
| `retry-delay-seconds` | no | `10` | Seconds before first retry; doubles on each subsequent attempt |

## Outputs

| Output | Description |
|---|---|
| `artifact-count` | Number of artifacts published |
