# SpeedtestInternational

Source config: [SpeedtestInternational.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/SpeedtestInternational/SpeedtestInternational.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| SpeedtestInternational | International speed tests, excluding China speed tests, from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [speedtest.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/speedtest.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "SpeedtestInternational"
    type: select
    proxies: []
rules:
  - RULE-SET,SpeedtestInternational_Domain,SpeedtestInternational
  - RULE-SET,SpeedtestInternational,SpeedtestInternational,no-resolve
  - RULE-SET,SpeedtestInternational_IP,SpeedtestInternational,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  SpeedtestInternational_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/mihomo/SpeedtestInternational_Domain.mrs }
  SpeedtestInternational: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/mihomo/SpeedtestInternational.yaml }
  SpeedtestInternational_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/mihomo/SpeedtestInternational_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/surge/SpeedtestInternational.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/surge/SpeedtestInternational.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/loon/SpeedtestInternational.list,policy=<policy>,tag=SpeedtestInternational,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/quantumult-x/SpeedtestInternational.list, tag=SpeedtestInternational, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/egern/SpeedtestInternational.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/shadowrocket/SpeedtestInternational.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "SpeedtestInternational",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/sing-box/SpeedtestInternational.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "SpeedtestInternational",
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

#### SpeedtestInternational.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/surge/SpeedtestInternational.list
```

#### SpeedtestInternational.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/surge/SpeedtestInternational.domainset
```

### Loon

#### SpeedtestInternational.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSpeedtestInternational%2Floon%2FSpeedtestInternational.list)


### Quantumult X

#### SpeedtestInternational.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSpeedtestInternational%2Fquantumult-x%2FSpeedtestInternational.list%2C%20tag%3DSpeedtestInternational%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### SpeedtestInternational.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSpeedtestInternational%2Fegern%2FSpeedtestInternational.yaml)


### Shadowrocket

#### SpeedtestInternational.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/shadowrocket/SpeedtestInternational.list
```

### sing-box

#### SpeedtestInternational.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/sing-box/SpeedtestInternational.srs
```

## Artifacts

### mrs(ipcidr)

#### SpeedtestInternational_IP.mrs

GitHub: [SpeedtestInternational_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/mihomo/SpeedtestInternational_IP.mrs)
Text: [SpeedtestInternational_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/mihomo/SpeedtestInternational_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/mihomo/SpeedtestInternational_IP.mrs
```

### mrs(domain)

#### SpeedtestInternational_Domain.mrs

GitHub: [SpeedtestInternational_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/mihomo/SpeedtestInternational_Domain.mrs)
Text: [SpeedtestInternational_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/mihomo/SpeedtestInternational_Domain.txt)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/mihomo/SpeedtestInternational_Domain.mrs
```

### yaml(remaining)

#### SpeedtestInternational.yaml

GitHub: [SpeedtestInternational.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/mihomo/SpeedtestInternational.yaml)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/mihomo/SpeedtestInternational.yaml
```

### Surge

#### SpeedtestInternational.list

GitHub: [SpeedtestInternational.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/surge/SpeedtestInternational.list)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/surge/SpeedtestInternational.list
```

#### SpeedtestInternational.domainset

GitHub: [SpeedtestInternational.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/surge/SpeedtestInternational.domainset)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/surge/SpeedtestInternational.domainset
```

### Loon

#### SpeedtestInternational.list

GitHub: [SpeedtestInternational.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/loon/SpeedtestInternational.list)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/loon/SpeedtestInternational.list
```

### Quantumult X

#### SpeedtestInternational.list

GitHub: [SpeedtestInternational.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/quantumult-x/SpeedtestInternational.list)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/quantumult-x/SpeedtestInternational.list
```

### Egern

#### SpeedtestInternational.yaml

GitHub: [SpeedtestInternational.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/egern/SpeedtestInternational.yaml)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/egern/SpeedtestInternational.yaml
```

### Shadowrocket

#### SpeedtestInternational.list

GitHub: [SpeedtestInternational.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/shadowrocket/SpeedtestInternational.list)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/shadowrocket/SpeedtestInternational.list
```

### sing-box

#### SpeedtestInternational.json

GitHub: [SpeedtestInternational.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/sing-box/SpeedtestInternational.json)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/sing-box/SpeedtestInternational.json
```

#### SpeedtestInternational.srs

GitHub: [SpeedtestInternational.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/sing-box/SpeedtestInternational.srs)
Source: [SpeedtestInternational.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SpeedtestInternational/SpeedtestInternational.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SpeedtestInternational/sing-box/SpeedtestInternational.srs
```
