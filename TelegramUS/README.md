# TelegramUS

Source config: [TelegramUS.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/TelegramUS/TelegramUS.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| TelegramUS | Telegram US regional routing rules from bgp.he.net | true | inline | classical | yaml | rules |  |  |  | [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml) |

## Mihomo Config

```yaml
proxy-groups:
  - name: "TelegramUS"
    type: select
    proxies: []
rules:
  - RULE-SET,TelegramUS_Domain,TelegramUS
  - RULE-SET,TelegramUS,TelegramUS,no-resolve
  - RULE-SET,TelegramUS_IP,TelegramUS,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  TelegramUS_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/mihomo/TelegramUS_Domain.mrs }
  TelegramUS: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/mihomo/TelegramUS.yaml }
  TelegramUS_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/mihomo/TelegramUS_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/surge/TelegramUS.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/surge/TelegramUS.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/loon/TelegramUS.list,policy=<policy>,tag=TelegramUS,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/quantumult-x/TelegramUS.list, tag=TelegramUS, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/egern/TelegramUS.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/shadowrocket/TelegramUS.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "TelegramUS",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/sing-box/TelegramUS.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "TelegramUS",
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

#### TelegramUS.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/surge/TelegramUS.list
```

#### TelegramUS.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/surge/TelegramUS.domainset
```

### Loon

#### TelegramUS.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramUS%2Floon%2FTelegramUS.list)


### Quantumult X

#### TelegramUS.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramUS%2Fquantumult-x%2FTelegramUS.list%2C%20tag%3DTelegramUS%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### TelegramUS.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTelegramUS%2Fegern%2FTelegramUS.yaml)


### Shadowrocket

#### TelegramUS.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/shadowrocket/TelegramUS.list
```

### sing-box

#### TelegramUS.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/sing-box/TelegramUS.srs
```

## Artifacts

### mrs(ipcidr)

#### TelegramUS_IP.mrs

GitHub: [TelegramUS_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/mihomo/TelegramUS_IP.mrs)
Text: [TelegramUS_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/mihomo/TelegramUS_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/mihomo/TelegramUS_IP.mrs
```

### mrs(domain)

#### TelegramUS_Domain.mrs

GitHub: [TelegramUS_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/mihomo/TelegramUS_Domain.mrs)
Text: [TelegramUS_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/mihomo/TelegramUS_Domain.txt)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/mihomo/TelegramUS_Domain.mrs
```

### yaml(remaining)

#### TelegramUS.yaml

GitHub: [TelegramUS.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/mihomo/TelegramUS.yaml)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/mihomo/TelegramUS.yaml
```

### Surge

#### TelegramUS.list

GitHub: [TelegramUS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/surge/TelegramUS.list)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/surge/TelegramUS.list
```

#### TelegramUS.domainset

GitHub: [TelegramUS.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/surge/TelegramUS.domainset)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/surge/TelegramUS.domainset
```

### Loon

#### TelegramUS.list

GitHub: [TelegramUS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/loon/TelegramUS.list)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/loon/TelegramUS.list
```

### Quantumult X

#### TelegramUS.list

GitHub: [TelegramUS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/quantumult-x/TelegramUS.list)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/quantumult-x/TelegramUS.list
```

### Egern

#### TelegramUS.yaml

GitHub: [TelegramUS.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/egern/TelegramUS.yaml)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/egern/TelegramUS.yaml
```

### Shadowrocket

#### TelegramUS.list

GitHub: [TelegramUS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/shadowrocket/TelegramUS.list)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/shadowrocket/TelegramUS.list
```

### sing-box

#### TelegramUS.json

GitHub: [TelegramUS.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/sing-box/TelegramUS.json)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/sing-box/TelegramUS.json
```

#### TelegramUS.srs

GitHub: [TelegramUS.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/sing-box/TelegramUS.srs)
Source: [TelegramUS.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TelegramUS/TelegramUS.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TelegramUS/sing-box/TelegramUS.srs
```
