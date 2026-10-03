# Global

Source config: [Global.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Global/Global.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Global | Global proxy rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [proxy.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/proxy.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Global"
    type: select
    proxies: []
rules:
  - RULE-SET,Global_Domain,Global
  - RULE-SET,Global,Global,no-resolve
  - RULE-SET,Global_IP,Global,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Global_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/mihomo/Global_Domain.mrs }
  Global: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/mihomo/Global.yaml }
  Global_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/mihomo/Global_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/surge/Global.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/surge/Global.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/loon/Global.list,policy=<policy>,tag=Global,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/quantumult-x/Global.list, tag=Global, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/egern/Global.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/shadowrocket/Global.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Global",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/sing-box/Global.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Global",
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

#### Global.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/surge/Global.list
```

#### Global.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/surge/Global.domainset
```

### Loon

#### Global.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGlobal%2Floon%2FGlobal.list)


### Quantumult X

#### Global.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGlobal%2Fquantumult-x%2FGlobal.list%2C%20tag%3DGlobal%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Global.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGlobal%2Fegern%2FGlobal.yaml)


### Shadowrocket

#### Global.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/shadowrocket/Global.list
```

### sing-box

#### Global.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/sing-box/Global.srs
```

## Artifacts

### mrs(ipcidr)

#### Global_IP.mrs

GitHub: [Global_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/mihomo/Global_IP.mrs)
Text: [Global_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/mihomo/Global_IP.txt)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/mihomo/Global_IP.mrs
```

### mrs(domain)

#### Global_Domain.mrs

GitHub: [Global_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/mihomo/Global_Domain.mrs)
Text: [Global_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/mihomo/Global_Domain.txt)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/mihomo/Global_Domain.mrs
```

### yaml(remaining)

#### Global.yaml

GitHub: [Global.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/mihomo/Global.yaml)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/mihomo/Global.yaml
```

### Surge

#### Global.list

GitHub: [Global.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/surge/Global.list)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/surge/Global.list
```

#### Global.domainset

GitHub: [Global.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/surge/Global.domainset)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/surge/Global.domainset
```

### Loon

#### Global.list

GitHub: [Global.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/loon/Global.list)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/loon/Global.list
```

### Quantumult X

#### Global.list

GitHub: [Global.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/quantumult-x/Global.list)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/quantumult-x/Global.list
```

### Egern

#### Global.yaml

GitHub: [Global.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/egern/Global.yaml)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/egern/Global.yaml
```

### Shadowrocket

#### Global.list

GitHub: [Global.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/shadowrocket/Global.list)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/shadowrocket/Global.list
```

### sing-box

#### Global.json

GitHub: [Global.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/sing-box/Global.json)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/sing-box/Global.json
```

#### Global.srs

GitHub: [Global.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/sing-box/Global.srs)
Source: [Global.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Global/Global.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Global/sing-box/Global.srs
```
