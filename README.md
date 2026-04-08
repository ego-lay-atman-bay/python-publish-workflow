# python-publish-workflow
 A workflow to publish a library to pypi and upload the wheel to the releases page

## Usage:

Copy and paste [.github/workflows/python-publish.yml](./.github/workflows/python-publish.yml) to your repository with the same path.

## Reusable workflow

>[!IMPORTANT]
> Reusable workflows are currently not supported yet
> https://github.com/pypa/gh-action-pypi-publish/issues/166

>[!NOTE]
> This workflow uses pypi publishing with [trusted publishers](https://docs.pypi.org/trusted-publishers/).
> This also will assume that `requirements.txt` exists, and it will also build according to the `pyproject.toml` file.

```yaml
name: "Upload Python Package"

on:
  release:
    types: [published]
    
  workflow_dispatch:

permissions:
  contents: write
  id-token: write

jobs:
  publish:
    uses: ego-lay-atman-bay/python-publish-workflow/.github/workflows/python-publish-reusable.yml@main
    with:
        python_version: '3.14'
```
