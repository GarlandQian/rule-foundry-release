# BiliBili

Source config: [BiliBili.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/BiliBili/BiliBili.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| BiliBili | Bilibili rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [bilibili.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/bilibili.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "BiliBili"
    type: select
    proxies: []
rules:
  - RULE-SET,BiliBili_Domain,BiliBili
  - RULE-SET,BiliBili,BiliBili,no-resolve
  - RULE-SET,BiliBili_IP,BiliBili,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  BiliBili_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/mihomo/BiliBili_Domain.mrs }
  BiliBili: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/mihomo/BiliBili.yaml }
  BiliBili_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/mihomo/BiliBili_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/surge/BiliBili.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/surge/BiliBili.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/loon/BiliBili.list,policy=<policy>,tag=BiliBili,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/quantumult-x/BiliBili.list, tag=BiliBili, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/egern/BiliBili.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/shadowrocket/BiliBili.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "BiliBili",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/sing-box/BiliBili.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "BiliBili",
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

#### BiliBili.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/surge/BiliBili.list
```

#### BiliBili.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/surge/BiliBili.domainset
```

### Loon

#### BiliBili.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBiliBili%2Floon%2FBiliBili.list)


### Quantumult X

#### BiliBili.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBiliBili%2Fquantumult-x%2FBiliBili.list%2C%20tag%3DBiliBili%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### BiliBili.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBiliBili%2Fegern%2FBiliBili.yaml)


### Shadowrocket

#### BiliBili.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/shadowrocket/BiliBili.list
```

### sing-box

#### BiliBili.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/sing-box/BiliBili.srs
```

## Artifacts

### mrs(ipcidr)

#### BiliBili_IP.mrs

GitHub: [BiliBili_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/mihomo/BiliBili_IP.mrs)
Text: [BiliBili_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/mihomo/BiliBili_IP.txt)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/mihomo/BiliBili_IP.mrs
```

### mrs(domain)

#### BiliBili_Domain.mrs

GitHub: [BiliBili_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/mihomo/BiliBili_Domain.mrs)
Text: [BiliBili_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/mihomo/BiliBili_Domain.txt)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/mihomo/BiliBili_Domain.mrs
```

### yaml(remaining)

#### BiliBili.yaml

GitHub: [BiliBili.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/mihomo/BiliBili.yaml)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/mihomo/BiliBili.yaml
```

### Surge

#### BiliBili.list

GitHub: [BiliBili.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/surge/BiliBili.list)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/surge/BiliBili.list
```

#### BiliBili.domainset

GitHub: [BiliBili.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/surge/BiliBili.domainset)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/surge/BiliBili.domainset
```

### Loon

#### BiliBili.list

GitHub: [BiliBili.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/loon/BiliBili.list)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/loon/BiliBili.list
```

### Quantumult X

#### BiliBili.list

GitHub: [BiliBili.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/quantumult-x/BiliBili.list)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/quantumult-x/BiliBili.list
```

### Egern

#### BiliBili.yaml

GitHub: [BiliBili.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/egern/BiliBili.yaml)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/egern/BiliBili.yaml
```

### Shadowrocket

#### BiliBili.list

GitHub: [BiliBili.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/shadowrocket/BiliBili.list)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/shadowrocket/BiliBili.list
```

### sing-box

#### BiliBili.json

GitHub: [BiliBili.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/sing-box/BiliBili.json)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/sing-box/BiliBili.json
```

#### BiliBili.srs

GitHub: [BiliBili.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/sing-box/BiliBili.srs)
Source: [BiliBili.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BiliBili/BiliBili.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BiliBili/sing-box/BiliBili.srs
```
