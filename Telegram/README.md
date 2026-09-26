# Telegram

Source config: [Telegram.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Telegram/Telegram.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Telegram | Telegram | true | http | classical | yaml | rules |  | [Telegram.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Telegram/Telegram.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Telegram"
    type: select
    proxies: []
rules:
  - RULE-SET,Telegram_Domain,Telegram
  - RULE-SET,Telegram,Telegram,no-resolve
  - RULE-SET,Telegram_IP,Telegram,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Telegram_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/mihomo/Telegram_Domain.mrs }
  Telegram: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/mihomo/Telegram.yaml }
  Telegram_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/mihomo/Telegram_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/surge/Telegram.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/surge/Telegram.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/loon/Telegram.list,policy=<policy>,tag=Telegram,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/quantumult-x/Telegram.list, tag=Telegram, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/egern/Telegram.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/shadowrocket/Telegram.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Telegram",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/sing-box/Telegram.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Telegram",
        "action": "route",
        "outbound": "<outbound>"
      }
    ]
  }
}
```

## Client Import / Copy

Replace `<policy>` before opening links that contain it. Copy blocks contain only raw URLs.

### Surge

#### Telegram.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/surge/Telegram.list
```

#### Telegram.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/surge/Telegram.domainset
```

### Loon

#### Telegram.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegram%2Floon%2FTelegram.list)


### Quantumult X

#### Telegram.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegram%2Fquantumult-x%2FTelegram.list%2C%20tag%3DTelegram%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Telegram.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegram%2Fegern%2FTelegram.yaml)


### Shadowrocket

#### Telegram.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/shadowrocket/Telegram.list
```

### sing-box

#### Telegram.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/sing-box/Telegram.srs
```

## Artifacts

### mrs(ipcidr)

#### Telegram_IP.mrs

GitHub: [Telegram_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/mihomo/Telegram_IP.mrs)
Text: [Telegram_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/mihomo/Telegram_IP.txt)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/mihomo/Telegram_IP.mrs
```

### mrs(domain)

#### Telegram_Domain.mrs

GitHub: [Telegram_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/mihomo/Telegram_Domain.mrs)
Text: [Telegram_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/mihomo/Telegram_Domain.txt)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/mihomo/Telegram_Domain.mrs
```

### yaml(remaining)

#### Telegram.yaml

GitHub: [Telegram.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/mihomo/Telegram.yaml)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/mihomo/Telegram.yaml
```

### Surge

#### Telegram.list

GitHub: [Telegram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/surge/Telegram.list)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/surge/Telegram.list
```

#### Telegram.domainset

GitHub: [Telegram.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/surge/Telegram.domainset)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/surge/Telegram.domainset
```

### Loon

#### Telegram.list

GitHub: [Telegram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/loon/Telegram.list)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/loon/Telegram.list
```

### Quantumult X

#### Telegram.list

GitHub: [Telegram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/quantumult-x/Telegram.list)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/quantumult-x/Telegram.list
```

### Egern

#### Telegram.yaml

GitHub: [Telegram.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/egern/Telegram.yaml)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/egern/Telegram.yaml
```

### Shadowrocket

#### Telegram.list

GitHub: [Telegram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/shadowrocket/Telegram.list)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/shadowrocket/Telegram.list
```

### sing-box

#### Telegram.json

GitHub: [Telegram.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/sing-box/Telegram.json)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/sing-box/Telegram.json
```

#### Telegram.srs

GitHub: [Telegram.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/sing-box/Telegram.srs)
Source: [Telegram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Telegram/Telegram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Telegram/sing-box/Telegram.srs
```
