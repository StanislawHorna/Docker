# 📛 Get Repository Name

This GitHub Composite Action extracts the repository name **without the owner** from the GitHub context
and returns it in lowercase, ready to be used as Docker image name.

## Outputs

| Name   | Description                               |
| ------ | ----------------------------------------- |
| `name` | The repository name (lowercase, no owner) |

---

## 🚀 Usage

```YAML
jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Get repository name
        id: repo
        uses: StanislawHorna/Docker/get-repo-name@main

      - name: Print repo name
        run: echo "Repository name is ${{ steps.repo.outputs.name }}"
```
