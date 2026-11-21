# LoyalsoldierDirect

Source config: [LoyalsoldierDirect.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/LoyalsoldierDirect/LoyalsoldierDirect.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| LoyalsoldierDirect | Loyalsoldier Direct Rules | true | http | domain | yaml | rules |  | [direct.txt](https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/direct.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "LoyalsoldierDirect"
    type: select
    proxies: []
rules:
  - RULE-SET,LoyalsoldierDirect_Domain,LoyalsoldierDirect
  - RULE-SET,LoyalsoldierDirect,LoyalsoldierDirect,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,LoyalsoldierDirect_IP,LoyalsoldierDirect,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  LoyalsoldierDirect_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_Domain.mrs }
  LoyalsoldierDirect: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  LoyalsoldierDirect_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/loon/LoyalsoldierDirect.list,policy=<policy>,tag=LoyalsoldierDirect,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/quantumult-x/LoyalsoldierDirect.list, tag=LoyalsoldierDirect, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/egern/LoyalsoldierDirect.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/shadowrocket/LoyalsoldierDirect.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "LoyalsoldierDirect",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/sing-box/LoyalsoldierDirect.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "LoyalsoldierDirect",
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

#### LoyalsoldierDirect.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.list
```

#### LoyalsoldierDirect.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.domainset
```

### Loon

#### LoyalsoldierDirect.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierDirect%2Floon%2FLoyalsoldierDirect.list)


### Quantumult X

#### LoyalsoldierDirect.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierDirect%2Fquantumult-x%2FLoyalsoldierDirect.list%2C%20tag%3DLoyalsoldierDirect%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### LoyalsoldierDirect.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierDirect%2Fegern%2FLoyalsoldierDirect.yaml)


### Shadowrocket

#### LoyalsoldierDirect.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/shadowrocket/LoyalsoldierDirect.list
```

### sing-box

#### LoyalsoldierDirect.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/sing-box/LoyalsoldierDirect.srs
```

## Artifacts

### mrs(ipcidr)

#### LoyalsoldierDirect_IP.mrs

GitHub: [LoyalsoldierDirect_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_IP.mrs)
Text: [LoyalsoldierDirect_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_IP.mrs
```

### mrs(domain)

#### LoyalsoldierDirect_Domain.mrs

GitHub: [LoyalsoldierDirect_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_Domain.mrs)
Text: [LoyalsoldierDirect_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_Domain.txt)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect_Domain.mrs
```

### yaml(remaining)

#### LoyalsoldierDirect.yaml

GitHub: [LoyalsoldierDirect.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/mihomo/LoyalsoldierDirect.yaml
```

### Surge

#### LoyalsoldierDirect.list

GitHub: [LoyalsoldierDirect.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.list)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.list
```

#### LoyalsoldierDirect.domainset

GitHub: [LoyalsoldierDirect.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.domainset)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/surge/LoyalsoldierDirect.domainset
```

### Loon

#### LoyalsoldierDirect.list

GitHub: [LoyalsoldierDirect.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/loon/LoyalsoldierDirect.list)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/loon/LoyalsoldierDirect.list
```

### Quantumult X

#### LoyalsoldierDirect.list

GitHub: [LoyalsoldierDirect.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/quantumult-x/LoyalsoldierDirect.list)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/quantumult-x/LoyalsoldierDirect.list
```

### Egern

#### LoyalsoldierDirect.yaml

GitHub: [LoyalsoldierDirect.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/egern/LoyalsoldierDirect.yaml)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/egern/LoyalsoldierDirect.yaml
```

### Shadowrocket

#### LoyalsoldierDirect.list

GitHub: [LoyalsoldierDirect.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/shadowrocket/LoyalsoldierDirect.list)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/shadowrocket/LoyalsoldierDirect.list
```

### sing-box

#### LoyalsoldierDirect.json

GitHub: [LoyalsoldierDirect.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/sing-box/LoyalsoldierDirect.json)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/sing-box/LoyalsoldierDirect.json
```

#### LoyalsoldierDirect.srs

GitHub: [LoyalsoldierDirect.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/sing-box/LoyalsoldierDirect.srs)
Source: [LoyalsoldierDirect.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierDirect/LoyalsoldierDirect.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierDirect/sing-box/LoyalsoldierDirect.srs
```
