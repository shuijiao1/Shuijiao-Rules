# Shuijiao-Rules

Personal Surge / Mihomo routing rules for Shuijiao. The repository intentionally keeps only two rule directories: `Surge/` and `Mihomo/`.

- Main references: [`SukkaW/Surge`](https://github.com/SukkaW/Surge) and [`blackmatrix7/ios_rule_script`](https://github.com/blackmatrix7/ios_rule_script)
- Surge outputs `.list`; Mihomo outputs `behavior: classical` `.yaml`
- Same content: files with the same name share the same normalized rules; only the wrapper format differs
- CDN is merged into `Proxy`
- Updated: `2026-07-01`

## Rule files

| Rule | Count | Surge | Mihomo |
|---|---:|---|---|
| `Telegram` | `50` | `Surge/Telegram.list` | `Mihomo/Telegram.yaml` |
| `AI` | `163` | `Surge/AI.list` | `Mihomo/AI.yaml` |
| `Speedtest` | `128` | `Surge/Speedtest.list` | `Mihomo/Speedtest.yaml` |
| `Crypto` | `239` | `Surge/Crypto.list` | `Mihomo/Crypto.yaml` |
| `Google` | `751` | `Surge/Google.list` | `Mihomo/Google.yaml` |
| `Apple` | `183` | `Surge/Apple.list` | `Mihomo/Apple.yaml` |
| `AppleCN` | `9` | `Surge/AppleCN.list` | `Mihomo/AppleCN.yaml` |
| `Proxy` | `7446` | `Surge/Proxy.list` | `Mihomo/Proxy.yaml` |
| `ChinaDomain` | `3690` | `Surge/ChinaDomain.list` | `Mihomo/ChinaDomain.yaml` |
| `LAN` | `145` | `Surge/LAN.list` | `Mihomo/LAN.yaml` |

## Recommended order

```text
LAN          -> DIRECT
AppleCN      -> DIRECT
ChinaDomain  -> DIRECT
AI           -> AI / Proxy
Telegram     -> Telegram / Proxy
Crypto       -> Crypto / Proxy
Speedtest    -> Proxy
Google       -> Proxy
Apple        -> Proxy
Proxy        -> Proxy
FINAL/MATCH  -> Proxy
```

## Attribution

This repository is a personal ruleset aggregation. It does not claim authorship of upstream rules. Main references:

- [`SukkaW/Surge`](https://github.com/SukkaW/Surge)
- [`blackmatrix7/ios_rule_script`](https://github.com/blackmatrix7/ios_rule_script)

Please review upstream licenses and disclaimers before use.
