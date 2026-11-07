# Microsoft

Source config: [Microsoft.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Microsoft/Microsoft.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Microsoft | Microsoft rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [microsoft.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/microsoft.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Microsoft"
    type: select
    proxies: []
rules:
  - RULE-SET,Microsoft_Domain,Microsoft
  - RULE-SET,Microsoft,Microsoft,no-resolve
  - RULE-SET,Microsoft_IP,Microsoft,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Microsoft_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/mihomo/Microsoft_Domain.mrs }
  Microsoft: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/mihomo/Microsoft.yaml }
  Microsoft_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/mihomo/Microsoft_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/surge/Microsoft.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/surge/Microsoft.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/loon/Microsoft.list,policy=<policy>,tag=Microsoft,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/quantumult-x/Microsoft.list, tag=Microsoft, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/egern/Microsoft.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/shadowrocket/Microsoft.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Microsoft",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/sing-box/Microsoft.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Microsoft",
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

#### Microsoft.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/surge/Microsoft.list
```

#### Microsoft.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/surge/Microsoft.domainset
```

### Loon

#### Microsoft.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FMicrosoft%2Floon%2FMicrosoft.list)


### Quantumult X

#### Microsoft.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FMicrosoft%2Fquantumult-x%2FMicrosoft.list%2C%20tag%3DMicrosoft%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Microsoft.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FMicrosoft%2Fegern%2FMicrosoft.yaml)


### Shadowrocket

#### Microsoft.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/shadowrocket/Microsoft.list
```

### sing-box

#### Microsoft.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/sing-box/Microsoft.srs
```

## Artifacts

### mrs(ipcidr)

#### Microsoft_IP.mrs

GitHub: [Microsoft_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/mihomo/Microsoft_IP.mrs)
Text: [Microsoft_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/mihomo/Microsoft_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/mihomo/Microsoft_IP.mrs
```

### mrs(domain)

#### Microsoft_Domain.mrs

GitHub: [Microsoft_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/mihomo/Microsoft_Domain.mrs)
Text: [Microsoft_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/mihomo/Microsoft_Domain.txt)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/mihomo/Microsoft_Domain.mrs
```

### yaml(remaining)

#### Microsoft.yaml

GitHub: [Microsoft.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/mihomo/Microsoft.yaml)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/mihomo/Microsoft.yaml
```

### Surge

#### Microsoft.list

GitHub: [Microsoft.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/surge/Microsoft.list)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/surge/Microsoft.list
```

#### Microsoft.domainset

GitHub: [Microsoft.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/surge/Microsoft.domainset)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/surge/Microsoft.domainset
```

### Loon

#### Microsoft.list

GitHub: [Microsoft.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/loon/Microsoft.list)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/loon/Microsoft.list
```

### Quantumult X

#### Microsoft.list

GitHub: [Microsoft.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/quantumult-x/Microsoft.list)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/quantumult-x/Microsoft.list
```

### Egern

#### Microsoft.yaml

GitHub: [Microsoft.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/egern/Microsoft.yaml)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/egern/Microsoft.yaml
```

### Shadowrocket

#### Microsoft.list

GitHub: [Microsoft.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/shadowrocket/Microsoft.list)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/shadowrocket/Microsoft.list
```

### sing-box

#### Microsoft.json

GitHub: [Microsoft.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/sing-box/Microsoft.json)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/sing-box/Microsoft.json
```

#### Microsoft.srs

GitHub: [Microsoft.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/sing-box/Microsoft.srs)
Source: [Microsoft.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Microsoft/Microsoft.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Microsoft/sing-box/Microsoft.srs
```
