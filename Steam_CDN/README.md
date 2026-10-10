# Steam_CDN

Source config: [Steam_CDN.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Steam_CDN/Steam_CDN.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Steam_CDN | Steam_CDN | true | http | domain | text | rules |  | [Steam_CDN.list](https://raw.githubusercontent.com/Aethersailor/Custom_OpenClash_Rules/refs/heads/main/rule/Steam_CDN.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Steam_CDN"
    type: select
    proxies: []
rules:
  - RULE-SET,Steam_CDN_Domain,Steam_CDN
  - RULE-SET,Steam_CDN,Steam_CDN,no-resolve
  - RULE-SET,Steam_CDN_IP,Steam_CDN,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Steam_CDN_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/mihomo/Steam_CDN_Domain.mrs }
  Steam_CDN: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/mihomo/Steam_CDN.yaml }
  Steam_CDN_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/mihomo/Steam_CDN_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/surge/Steam_CDN.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/surge/Steam_CDN.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/loon/Steam_CDN.list,policy=<policy>,tag=Steam_CDN,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/quantumult-x/Steam_CDN.list, tag=Steam_CDN, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/egern/Steam_CDN.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/shadowrocket/Steam_CDN.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Steam_CDN",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/sing-box/Steam_CDN.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Steam_CDN",
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

#### Steam_CDN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/surge/Steam_CDN.list
```

#### Steam_CDN.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/surge/Steam_CDN.domainset
```

### Loon

#### Steam_CDN.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteam_CDN%2Floon%2FSteam_CDN.list)


### Quantumult X

#### Steam_CDN.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteam_CDN%2Fquantumult-x%2FSteam_CDN.list%2C%20tag%3DSteam_CDN%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Steam_CDN.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteam_CDN%2Fegern%2FSteam_CDN.yaml)


### Shadowrocket

#### Steam_CDN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/shadowrocket/Steam_CDN.list
```

### sing-box

#### Steam_CDN.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/sing-box/Steam_CDN.srs
```

## Artifacts

### mrs(ipcidr)

#### Steam_CDN_IP.mrs

GitHub: [Steam_CDN_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/mihomo/Steam_CDN_IP.mrs)
Text: [Steam_CDN_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/mihomo/Steam_CDN_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/mihomo/Steam_CDN_IP.mrs
```

### mrs(domain)

#### Steam_CDN_Domain.mrs

GitHub: [Steam_CDN_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/mihomo/Steam_CDN_Domain.mrs)
Text: [Steam_CDN_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/mihomo/Steam_CDN_Domain.txt)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/mihomo/Steam_CDN_Domain.mrs
```

### yaml(remaining)

#### Steam_CDN.yaml

GitHub: [Steam_CDN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/mihomo/Steam_CDN.yaml)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/mihomo/Steam_CDN.yaml
```

### Surge

#### Steam_CDN.list

GitHub: [Steam_CDN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/surge/Steam_CDN.list)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/surge/Steam_CDN.list
```

#### Steam_CDN.domainset

GitHub: [Steam_CDN.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/surge/Steam_CDN.domainset)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/surge/Steam_CDN.domainset
```

### Loon

#### Steam_CDN.list

GitHub: [Steam_CDN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/loon/Steam_CDN.list)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/loon/Steam_CDN.list
```

### Quantumult X

#### Steam_CDN.list

GitHub: [Steam_CDN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/quantumult-x/Steam_CDN.list)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/quantumult-x/Steam_CDN.list
```

### Egern

#### Steam_CDN.yaml

GitHub: [Steam_CDN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/egern/Steam_CDN.yaml)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/egern/Steam_CDN.yaml
```

### Shadowrocket

#### Steam_CDN.list

GitHub: [Steam_CDN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/shadowrocket/Steam_CDN.list)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/shadowrocket/Steam_CDN.list
```

### sing-box

#### Steam_CDN.json

GitHub: [Steam_CDN.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/sing-box/Steam_CDN.json)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/sing-box/Steam_CDN.json
```

#### Steam_CDN.srs

GitHub: [Steam_CDN.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/sing-box/Steam_CDN.srs)
Source: [Steam_CDN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam_CDN/Steam_CDN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam_CDN/sing-box/Steam_CDN.srs
```
