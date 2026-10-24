# Instagram

Source config: [Instagram.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Instagram/Instagram.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Instagram | Instagram | true | http | classical | yaml | rules |  | [Instagram.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Instagram/Instagram.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Instagram"
    type: select
    proxies: []
rules:
  - RULE-SET,Instagram_Domain,Instagram
  - RULE-SET,Instagram,Instagram,no-resolve
  - RULE-SET,Instagram_IP,Instagram,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Instagram_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/mihomo/Instagram_Domain.mrs }
  Instagram: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/mihomo/Instagram.yaml }
  Instagram_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/mihomo/Instagram_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/surge/Instagram.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/surge/Instagram.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/loon/Instagram.list,policy=<policy>,tag=Instagram,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/quantumult-x/Instagram.list, tag=Instagram, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/egern/Instagram.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/shadowrocket/Instagram.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Instagram",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/sing-box/Instagram.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Instagram",
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

#### Instagram.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/surge/Instagram.list
```

#### Instagram.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/surge/Instagram.domainset
```

### Loon

#### Instagram.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FInstagram%2Floon%2FInstagram.list)


### Quantumult X

#### Instagram.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FInstagram%2Fquantumult-x%2FInstagram.list%2C%20tag%3DInstagram%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Instagram.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FInstagram%2Fegern%2FInstagram.yaml)


### Shadowrocket

#### Instagram.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/shadowrocket/Instagram.list
```

### sing-box

#### Instagram.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/sing-box/Instagram.srs
```

## Artifacts

### mrs(ipcidr)

#### Instagram_IP.mrs

GitHub: [Instagram_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/mihomo/Instagram_IP.mrs)
Text: [Instagram_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/mihomo/Instagram_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/mihomo/Instagram_IP.mrs
```

### mrs(domain)

#### Instagram_Domain.mrs

GitHub: [Instagram_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/mihomo/Instagram_Domain.mrs)
Text: [Instagram_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/mihomo/Instagram_Domain.txt)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/mihomo/Instagram_Domain.mrs
```

### yaml(remaining)

#### Instagram.yaml

GitHub: [Instagram.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/mihomo/Instagram.yaml)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/mihomo/Instagram.yaml
```

### Surge

#### Instagram.list

GitHub: [Instagram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/surge/Instagram.list)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/surge/Instagram.list
```

#### Instagram.domainset

GitHub: [Instagram.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/surge/Instagram.domainset)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/surge/Instagram.domainset
```

### Loon

#### Instagram.list

GitHub: [Instagram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/loon/Instagram.list)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/loon/Instagram.list
```

### Quantumult X

#### Instagram.list

GitHub: [Instagram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/quantumult-x/Instagram.list)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/quantumult-x/Instagram.list
```

### Egern

#### Instagram.yaml

GitHub: [Instagram.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/egern/Instagram.yaml)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/egern/Instagram.yaml
```

### Shadowrocket

#### Instagram.list

GitHub: [Instagram.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/shadowrocket/Instagram.list)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/shadowrocket/Instagram.list
```

### sing-box

#### Instagram.json

GitHub: [Instagram.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/sing-box/Instagram.json)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/sing-box/Instagram.json
```

#### Instagram.srs

GitHub: [Instagram.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/sing-box/Instagram.srs)
Source: [Instagram.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Instagram/Instagram.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Instagram/sing-box/Instagram.srs
```
