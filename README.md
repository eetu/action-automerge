# actions

## automerge

Automatically merges dependabot PRs, but can be extended to merge PRs from other actors as well

```yaml
name: Automerge

on:
  pull_request:
    branches: [main]

# Allow github token to merge PR
permissions:
  contents: write
  pull-requests: write

jobs:
  automerge:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - name: Automerge Dependabot PR
        uses: eetu/action-automerge@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

Using optional parameters

```yaml
steps:
  - name: Automerge My PRs using squash
    uses: eetu/action-automerge@v1
    with:
      actors: |
        - eetu
      merge_method: squash
      interval: 30
      github_token: ${{ secrets.GITHUB_TOKEN }}
```
