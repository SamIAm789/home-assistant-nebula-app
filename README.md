# home-assistant-nebula-app

This repository contains the Nebula node configuration and helper files used to run Nebula inside Home Assistant (add‑on or container). Certificates are stored in `ssl/` and are **not** included here — replace with your own CA and node certs.

## Files
- **config.yml** — Nebula configuration used by the node.
- **start.sh** — wrapper to start Nebula.
- **Dockerfile** — optional container image build.
- **nebula.service** — systemd unit for running Nebula on a host.
- **scripts/validate-config.sh** — helper to validate config and certs.
- **ssl/** — directory for CA and node certificates (not committed).

## Usage
1. Place your `ca.crt`, `host.crt`, and `host.key` into `ssl/`.
2. Edit `config.yml` to match your network and lighthouse IP.
3. Run `./scripts/validate-config.sh` to sanity check.
4. Start Nebula with `./start.sh` or via systemd `nebula.service`.
