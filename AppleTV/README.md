# AppleTV

Source config: [AppleTV.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/AppleTV/AppleTV.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| AppleTV | Apple TV streaming rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [apple-tv.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/apple-tv.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "AppleTV"
    type: select
    proxies: []
rules:
  - RULE-SET,AppleTV_Domain,AppleTV
  - RULE-SET,AppleTV,AppleTV,no-resolve
  - RULE-SET,AppleTV_IP,AppleTV,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  AppleTV_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/mihomo/AppleTV_Domain.mrs }
  AppleTV: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/mihomo/AppleTV.yaml }
  AppleTV_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/mihomo/AppleTV_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/surge/AppleTV.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/surge/AppleTV.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/loon/AppleTV.list,policy=<policy>,tag=AppleTV,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/quantumult-x/AppleTV.list, tag=AppleTV, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/egern/AppleTV.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/shadowrocket/AppleTV.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "AppleTV",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/sing-box/AppleTV.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "AppleTV",
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

#### AppleTV.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/surge/AppleTV.list
```

#### AppleTV.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/surge/AppleTV.domainset
```

### Loon

#### AppleTV.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleTV%2Floon%2FAppleTV.list)


### Quantumult X

#### AppleTV.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleTV%2Fquantumult-x%2FAppleTV.list%2C%20tag%3DAppleTV%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### AppleTV.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleTV%2Fegern%2FAppleTV.yaml)


### Shadowrocket

#### AppleTV.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/shadowrocket/AppleTV.list
```

### sing-box

#### AppleTV.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/sing-box/AppleTV.srs
```

## Artifacts

### mrs(ipcidr)

#### AppleTV_IP.mrs

GitHub: [AppleTV_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/mihomo/AppleTV_IP.mrs)
Text: [AppleTV_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/mihomo/AppleTV_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/mihomo/AppleTV_IP.mrs
```

### mrs(domain)

#### AppleTV_Domain.mrs

GitHub: [AppleTV_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/mihomo/AppleTV_Domain.mrs)
Text: [AppleTV_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/mihomo/AppleTV_Domain.txt)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/mihomo/AppleTV_Domain.mrs
```

### yaml(remaining)

#### AppleTV.yaml

GitHub: [AppleTV.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/mihomo/AppleTV.yaml)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/mihomo/AppleTV.yaml
```

### Surge

#### AppleTV.list

GitHub: [AppleTV.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/surge/AppleTV.list)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/surge/AppleTV.list
```

#### AppleTV.domainset

GitHub: [AppleTV.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/surge/AppleTV.domainset)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/surge/AppleTV.domainset
```

### Loon

#### AppleTV.list

GitHub: [AppleTV.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/loon/AppleTV.list)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/loon/AppleTV.list
```

### Quantumult X

#### AppleTV.list

GitHub: [AppleTV.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/quantumult-x/AppleTV.list)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/quantumult-x/AppleTV.list
```

### Egern

#### AppleTV.yaml

GitHub: [AppleTV.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/egern/AppleTV.yaml)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/egern/AppleTV.yaml
```

### Shadowrocket

#### AppleTV.list

GitHub: [AppleTV.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/shadowrocket/AppleTV.list)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/shadowrocket/AppleTV.list
```

### sing-box

#### AppleTV.json

GitHub: [AppleTV.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/sing-box/AppleTV.json)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/sing-box/AppleTV.json
```

#### AppleTV.srs

GitHub: [AppleTV.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/sing-box/AppleTV.srs)
Source: [AppleTV.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleTV/AppleTV.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleTV/sing-box/AppleTV.srs
```
