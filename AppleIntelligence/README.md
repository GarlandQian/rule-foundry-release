# AppleIntelligence

Source config: [AppleIntelligence.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/AppleIntelligence/AppleIntelligence.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| AppleIntelligence | Apple Intelligence rules from MagicRule | true | magicrule | classical | yaml | rules |  | [magicrule.pages.dev](https://magicrule.pages.dev/#/c/Mihomo/r/fb5031ac-df12-4202-ae19-cace89839599) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "AppleIntelligence"
    type: select
    proxies: []
rules:
  - RULE-SET,AppleIntelligence_Domain,AppleIntelligence
  - RULE-SET,AppleIntelligence,AppleIntelligence,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,AppleIntelligence_IP,AppleIntelligence,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  AppleIntelligence_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/mihomo/AppleIntelligence_Domain.mrs }
  AppleIntelligence: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/mihomo/AppleIntelligence.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  AppleIntelligence_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/mihomo/AppleIntelligence_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/surge/AppleIntelligence.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/surge/AppleIntelligence.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/loon/AppleIntelligence.list,policy=<policy>,tag=AppleIntelligence,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/quantumult-x/AppleIntelligence.list, tag=AppleIntelligence, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/egern/AppleIntelligence.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/shadowrocket/AppleIntelligence.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "AppleIntelligence",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/sing-box/AppleIntelligence.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "AppleIntelligence",
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

#### AppleIntelligence.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/surge/AppleIntelligence.list
```

#### AppleIntelligence.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/surge/AppleIntelligence.domainset
```

### Loon

#### AppleIntelligence.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleIntelligence%2Floon%2FAppleIntelligence.list)


### Quantumult X

#### AppleIntelligence.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleIntelligence%2Fquantumult-x%2FAppleIntelligence.list%2C%20tag%3DAppleIntelligence%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### AppleIntelligence.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleIntelligence%2Fegern%2FAppleIntelligence.yaml)


### Shadowrocket

#### AppleIntelligence.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/shadowrocket/AppleIntelligence.list
```

### sing-box

#### AppleIntelligence.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/sing-box/AppleIntelligence.srs
```

## Artifacts

### mrs(ipcidr)

#### AppleIntelligence_IP.mrs

GitHub: [AppleIntelligence_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/mihomo/AppleIntelligence_IP.mrs)
Text: [AppleIntelligence_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/mihomo/AppleIntelligence_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/mihomo/AppleIntelligence_IP.mrs
```

### mrs(domain)

#### AppleIntelligence_Domain.mrs

GitHub: [AppleIntelligence_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/mihomo/AppleIntelligence_Domain.mrs)
Text: [AppleIntelligence_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/mihomo/AppleIntelligence_Domain.txt)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/mihomo/AppleIntelligence_Domain.mrs
```

### yaml(remaining)

#### AppleIntelligence.yaml

GitHub: [AppleIntelligence.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/mihomo/AppleIntelligence.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/mihomo/AppleIntelligence.yaml
```

### Surge

#### AppleIntelligence.list

GitHub: [AppleIntelligence.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/surge/AppleIntelligence.list)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/surge/AppleIntelligence.list
```

#### AppleIntelligence.domainset

GitHub: [AppleIntelligence.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/surge/AppleIntelligence.domainset)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/surge/AppleIntelligence.domainset
```

### Loon

#### AppleIntelligence.list

GitHub: [AppleIntelligence.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/loon/AppleIntelligence.list)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/loon/AppleIntelligence.list
```

### Quantumult X

#### AppleIntelligence.list

GitHub: [AppleIntelligence.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/quantumult-x/AppleIntelligence.list)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/quantumult-x/AppleIntelligence.list
```

### Egern

#### AppleIntelligence.yaml

GitHub: [AppleIntelligence.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/egern/AppleIntelligence.yaml)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/egern/AppleIntelligence.yaml
```

### Shadowrocket

#### AppleIntelligence.list

GitHub: [AppleIntelligence.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/shadowrocket/AppleIntelligence.list)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/shadowrocket/AppleIntelligence.list
```

### sing-box

#### AppleIntelligence.json

GitHub: [AppleIntelligence.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/sing-box/AppleIntelligence.json)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/sing-box/AppleIntelligence.json
```

#### AppleIntelligence.srs

GitHub: [AppleIntelligence.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/sing-box/AppleIntelligence.srs)
Source: [AppleIntelligence.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleIntelligence/AppleIntelligence.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleIntelligence/sing-box/AppleIntelligence.srs
```
