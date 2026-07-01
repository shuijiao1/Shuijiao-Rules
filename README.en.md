# Shuijiao-Rules

Personal Surge / Mihomo routing rules for Shuijiao. The repository intentionally keeps only two rule directories: `Surge/` and `Mihomo/`.

- Main references: [`SukkaW/Surge`](https://github.com/SukkaW/Surge) and [`blackmatrix7/ios_rule_script`](https://github.com/blackmatrix7/ios_rule_script)
- `Ads` is sourced from [`TG-Twilight/AWAvenue-Ads-Rule`](https://github.com/TG-Twilight/AWAvenue-Ads-Rule) and is intended to be used with a `REJECT` policy
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
| `AppleCN` | `8` | `Surge/AppleCN.list` | `Mihomo/AppleCN.yaml` |
| `Proxy` | `7439` | `Surge/Proxy.list` | `Mihomo/Proxy.yaml` |
| `China` | `7640` | `Surge/China.list` | `Mihomo/China.yaml` |
| `Douyin` | `30` | `Surge/Douyin.list` | `Mihomo/Douyin.yaml` |
| `LAN` | `145` | `Surge/LAN.list` | `Mihomo/LAN.yaml` |
| `Ads` | `905` | `Surge/Ads.list` | `Mihomo/Ads.yaml` |
| `Streaming` | `1852` | `Surge/Streaming.list` | `Mihomo/Streaming.yaml` |
| `Game` | `689` | `Surge/Game.list` | `Mihomo/Game.yaml` |
| `Pay` | `380` | `Surge/Pay.list` | `Mihomo/Pay.yaml` |

## Recommended order

```text
LAN     -> DIRECT
Ads     -> REJECT
AppleCN -> DIRECT
China   -> DIRECT
AI      -> AI / Proxy
Telegram-> Telegram / Proxy
Crypto  -> Crypto / Proxy
Speedtest -> Proxy
Google  -> Proxy
Apple   -> Proxy
Proxy   -> Proxy
FINAL/MATCH -> Proxy
```

Optional standby rules:

```text
Douyin   -> DIRECT / Final
Streaming -> Final / Streaming
Game      -> Final / Game
Pay       -> Final / Pay
```

`China` includes domains, keywords, and China BGP CIDR rules. `Douyin` is for the mainland Douyin app and related CDN/video domains, not international TikTok. `AppleCN` intentionally excludes iCloud. `Ads` uses AWAvenue only and avoids larger blocklists to reduce false positives. `Douyin`, `Streaming`, `Game`, and `Pay` are provided as optional standby rules and are not meant to be enabled by default.

## Attribution

This repository is a personal ruleset aggregation. It does not claim authorship of upstream rules. Main references:

- [`SukkaW/Surge`](https://github.com/SukkaW/Surge)
- [`blackmatrix7/ios_rule_script`](https://github.com/blackmatrix7/ios_rule_script)
- [`TG-Twilight/AWAvenue-Ads-Rule`](https://github.com/TG-Twilight/AWAvenue-Ads-Rule)

Please review upstream licenses and disclaimers before use.
