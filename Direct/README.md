# Direct

Source config: [Direct.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Direct/Direct.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Direct | Direct | true | http | classical | yaml | rules |  | [Direct.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Direct/Direct.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Direct"
    type: select
    proxies: []
rules:
  - RULE-SET,Direct_Domain,Direct
  - RULE-SET,Direct,Direct,no-resolve
  - RULE-SET,Direct_IP,Direct,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Direct_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/mihomo/Direct_Domain.mrs }
  Direct: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/mihomo/Direct.yaml }
  Direct_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/mihomo/Direct_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/surge/Direct.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/surge/Direct.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/loon/Direct.list,policy=<policy>,tag=Direct,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/quantumult-x/Direct.list, tag=Direct, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/egern/Direct.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/shadowrocket/Direct.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Direct",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/sing-box/Direct.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Direct",
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

#### Direct.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/surge/Direct.list
```

#### Direct.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/surge/Direct.domainset
```

### Loon

#### Direct.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDirect%2Floon%2FDirect.list)


### Quantumult X

#### Direct.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDirect%2Fquantumult-x%2FDirect.list%2C%20tag%3DDirect%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Direct.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDirect%2Fegern%2FDirect.yaml)


### Shadowrocket

#### Direct.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/shadowrocket/Direct.list
```

### sing-box

#### Direct.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/sing-box/Direct.srs
```

## Artifacts

### mrs(ipcidr)

#### Direct_IP.mrs

GitHub: [Direct_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/mihomo/Direct_IP.mrs)
Text: [Direct_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/mihomo/Direct_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/mihomo/Direct_IP.mrs
```

### mrs(domain)

#### Direct_Domain.mrs

GitHub: [Direct_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/mihomo/Direct_Domain.mrs)
Text: [Direct_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/mihomo/Direct_Domain.txt)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/mihomo/Direct_Domain.mrs
```

### yaml(remaining)

#### Direct.yaml

GitHub: [Direct.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/mihomo/Direct.yaml)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/mihomo/Direct.yaml
```

### Surge

#### Direct.list

GitHub: [Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/surge/Direct.list)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/surge/Direct.list
```

#### Direct.domainset

GitHub: [Direct.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/surge/Direct.domainset)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/surge/Direct.domainset
```

### Loon

#### Direct.list

GitHub: [Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/loon/Direct.list)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/loon/Direct.list
```

### Quantumult X

#### Direct.list

GitHub: [Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/quantumult-x/Direct.list)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/quantumult-x/Direct.list
```

### Egern

#### Direct.yaml

GitHub: [Direct.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/egern/Direct.yaml)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/egern/Direct.yaml
```

### Shadowrocket

#### Direct.list

GitHub: [Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/shadowrocket/Direct.list)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/shadowrocket/Direct.list
```

### sing-box

#### Direct.json

GitHub: [Direct.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/sing-box/Direct.json)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/sing-box/Direct.json
```

#### Direct.srs

GitHub: [Direct.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/sing-box/Direct.srs)
Source: [Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Direct/Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Direct/sing-box/Direct.srs
```
