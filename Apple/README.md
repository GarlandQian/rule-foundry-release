# Apple

Source config: [Apple.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Apple/Apple.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Apple | Apple rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [apple.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/apple.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Apple"
    type: select
    proxies: []
rules:
  - RULE-SET,Apple_Domain,Apple
  - RULE-SET,Apple,Apple,no-resolve
  - RULE-SET,Apple_IP,Apple,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Apple_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/mihomo/Apple_Domain.mrs }
  Apple: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/mihomo/Apple.yaml }
  Apple_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/mihomo/Apple_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/surge/Apple.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/surge/Apple.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/loon/Apple.list,policy=<policy>,tag=Apple,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/quantumult-x/Apple.list, tag=Apple, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/egern/Apple.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/shadowrocket/Apple.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Apple",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/sing-box/Apple.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Apple",
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

#### Apple.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/surge/Apple.list
```

#### Apple.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/surge/Apple.domainset
```

### Loon

#### Apple.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple%2Floon%2FApple.list)


### Quantumult X

#### Apple.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple%2Fquantumult-x%2FApple.list%2C%20tag%3DApple%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Apple.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple%2Fegern%2FApple.yaml)


### Shadowrocket

#### Apple.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/shadowrocket/Apple.list
```

### sing-box

#### Apple.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/sing-box/Apple.srs
```

## Artifacts

### mrs(ipcidr)

#### Apple_IP.mrs

GitHub: [Apple_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/mihomo/Apple_IP.mrs)
Text: [Apple_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/mihomo/Apple_IP.txt)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/mihomo/Apple_IP.mrs
```

### mrs(domain)

#### Apple_Domain.mrs

GitHub: [Apple_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/mihomo/Apple_Domain.mrs)
Text: [Apple_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/mihomo/Apple_Domain.txt)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/mihomo/Apple_Domain.mrs
```

### yaml(remaining)

#### Apple.yaml

GitHub: [Apple.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/mihomo/Apple.yaml)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/mihomo/Apple.yaml
```

### Surge

#### Apple.list

GitHub: [Apple.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/surge/Apple.list)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/surge/Apple.list
```

#### Apple.domainset

GitHub: [Apple.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/surge/Apple.domainset)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/surge/Apple.domainset
```

### Loon

#### Apple.list

GitHub: [Apple.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/loon/Apple.list)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/loon/Apple.list
```

### Quantumult X

#### Apple.list

GitHub: [Apple.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/quantumult-x/Apple.list)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/quantumult-x/Apple.list
```

### Egern

#### Apple.yaml

GitHub: [Apple.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/egern/Apple.yaml)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/egern/Apple.yaml
```

### Shadowrocket

#### Apple.list

GitHub: [Apple.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/shadowrocket/Apple.list)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/shadowrocket/Apple.list
```

### sing-box

#### Apple.json

GitHub: [Apple.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/sing-box/Apple.json)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/sing-box/Apple.json
```

#### Apple.srs

GitHub: [Apple.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/sing-box/Apple.srs)
Source: [Apple.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple/Apple.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple/sing-box/Apple.srs
```
