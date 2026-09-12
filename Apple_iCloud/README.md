# Apple_iCloud

Source config: [Apple_iCloud.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Apple_iCloud/Apple_iCloud.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Apple_iCloud | Apple_iCloud | true | http | classical | yaml | rules |  | [iCloud.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/iCloud/iCloud.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Apple_iCloud"
    type: select
    proxies: []
rules:
  - RULE-SET,Apple_iCloud_Domain,Apple_iCloud
  - RULE-SET,Apple_iCloud,Apple_iCloud,no-resolve
  - RULE-SET,Apple_iCloud_IP,Apple_iCloud,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Apple_iCloud_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/mihomo/Apple_iCloud_Domain.mrs }
  Apple_iCloud: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/mihomo/Apple_iCloud.yaml }
  Apple_iCloud_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/mihomo/Apple_iCloud_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/surge/Apple_iCloud.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/surge/Apple_iCloud.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/loon/Apple_iCloud.list,policy=<policy>,tag=Apple_iCloud,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/quantumult-x/Apple_iCloud.list, tag=Apple_iCloud, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/egern/Apple_iCloud.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/shadowrocket/Apple_iCloud.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Apple_iCloud",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/sing-box/Apple_iCloud.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Apple_iCloud",
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

#### Apple_iCloud.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/surge/Apple_iCloud.list
```

#### Apple_iCloud.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/surge/Apple_iCloud.domainset
```

### Loon

#### Apple_iCloud.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_iCloud%2Floon%2FApple_iCloud.list)


### Quantumult X

#### Apple_iCloud.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_iCloud%2Fquantumult-x%2FApple_iCloud.list%2C%20tag%3DApple_iCloud%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Apple_iCloud.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_iCloud%2Fegern%2FApple_iCloud.yaml)


### Shadowrocket

#### Apple_iCloud.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/shadowrocket/Apple_iCloud.list
```

### sing-box

#### Apple_iCloud.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/sing-box/Apple_iCloud.srs
```

## Artifacts

### mrs(ipcidr)

#### Apple_iCloud_IP.mrs

GitHub: [Apple_iCloud_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/mihomo/Apple_iCloud_IP.mrs)
Text: [Apple_iCloud_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/mihomo/Apple_iCloud_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/mihomo/Apple_iCloud_IP.mrs
```

### mrs(domain)

#### Apple_iCloud_Domain.mrs

GitHub: [Apple_iCloud_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/mihomo/Apple_iCloud_Domain.mrs)
Text: [Apple_iCloud_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/mihomo/Apple_iCloud_Domain.txt)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/mihomo/Apple_iCloud_Domain.mrs
```

### yaml(remaining)

#### Apple_iCloud.yaml

GitHub: [Apple_iCloud.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/mihomo/Apple_iCloud.yaml)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/mihomo/Apple_iCloud.yaml
```

### Surge

#### Apple_iCloud.list

GitHub: [Apple_iCloud.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/surge/Apple_iCloud.list)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/surge/Apple_iCloud.list
```

#### Apple_iCloud.domainset

GitHub: [Apple_iCloud.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/surge/Apple_iCloud.domainset)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/surge/Apple_iCloud.domainset
```

### Loon

#### Apple_iCloud.list

GitHub: [Apple_iCloud.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/loon/Apple_iCloud.list)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/loon/Apple_iCloud.list
```

### Quantumult X

#### Apple_iCloud.list

GitHub: [Apple_iCloud.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/quantumult-x/Apple_iCloud.list)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/quantumult-x/Apple_iCloud.list
```

### Egern

#### Apple_iCloud.yaml

GitHub: [Apple_iCloud.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/egern/Apple_iCloud.yaml)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/egern/Apple_iCloud.yaml
```

### Shadowrocket

#### Apple_iCloud.list

GitHub: [Apple_iCloud.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/shadowrocket/Apple_iCloud.list)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/shadowrocket/Apple_iCloud.list
```

### sing-box

#### Apple_iCloud.json

GitHub: [Apple_iCloud.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/sing-box/Apple_iCloud.json)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/sing-box/Apple_iCloud.json
```

#### Apple_iCloud.srs

GitHub: [Apple_iCloud.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/sing-box/Apple_iCloud.srs)
Source: [Apple_iCloud.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_iCloud/Apple_iCloud.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_iCloud/sing-box/Apple_iCloud.srs
```
