# Custom_Direct

Source config: [Custom_Direct.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Custom_Direct/Custom_Direct.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Custom_Direct | Custom_Direct | true | http | domain | mrs | rules |  | [Custom_Direct_Domain.mrs](https://raw.githubusercontent.com/Aethersailor/Custom_OpenClash_Rules/main/rule/Custom_Direct_Domain.mrs) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Custom_Direct"
    type: select
    proxies: []
rules:
  - RULE-SET,Custom_Direct_Domain,Custom_Direct
  - RULE-SET,Custom_Direct,Custom_Direct,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,Custom_Direct_IP,Custom_Direct,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Custom_Direct_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/mihomo/Custom_Direct_Domain.mrs }
  Custom_Direct: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/mihomo/Custom_Direct.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  Custom_Direct_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/mihomo/Custom_Direct_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/surge/Custom_Direct.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/surge/Custom_Direct.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/loon/Custom_Direct.list,policy=<policy>,tag=Custom_Direct,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/quantumult-x/Custom_Direct.list, tag=Custom_Direct, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/egern/Custom_Direct.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/shadowrocket/Custom_Direct.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Custom_Direct",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/sing-box/Custom_Direct.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Custom_Direct",
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

#### Custom_Direct.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/surge/Custom_Direct.list
```

#### Custom_Direct.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/surge/Custom_Direct.domainset
```

### Loon

#### Custom_Direct.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCustom_Direct%2Floon%2FCustom_Direct.list)


### Quantumult X

#### Custom_Direct.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCustom_Direct%2Fquantumult-x%2FCustom_Direct.list%2C%20tag%3DCustom_Direct%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Custom_Direct.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCustom_Direct%2Fegern%2FCustom_Direct.yaml)


### Shadowrocket

#### Custom_Direct.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/shadowrocket/Custom_Direct.list
```

### sing-box

#### Custom_Direct.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/sing-box/Custom_Direct.srs
```

## Artifacts

### mrs(ipcidr)

#### Custom_Direct_IP.mrs

GitHub: [Custom_Direct_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/mihomo/Custom_Direct_IP.mrs)
Text: [Custom_Direct_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/mihomo/Custom_Direct_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/mihomo/Custom_Direct_IP.mrs
```

### mrs(domain)

#### Custom_Direct_Domain.mrs

GitHub: [Custom_Direct_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/mihomo/Custom_Direct_Domain.mrs)
Text: [Custom_Direct_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/mihomo/Custom_Direct_Domain.txt)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/mihomo/Custom_Direct_Domain.mrs
```

### yaml(remaining)

#### Custom_Direct.yaml

GitHub: [Custom_Direct.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/mihomo/Custom_Direct.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/mihomo/Custom_Direct.yaml
```

### Surge

#### Custom_Direct.list

GitHub: [Custom_Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/surge/Custom_Direct.list)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/surge/Custom_Direct.list
```

#### Custom_Direct.domainset

GitHub: [Custom_Direct.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/surge/Custom_Direct.domainset)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/surge/Custom_Direct.domainset
```

### Loon

#### Custom_Direct.list

GitHub: [Custom_Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/loon/Custom_Direct.list)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/loon/Custom_Direct.list
```

### Quantumult X

#### Custom_Direct.list

GitHub: [Custom_Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/quantumult-x/Custom_Direct.list)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/quantumult-x/Custom_Direct.list
```

### Egern

#### Custom_Direct.yaml

GitHub: [Custom_Direct.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/egern/Custom_Direct.yaml)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/egern/Custom_Direct.yaml
```

### Shadowrocket

#### Custom_Direct.list

GitHub: [Custom_Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/shadowrocket/Custom_Direct.list)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/shadowrocket/Custom_Direct.list
```

### sing-box

#### Custom_Direct.json

GitHub: [Custom_Direct.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/sing-box/Custom_Direct.json)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/sing-box/Custom_Direct.json
```

#### Custom_Direct.srs

GitHub: [Custom_Direct.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/sing-box/Custom_Direct.srs)
Source: [Custom_Direct.original.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Direct/Custom_Direct.original.mrs)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Direct/sing-box/Custom_Direct.srs
```
