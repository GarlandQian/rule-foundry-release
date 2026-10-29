# HBO

Source config: [HBO.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/HBO/HBO.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| HBO | HBO rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [hbo.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/hbo.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "HBO"
    type: select
    proxies: []
rules:
  - RULE-SET,HBO_Domain,HBO
  - RULE-SET,HBO,HBO,no-resolve
  - RULE-SET,HBO_IP,HBO,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  HBO_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/mihomo/HBO_Domain.mrs }
  HBO: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/mihomo/HBO.yaml }
  HBO_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/mihomo/HBO_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/surge/HBO.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/surge/HBO.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/loon/HBO.list,policy=<policy>,tag=HBO,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/quantumult-x/HBO.list, tag=HBO, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/egern/HBO.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/shadowrocket/HBO.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "HBO",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/sing-box/HBO.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "HBO",
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

#### HBO.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/surge/HBO.list
```

#### HBO.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/surge/HBO.domainset
```

### Loon

#### HBO.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FHBO%2Floon%2FHBO.list)


### Quantumult X

#### HBO.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FHBO%2Fquantumult-x%2FHBO.list%2C%20tag%3DHBO%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### HBO.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FHBO%2Fegern%2FHBO.yaml)


### Shadowrocket

#### HBO.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/shadowrocket/HBO.list
```

### sing-box

#### HBO.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/sing-box/HBO.srs
```

## Artifacts

### mrs(ipcidr)

#### HBO_IP.mrs

GitHub: [HBO_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/mihomo/HBO_IP.mrs)
Text: [HBO_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/mihomo/HBO_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/mihomo/HBO_IP.mrs
```

### mrs(domain)

#### HBO_Domain.mrs

GitHub: [HBO_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/mihomo/HBO_Domain.mrs)
Text: [HBO_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/mihomo/HBO_Domain.txt)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/mihomo/HBO_Domain.mrs
```

### yaml(remaining)

#### HBO.yaml

GitHub: [HBO.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/mihomo/HBO.yaml)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/mihomo/HBO.yaml
```

### Surge

#### HBO.list

GitHub: [HBO.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/surge/HBO.list)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/surge/HBO.list
```

#### HBO.domainset

GitHub: [HBO.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/surge/HBO.domainset)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/surge/HBO.domainset
```

### Loon

#### HBO.list

GitHub: [HBO.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/loon/HBO.list)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/loon/HBO.list
```

### Quantumult X

#### HBO.list

GitHub: [HBO.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/quantumult-x/HBO.list)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/quantumult-x/HBO.list
```

### Egern

#### HBO.yaml

GitHub: [HBO.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/egern/HBO.yaml)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/egern/HBO.yaml
```

### Shadowrocket

#### HBO.list

GitHub: [HBO.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/shadowrocket/HBO.list)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/shadowrocket/HBO.list
```

### sing-box

#### HBO.json

GitHub: [HBO.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/sing-box/HBO.json)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/sing-box/HBO.json
```

#### HBO.srs

GitHub: [HBO.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/sing-box/HBO.srs)
Source: [HBO.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/HBO/HBO.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/HBO/sing-box/HBO.srs
```
