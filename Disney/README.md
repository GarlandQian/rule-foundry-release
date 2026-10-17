# Disney

Source config: [Disney.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Disney/Disney.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Disney | Disney rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [disney.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/disney.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Disney"
    type: select
    proxies: []
rules:
  - RULE-SET,Disney_Domain,Disney
  - RULE-SET,Disney,Disney,no-resolve
  - RULE-SET,Disney_IP,Disney,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Disney_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/mihomo/Disney_Domain.mrs }
  Disney: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/mihomo/Disney.yaml }
  Disney_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/mihomo/Disney_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/surge/Disney.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/surge/Disney.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/loon/Disney.list,policy=<policy>,tag=Disney,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/quantumult-x/Disney.list, tag=Disney, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/egern/Disney.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/shadowrocket/Disney.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Disney",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/sing-box/Disney.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Disney",
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

#### Disney.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/surge/Disney.list
```

#### Disney.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/surge/Disney.domainset
```

### Loon

#### Disney.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDisney%2Floon%2FDisney.list)


### Quantumult X

#### Disney.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDisney%2Fquantumult-x%2FDisney.list%2C%20tag%3DDisney%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Disney.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDisney%2Fegern%2FDisney.yaml)


### Shadowrocket

#### Disney.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/shadowrocket/Disney.list
```

### sing-box

#### Disney.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/sing-box/Disney.srs
```

## Artifacts

### mrs(ipcidr)

#### Disney_IP.mrs

GitHub: [Disney_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/mihomo/Disney_IP.mrs)
Text: [Disney_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/mihomo/Disney_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/mihomo/Disney_IP.mrs
```

### mrs(domain)

#### Disney_Domain.mrs

GitHub: [Disney_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/mihomo/Disney_Domain.mrs)
Text: [Disney_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/mihomo/Disney_Domain.txt)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/mihomo/Disney_Domain.mrs
```

### yaml(remaining)

#### Disney.yaml

GitHub: [Disney.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/mihomo/Disney.yaml)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/mihomo/Disney.yaml
```

### Surge

#### Disney.list

GitHub: [Disney.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/surge/Disney.list)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/surge/Disney.list
```

#### Disney.domainset

GitHub: [Disney.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/surge/Disney.domainset)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/surge/Disney.domainset
```

### Loon

#### Disney.list

GitHub: [Disney.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/loon/Disney.list)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/loon/Disney.list
```

### Quantumult X

#### Disney.list

GitHub: [Disney.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/quantumult-x/Disney.list)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/quantumult-x/Disney.list
```

### Egern

#### Disney.yaml

GitHub: [Disney.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/egern/Disney.yaml)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/egern/Disney.yaml
```

### Shadowrocket

#### Disney.list

GitHub: [Disney.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/shadowrocket/Disney.list)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/shadowrocket/Disney.list
```

### sing-box

#### Disney.json

GitHub: [Disney.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/sing-box/Disney.json)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/sing-box/Disney.json
```

#### Disney.srs

GitHub: [Disney.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/sing-box/Disney.srs)
Source: [Disney.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Disney/Disney.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Disney/sing-box/Disney.srs
```
