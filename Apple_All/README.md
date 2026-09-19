# Apple_All

Source config: [Apple_All.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Apple_All/Apple_All.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Apple_All | Apple rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [apple.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/apple.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Apple_All"
    type: select
    proxies: []
rules:
  - RULE-SET,Apple_All_Domain,Apple_All
  - RULE-SET,Apple_All,Apple_All,no-resolve
  - RULE-SET,Apple_All_IP,Apple_All,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Apple_All_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/mihomo/Apple_All_Domain.mrs }
  Apple_All: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/mihomo/Apple_All.yaml }
  Apple_All_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/mihomo/Apple_All_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/surge/Apple_All.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/surge/Apple_All.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/loon/Apple_All.list,policy=<policy>,tag=Apple_All,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/quantumult-x/Apple_All.list, tag=Apple_All, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/egern/Apple_All.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/shadowrocket/Apple_All.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Apple_All",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/sing-box/Apple_All.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Apple_All",
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

#### Apple_All.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/surge/Apple_All.list
```

#### Apple_All.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/surge/Apple_All.domainset
```

### Loon

#### Apple_All.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_All%2Floon%2FApple_All.list)


### Quantumult X

#### Apple_All.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_All%2Fquantumult-x%2FApple_All.list%2C%20tag%3DApple_All%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Apple_All.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_All%2Fegern%2FApple_All.yaml)


### Shadowrocket

#### Apple_All.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/shadowrocket/Apple_All.list
```

### sing-box

#### Apple_All.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/sing-box/Apple_All.srs
```

## Artifacts

### mrs(ipcidr)

#### Apple_All_IP.mrs

GitHub: [Apple_All_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/mihomo/Apple_All_IP.mrs)
Text: [Apple_All_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/mihomo/Apple_All_IP.txt)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/mihomo/Apple_All_IP.mrs
```

### mrs(domain)

#### Apple_All_Domain.mrs

GitHub: [Apple_All_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/mihomo/Apple_All_Domain.mrs)
Text: [Apple_All_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/mihomo/Apple_All_Domain.txt)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/mihomo/Apple_All_Domain.mrs
```

### yaml(remaining)

#### Apple_All.yaml

GitHub: [Apple_All.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/mihomo/Apple_All.yaml)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/mihomo/Apple_All.yaml
```

### Surge

#### Apple_All.list

GitHub: [Apple_All.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/surge/Apple_All.list)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/surge/Apple_All.list
```

#### Apple_All.domainset

GitHub: [Apple_All.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/surge/Apple_All.domainset)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/surge/Apple_All.domainset
```

### Loon

#### Apple_All.list

GitHub: [Apple_All.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/loon/Apple_All.list)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/loon/Apple_All.list
```

### Quantumult X

#### Apple_All.list

GitHub: [Apple_All.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/quantumult-x/Apple_All.list)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/quantumult-x/Apple_All.list
```

### Egern

#### Apple_All.yaml

GitHub: [Apple_All.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/egern/Apple_All.yaml)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/egern/Apple_All.yaml
```

### Shadowrocket

#### Apple_All.list

GitHub: [Apple_All.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/shadowrocket/Apple_All.list)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/shadowrocket/Apple_All.list
```

### sing-box

#### Apple_All.json

GitHub: [Apple_All.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/sing-box/Apple_All.json)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/sing-box/Apple_All.json
```

#### Apple_All.srs

GitHub: [Apple_All.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/sing-box/Apple_All.srs)
Source: [Apple_All.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_All/Apple_All.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_All/sing-box/Apple_All.srs
```
