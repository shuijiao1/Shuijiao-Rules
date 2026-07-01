# Shuijiao-Rules

[English](README.en.md)

水饺自用的 Surge / Mihomo 分流规则。仓库只保留两个规则目录：`Surge/` 和 `Mihomo/`。

- 主要参考：[`SukkaW/Surge`](https://github.com/SukkaW/Surge) 与 [`blackmatrix7/ios_rule_script`](https://github.com/blackmatrix7/ios_rule_script)
- 输出格式：Surge 使用 `.list`，Mihomo 使用 `behavior: classical` 的 `.yaml`
- 内容一致：同名的 Surge 与 Mihomo 文件使用同一份规则内容，只是文件格式不同
- CDN 规则：已经合并进 `Proxy`，不单独提供 `CDN` 文件
- 更新时间：`2026-07-01`

## 规则列表

| 规则 | 条数 | Surge | Mihomo |
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

## 分类说明

- `Telegram`：Telegram 域名、ASN/IP 段。
- `AI`：OpenAI / ChatGPT / Claude / Gemini / Grok / Perplexity / Poe / Copilot / Midjourney / Hugging Face / Mistral / Cursor / Windsurf 等 AI 服务。
- `Speedtest`：Ookla Speedtest、Fast、Cloudflare Speed、M-Lab、LibreSpeed 以及常见测速节点。
- `Crypto`：Binance、Bybit、OKX、Coinbase、Kraken、KuCoin、Gate、MEXC、Bitget、HTX/Huobi、行情、钱包、DeFi 与链上浏览器。
- `Google`：Google、YouTube、Gmail、Drive、Firebase 等常规 Google 服务；Gemini / AI Studio 等 AI 域名优先放入 `AI`。
- `Apple`：Apple 国际服务、Apple Media、Apple TV、Apple Developer、Apple CDN 与 Apple IP。
- `AppleCN`：中国区 Apple / iCloud 域名，建议直连。
- `Proxy`：常见国外站点、国外 CDN、开发者服务、社交服务等；已合并 CDN。
- `ChinaDomain`：中国大陆常见域名，建议直连；只包含域名规则，不包含中国 IP 大表。
- `LAN`：局域网、本地域名、私有地址段，建议直连。

## 推荐优先级

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

优先级原则：`LAN` 永远最前；`AppleCN` 早于 `Apple`；`AI` 早于 `Google` / `Proxy`；具体分类早于 `Proxy`。

## Surge 示例

```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/LAN.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/AppleCN.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/ChinaDomain.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/AI.list,AI
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/Telegram.list,Telegram
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/Crypto.list,Crypto
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/Speedtest.list,Proxy
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/Google.list,Proxy
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/Apple.list,Proxy
RULE-SET,https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Surge/Proxy.list,Proxy
FINAL,Proxy
```

## Mihomo 示例

```yaml
rule-providers:
  telegram:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/Telegram.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/Telegram.yaml
  ai:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/AI.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/AI.yaml
  speedtest:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/Speedtest.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/Speedtest.yaml
  crypto:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/Crypto.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/Crypto.yaml
  google:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/Google.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/Google.yaml
  apple:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/Apple.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/Apple.yaml
  applecn:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/AppleCN.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/AppleCN.yaml
  proxy:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/Proxy.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/Proxy.yaml
  chinadomain:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/ChinaDomain.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/ChinaDomain.yaml
  lan:
    type: http
    behavior: classical
    format: yaml
    interval: 86400
    path: ./rules/Shuijiao/LAN.yaml
    url: https://raw.githubusercontent.com/shuijiao1/Shuijiao-Rules/main/Mihomo/LAN.yaml

rules:
  - RULE-SET,lan,DIRECT
  - RULE-SET,applecn,DIRECT
  - RULE-SET,chinadomain,DIRECT
  - RULE-SET,ai,AI
  - RULE-SET,telegram,Telegram
  - RULE-SET,crypto,Crypto
  - RULE-SET,speedtest,Proxy
  - RULE-SET,google,Proxy
  - RULE-SET,apple,Proxy
  - RULE-SET,proxy,Proxy
  - MATCH,Proxy
```

## 来源与授权

本仓库为个人自用规则整理，不声明上游规则原创权。规则主要来自并参考：

- [`SukkaW/Surge`](https://github.com/SukkaW/Surge)
- [`blackmatrix7/ios_rule_script`](https://github.com/blackmatrix7/ios_rule_script)

本仓库仅做格式转换、去重、合并和个人补丁维护。使用前请自行确认上游项目的授权、免责声明和适用范围。
