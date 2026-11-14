# TelegramEU

Source config: [TelegramEU.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/TelegramEU/TelegramEU.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| TelegramEU | Telegram EU regional routing rules from bgp.he.net | true | inline | classical | yaml | rules |  |  |  | [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml) |

## Mihomo Config

```yaml
proxy-groups:
  - name: "TelegramEU"
    type: select
    proxies: []
rules:
  - RULE-SET,TelegramEU_Domain,TelegramEU
  - RULE-SET,TelegramEU,TelegramEU,no-resolve
  - RULE-SET,TelegramEU_IP,TelegramEU,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  TelegramEU_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/mihomo/TelegramEU_Domain.mrs }
  TelegramEU: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/mihomo/TelegramEU.yaml }
  TelegramEU_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/mihomo/TelegramEU_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/surge/TelegramEU.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/surge/TelegramEU.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/loon/TelegramEU.list,policy=<policy>,tag=TelegramEU,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/quantumult-x/TelegramEU.list, tag=TelegramEU, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/egern/TelegramEU.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/shadowrocket/TelegramEU.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "TelegramEU",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/sing-box/TelegramEU.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "TelegramEU",
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

#### TelegramEU.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/surge/TelegramEU.list
```

#### TelegramEU.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/surge/TelegramEU.domainset
```

### Loon

#### TelegramEU.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramEU%2Floon%2FTelegramEU.list)


### Quantumult X

#### TelegramEU.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramEU%2Fquantumult-x%2FTelegramEU.list%2C%20tag%3DTelegramEU%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### TelegramEU.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramEU%2Fegern%2FTelegramEU.yaml)


### Shadowrocket

#### TelegramEU.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/shadowrocket/TelegramEU.list
```

### sing-box

#### TelegramEU.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/sing-box/TelegramEU.srs
```

## Artifacts

### mrs(ipcidr)

#### TelegramEU_IP.mrs

GitHub: [TelegramEU_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/mihomo/TelegramEU_IP.mrs)
Text: [TelegramEU_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/mihomo/TelegramEU_IP.txt)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/mihomo/TelegramEU_IP.mrs
```

### mrs(domain)

#### TelegramEU_Domain.mrs

GitHub: [TelegramEU_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/mihomo/TelegramEU_Domain.mrs)
Text: [TelegramEU_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/mihomo/TelegramEU_Domain.txt)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/mihomo/TelegramEU_Domain.mrs
```

### yaml(remaining)

#### TelegramEU.yaml

GitHub: [TelegramEU.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/mihomo/TelegramEU.yaml)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/mihomo/TelegramEU.yaml
```

### Surge

#### TelegramEU.list

GitHub: [TelegramEU.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/surge/TelegramEU.list)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/surge/TelegramEU.list
```

#### TelegramEU.domainset

GitHub: [TelegramEU.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/surge/TelegramEU.domainset)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/surge/TelegramEU.domainset
```

### Loon

#### TelegramEU.list

GitHub: [TelegramEU.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/loon/TelegramEU.list)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/loon/TelegramEU.list
```

### Quantumult X

#### TelegramEU.list

GitHub: [TelegramEU.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/quantumult-x/TelegramEU.list)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/quantumult-x/TelegramEU.list
```

### Egern

#### TelegramEU.yaml

GitHub: [TelegramEU.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/egern/TelegramEU.yaml)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/egern/TelegramEU.yaml
```

### Shadowrocket

#### TelegramEU.list

GitHub: [TelegramEU.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/shadowrocket/TelegramEU.list)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/shadowrocket/TelegramEU.list
```

### sing-box

#### TelegramEU.json

GitHub: [TelegramEU.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/sing-box/TelegramEU.json)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/sing-box/TelegramEU.json
```

#### TelegramEU.srs

GitHub: [TelegramEU.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/sing-box/TelegramEU.srs)
Source: [TelegramEU.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramEU/TelegramEU.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramEU/sing-box/TelegramEU.srs
```
