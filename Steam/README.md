# Steam

Source config: [Steam.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Steam/Steam.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Steam | Steam | true | http | classical | yaml | rules |  | [Steam.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Steam/Steam.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Steam"
    type: select
    proxies: []
rules:
  - RULE-SET,Steam_Domain,Steam
  - RULE-SET,Steam,Steam,no-resolve
  - RULE-SET,Steam_IP,Steam,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Steam_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/mihomo/Steam_Domain.mrs }
  Steam: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/mihomo/Steam.yaml }
  Steam_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/mihomo/Steam_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/surge/Steam.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/surge/Steam.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/loon/Steam.list,policy=<policy>,tag=Steam,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/quantumult-x/Steam.list, tag=Steam, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/egern/Steam.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/shadowrocket/Steam.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Steam",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/sing-box/Steam.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Steam",
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

#### Steam.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/surge/Steam.list
```

#### Steam.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/surge/Steam.domainset
```

### Loon

#### Steam.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteam%2Floon%2FSteam.list)


### Quantumult X

#### Steam.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteam%2Fquantumult-x%2FSteam.list%2C%20tag%3DSteam%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Steam.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteam%2Fegern%2FSteam.yaml)


### Shadowrocket

#### Steam.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/shadowrocket/Steam.list
```

### sing-box

#### Steam.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/sing-box/Steam.srs
```

## Artifacts

### mrs(ipcidr)

#### Steam_IP.mrs

GitHub: [Steam_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/mihomo/Steam_IP.mrs)
Text: [Steam_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/mihomo/Steam_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/mihomo/Steam_IP.mrs
```

### mrs(domain)

#### Steam_Domain.mrs

GitHub: [Steam_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/mihomo/Steam_Domain.mrs)
Text: [Steam_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/mihomo/Steam_Domain.txt)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/mihomo/Steam_Domain.mrs
```

### yaml(remaining)

#### Steam.yaml

GitHub: [Steam.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/mihomo/Steam.yaml)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/mihomo/Steam.yaml
```

### Surge

#### Steam.list

GitHub: [Steam.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/surge/Steam.list)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/surge/Steam.list
```

#### Steam.domainset

GitHub: [Steam.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/surge/Steam.domainset)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/surge/Steam.domainset
```

### Loon

#### Steam.list

GitHub: [Steam.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/loon/Steam.list)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/loon/Steam.list
```

### Quantumult X

#### Steam.list

GitHub: [Steam.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/quantumult-x/Steam.list)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/quantumult-x/Steam.list
```

### Egern

#### Steam.yaml

GitHub: [Steam.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/egern/Steam.yaml)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/egern/Steam.yaml
```

### Shadowrocket

#### Steam.list

GitHub: [Steam.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/shadowrocket/Steam.list)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/shadowrocket/Steam.list
```

### sing-box

#### Steam.json

GitHub: [Steam.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/sing-box/Steam.json)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/sing-box/Steam.json
```

#### Steam.srs

GitHub: [Steam.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/sing-box/Steam.srs)
Source: [Steam.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Steam/Steam.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Steam/sing-box/Steam.srs
```
