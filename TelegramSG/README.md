# TelegramSG

Source config: [TelegramSG.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/TelegramSG/TelegramSG.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| TelegramSG | Telegram SG regional routing rules from bgp.he.net | true | inline | classical | yaml | rules |  |  |  | [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml) |

## Mihomo Config

```yaml
proxy-groups:
  - name: "TelegramSG"
    type: select
    proxies: []
rules:
  - RULE-SET,TelegramSG_Domain,TelegramSG
  - RULE-SET,TelegramSG,TelegramSG,no-resolve
  - RULE-SET,TelegramSG_IP,TelegramSG,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  TelegramSG_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/mihomo/TelegramSG_Domain.mrs }
  TelegramSG: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/mihomo/TelegramSG.yaml }
  TelegramSG_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/mihomo/TelegramSG_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/surge/TelegramSG.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/surge/TelegramSG.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/loon/TelegramSG.list,policy=<policy>,tag=TelegramSG,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/quantumult-x/TelegramSG.list, tag=TelegramSG, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/egern/TelegramSG.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/shadowrocket/TelegramSG.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "TelegramSG",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/sing-box/TelegramSG.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "TelegramSG",
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

#### TelegramSG.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/surge/TelegramSG.list
```

#### TelegramSG.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/surge/TelegramSG.domainset
```

### Loon

#### TelegramSG.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramSG%2Floon%2FTelegramSG.list)


### Quantumult X

#### TelegramSG.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramSG%2Fquantumult-x%2FTelegramSG.list%2C%20tag%3DTelegramSG%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### TelegramSG.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramSG%2Fegern%2FTelegramSG.yaml)


### Shadowrocket

#### TelegramSG.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/shadowrocket/TelegramSG.list
```

### sing-box

#### TelegramSG.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/sing-box/TelegramSG.srs
```

## Artifacts

### mrs(ipcidr)

#### TelegramSG_IP.mrs

GitHub: [TelegramSG_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/mihomo/TelegramSG_IP.mrs)
Text: [TelegramSG_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/mihomo/TelegramSG_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/mihomo/TelegramSG_IP.mrs
```

### mrs(domain)

#### TelegramSG_Domain.mrs

GitHub: [TelegramSG_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/mihomo/TelegramSG_Domain.mrs)
Text: [TelegramSG_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/mihomo/TelegramSG_Domain.txt)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/mihomo/TelegramSG_Domain.mrs
```

### yaml(remaining)

#### TelegramSG.yaml

GitHub: [TelegramSG.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/mihomo/TelegramSG.yaml)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/mihomo/TelegramSG.yaml
```

### Surge

#### TelegramSG.list

GitHub: [TelegramSG.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/surge/TelegramSG.list)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/surge/TelegramSG.list
```

#### TelegramSG.domainset

GitHub: [TelegramSG.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/surge/TelegramSG.domainset)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/surge/TelegramSG.domainset
```

### Loon

#### TelegramSG.list

GitHub: [TelegramSG.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/loon/TelegramSG.list)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/loon/TelegramSG.list
```

### Quantumult X

#### TelegramSG.list

GitHub: [TelegramSG.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/quantumult-x/TelegramSG.list)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/quantumult-x/TelegramSG.list
```

### Egern

#### TelegramSG.yaml

GitHub: [TelegramSG.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/egern/TelegramSG.yaml)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/egern/TelegramSG.yaml
```

### Shadowrocket

#### TelegramSG.list

GitHub: [TelegramSG.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/shadowrocket/TelegramSG.list)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/shadowrocket/TelegramSG.list
```

### sing-box

#### TelegramSG.json

GitHub: [TelegramSG.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/sing-box/TelegramSG.json)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/sing-box/TelegramSG.json
```

#### TelegramSG.srs

GitHub: [TelegramSG.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/sing-box/TelegramSG.srs)
Source: [TelegramSG.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramSG/TelegramSG.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramSG/sing-box/TelegramSG.srs
```
