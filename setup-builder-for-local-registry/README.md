# 🛠️ Setup Docker Builder with Local Registry

This GitHub Composite Action configures a Docker `buildx` builder to **push images to a local or self-hosted Docker registry** using a trusted TLS certificate.

It is particularly useful for environments with internal registries or air-gapped infrastructure.

---

## Features

- 🧩 Installs system-level trusted TLS certificate
- 🔐 Adds the certificate to Docker's registry config
- 🐳 Initializes Docker Buildx with custom BuildKit config
- 🧬 Includes QEMU setup for multi-architecture builds

---

## Inputs

| Name            | Description                                       | Required |
| --------------- | ------------------------------------------------- | -------- |
| `registry-fqdn` | Fully qualified domain name of the local registry | ✅ Yes   |
| `tls-cert`      | PEM-formatted TLS certificate (string)            | ✅ Yes   |

---

## 🚀 Usage Example

```YAML
jobs:
  setup-builder:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Setup Docker Builder for Local Registry
        uses: ./setup-builder-for-local-registry
        with:
          registry-fqdn: registry.local.internal
          tls-cert: ${{ secrets.LOCAL_REGISTRY_TLS_CERT }}
```
