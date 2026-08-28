# sing-box-forge

Automated toolchain for sing-box: nightly builds from source, compiled geo-routing rules, and aggregated proxy configs.

## What it does

- **Builds sing-box** from the latest upstream release with custom tags and publishes binaries.
- **Compiles geo-rules** (`geoip` + `geosite`) into SRS format and pushes them to the `rule-set` branch.
- **Aggregates proxy configs** from public sources, deduplicates nodes by country, and generates subscription lists.

## Branches

| Branch | Purpose |
|--------|---------|
| `main` | Source code, workflows, and generated proxy configs |
| `rule-set` | Compiled SRS files (`geoip/`, `geosite/`) |

## Proxy configs

Generated configs are updated hourly and available as raw files in the `main` branch:

- `blacklist_all.txt` — mixed nodes (VLESS, VMess, Trojan, SS, Hysteria2)
- `whitelist_all.txt` — anti-block nodes for bypassing restrictions

Import the raw URL directly into your sing-box client.

## Automation

All tasks run via GitHub Actions:

| Workflow | Schedule |
|----------|----------|
| Build sing-box + geo-rules | Daily at 00:00 UTC |
| Sync proxy configs | Hourly |

## Disclaimer

This project aggregates publicly available proxy nodes for personal use. The author is not responsible for the availability, security, or legality of third-party nodes.