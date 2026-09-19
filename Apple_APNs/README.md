# Apple_APNs

Source config: [Apple_APNs.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Apple_APNs/Apple_APNs.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Apple_APNs | APNs rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [apns.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/apns.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Apple_APNs"
    type: select
    proxies: []
rules:
  - RULE-SET,Apple_APNs_Domain,Apple_APNs
  - RULE-SET,Apple_APNs,Apple_APNs,no-resolve
  - RULE-SET,Apple_APNs_IP,Apple_APNs,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Apple_APNs_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/mihomo/Apple_APNs_Domain.mrs }
  Apple_APNs: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/mihomo/Apple_APNs.yaml }
  Apple_APNs_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/mihomo/Apple_APNs_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/surge/Apple_APNs.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/surge/Apple_APNs.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/loon/Apple_APNs.list,policy=<policy>,tag=Apple_APNs,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/quantumult-x/Apple_APNs.list, tag=Apple_APNs, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/egern/Apple_APNs.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/shadowrocket/Apple_APNs.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Apple_APNs",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/sing-box/Apple_APNs.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Apple_APNs",
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

#### Apple_APNs.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/surge/Apple_APNs.list
```

#### Apple_APNs.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/surge/Apple_APNs.domainset
```

### Loon

#### Apple_APNs.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_APNs%2Floon%2FApple_APNs.list)


### Quantumult X

#### Apple_APNs.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_APNs%2Fquantumult-x%2FApple_APNs.list%2C%20tag%3DApple_APNs%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Apple_APNs.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_APNs%2Fegern%2FApple_APNs.yaml)


### Shadowrocket

#### Apple_APNs.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/shadowrocket/Apple_APNs.list
```

### sing-box

#### Apple_APNs.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/sing-box/Apple_APNs.srs
```

## Artifacts

### mrs(ipcidr)

#### Apple_APNs_IP.mrs

GitHub: [Apple_APNs_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/mihomo/Apple_APNs_IP.mrs)
Text: [Apple_APNs_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/mihomo/Apple_APNs_IP.txt)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/mihomo/Apple_APNs_IP.mrs
```

### mrs(domain)

#### Apple_APNs_Domain.mrs

GitHub: [Apple_APNs_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/mihomo/Apple_APNs_Domain.mrs)
Text: [Apple_APNs_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/mihomo/Apple_APNs_Domain.txt)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/mihomo/Apple_APNs_Domain.mrs
```

### yaml(remaining)

#### Apple_APNs.yaml

GitHub: [Apple_APNs.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/mihomo/Apple_APNs.yaml)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/mihomo/Apple_APNs.yaml
```

### Surge

#### Apple_APNs.list

GitHub: [Apple_APNs.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/surge/Apple_APNs.list)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/surge/Apple_APNs.list
```

#### Apple_APNs.domainset

GitHub: [Apple_APNs.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/surge/Apple_APNs.domainset)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/surge/Apple_APNs.domainset
```

### Loon

#### Apple_APNs.list

GitHub: [Apple_APNs.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/loon/Apple_APNs.list)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/loon/Apple_APNs.list
```

### Quantumult X

#### Apple_APNs.list

GitHub: [Apple_APNs.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/quantumult-x/Apple_APNs.list)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/quantumult-x/Apple_APNs.list
```

### Egern

#### Apple_APNs.yaml

GitHub: [Apple_APNs.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/egern/Apple_APNs.yaml)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/egern/Apple_APNs.yaml
```

### Shadowrocket

#### Apple_APNs.list

GitHub: [Apple_APNs.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/shadowrocket/Apple_APNs.list)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/shadowrocket/Apple_APNs.list
```

### sing-box

#### Apple_APNs.json

GitHub: [Apple_APNs.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/sing-box/Apple_APNs.json)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/sing-box/Apple_APNs.json
```

#### Apple_APNs.srs

GitHub: [Apple_APNs.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/sing-box/Apple_APNs.srs)
Source: [Apple_APNs.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_APNs/Apple_APNs.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_APNs/sing-box/Apple_APNs.srs
```
