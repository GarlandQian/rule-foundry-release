# AI

Source config: [AI.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/AI/AI.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| AI | AI rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [ai.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/ai.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "AI"
    type: select
    proxies: []
rules:
  - RULE-SET,AI_Domain,AI
  - RULE-SET,AI,AI,no-resolve
  - RULE-SET,AI_IP,AI,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  AI_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_Domain.mrs }
  AI: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI.yaml }
  AI_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/loon/AI.list,policy=<policy>,tag=AI,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/quantumult-x/AI.list, tag=AI, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/egern/AI.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/shadowrocket/AI.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "AI",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "AI",
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

#### AI.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.list
```

#### AI.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.domainset
```

### Loon

#### AI.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAI%2Floon%2FAI.list)


### Quantumult X

#### AI.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAI%2Fquantumult-x%2FAI.list%2C%20tag%3DAI%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### AI.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAI%2Fegern%2FAI.yaml)


### Shadowrocket

#### AI.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/shadowrocket/AI.list
```

### sing-box

#### AI.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.srs
```

## Artifacts

### mrs(ipcidr)

#### AI_IP.mrs

GitHub: [AI_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_IP.mrs)
Text: [AI_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_IP.mrs
```

### mrs(domain)

#### AI_Domain.mrs

GitHub: [AI_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_Domain.mrs)
Text: [AI_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_Domain.txt)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_Domain.mrs
```

### yaml(remaining)

#### AI.yaml

GitHub: [AI.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI.yaml)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI.yaml
```

### Surge

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/surge/AI.list)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.list
```

#### AI.domainset

GitHub: [AI.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/surge/AI.domainset)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.domainset
```

### Loon

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/loon/AI.list)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/loon/AI.list
```

### Quantumult X

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/quantumult-x/AI.list)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/quantumult-x/AI.list
```

### Egern

#### AI.yaml

GitHub: [AI.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/egern/AI.yaml)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/egern/AI.yaml
```

### Shadowrocket

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/shadowrocket/AI.list)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/shadowrocket/AI.list
```

### sing-box

#### AI.json

GitHub: [AI.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/sing-box/AI.json)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.json
```

#### AI.srs

GitHub: [AI.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/sing-box/AI.srs)
Source: [AI.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/AI.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.srs
```
