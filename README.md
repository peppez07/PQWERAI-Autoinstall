# PQWERAI autoinstallation — compiled launcher

This public repository distributes the **built Linux amd64 installer only**, its checksum/build metadata and required third-party notices. It contains no project implementation source, Core images, wallet keys or private installation payloads. The source and full kit remain in the owner's private autoinstaller repository.

**Isolated lab use only.** Public Core activation remains blocked by known Core WASM findings. This launcher refuses public peer/seed-rpc roles. It does not download payloads automatically or contain an access token.

1. Obtain `pqwerai-autoinstall-linux-amd64` and `SHA256SUMS`. Verify the checksum through an owner-trusted channel, then set the executable bit with `chmod 0755 pqwerai-autoinstall-linux-amd64`.
2. Obtain the private source-backed kit and its expected SHA-256 using your authorized access to `peppez07/PQWERAI-Autoinstall-Private`. Core payloads are deliberately not publicly mirrored.
3. Verify or preview without installation:

```sh
./pqwerai-autoinstall-linux-amd64 --version
./pqwerai-autoinstall-linux-amd64 --kit ./private-kit.tar.gz --sha256 EXPECTED_KIT_SHA256 --verify-only
./pqwerai-autoinstall-linux-amd64 --kit ./private-kit.tar.gz --sha256 EXPECTED_KIT_SHA256 --destination /opt/pqwerai-lab
```

For a fresh owner-controlled Ubuntu amd64 host, explicitly install:

```sh
sudo ./pqwerai-autoinstall-linux-amd64 --kit ./private-kit.tar.gz --sha256 EXPECTED_KIT_SHA256 --apply --role lab --install-docker --destination /opt/pqwerai-lab
```

The launcher refuses an existing nonempty destination and archive traversal/links. It makes a fresh checksum-verified private snapshot before execution and retains staging for review/recovery. `--cache` selects the staging parent directory. Plan/verify mode does not extract, install Docker or start services. Hashes establish integrity relative to a trusted expected value, not an independent release signature.

The full private kit uses the existing PQWERAI dashboard and Docker Compose. Coolify is not required. Pool and relay packages remain optional. No mining, validator keys, funds, QAI contract deployment, public server update or firewall change is activated by the launcher itself.

Validation is local author verification on Windows/Docker with Ubuntu 24.04 userland and an empty isolated Docker engine. Independent VPS/systemd/ACME, cross-NAT relay traffic and multi-GPU inference remain unverified. See `build-info.json` and the private repository's evidence for exact versions and results. This is not an independently audited public blockchain release.

The required Go notices are in `LICENSES/`. No new license is asserted for private historical/component code. Public Core/helper distribution remains withheld pending corresponding-source/license and security acceptance. The public repository is intentionally not a public source offer for those payloads.
