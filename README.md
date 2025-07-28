# 🐳 Docker Automation Toolkit

This repository provides a set of **GitHub Composite Actions** and a **reusable workflow**
to simplify Docker image builds, tagging, and registry configuration for local or internal environments.

## 🧩 Composite Actions

- 📛 [get-repo-name](/get-repo-name/) - Extracts the current repository name from the GitHub context.
- 🛠️ [setup-builder-for-local-registry](/setup-builder-for-local-registry/) - Sets up a Docker buildx builder that communicates with an internal or self-hosted Docker registry using TLS.

## 🔁 Reusable Workflow

- [build-docker-image](/.github/workflows/build-docker-image.yml) - Reusable workflow to build and push
  multi-platform Docker images
  - 🔒 Supports TLS-authenticated internal registries
  - 🏗 Configures Docker builder via composite action
  - 🏷 Tags images by version and `latest`
  - 🧾 Uploads image digests as artifacts

### Usage Example

```YAML
jobs:
  docker-release:
    uses: StanislawHorna/Docker/.github/workflows/build-docker-image.yml@main
    with:
      registry-fqdn: docker.internal.local
      image-version: 25-32-1
    secrets:
      GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      VAULT_ROLE_ID: ${{ secrets.VAULT_ROLE_ID }}
      VAULT_SECRET_ID: ${{ secrets.VAULT_SECRET_ID }}
```
