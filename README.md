# backstage-arm64-images

Multi-arch Backstage images (`linux/amd64` + `linux/arm64`) dla klastra nucleospl.

Budowane z [nucleospl/homelab-backstage](https://github.com/nucleospl/homelab-backstage) po pinowanym commit SHA.
Natywne runnery — bez QEMU. Skanowane Trivym, podpisane cosign (keyless OIDC).

## Obraz

```
ghcr.io/nucleospl/backstage-arm64-images/app:VERSION
```

## Jak wydać nową wersję

1. Utwórz release w `nucleospl/homelab-backstage` z tagiem (np. `v1.1.0`)
2. `check-release.yml` wykryje go automatycznie (co 6h) lub uruchom `workflow_dispatch`
3. `build.yml` zbuduje i wypchnie obrazy do GHCR

## Weryfikacja (cosign)

```bash
cosign verify \
  --certificate-identity-regexp="https://github.com/nucleospl/backstage-arm64-images/.*" \
  --certificate-oidc-issuer="https://token.actions.githubusercontent.com" \
  ghcr.io/nucleospl/backstage-arm64-images/app:VERSION
```
