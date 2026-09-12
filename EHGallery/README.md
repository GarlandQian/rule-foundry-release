# EHGallery

Source config: [EHGallery.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/EHGallery/EHGallery.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| EHGallery | EHGallery | true | http | classical | yaml | rules |  | [EHGallery.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/EHGallery/EHGallery.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "EHGallery"
    type: select
    proxies: []
rules:
  - RULE-SET,EHGallery_Domain,EHGallery
  - RULE-SET,EHGallery_IP,EHGallery,no-resolve
  - RULE-SET,EHGallery,EHGallery,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  EHGallery_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/mihomo/EHGallery_Domain.mrs }
  EHGallery_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/mihomo/EHGallery_IP.mrs }
  EHGallery: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/mihomo/EHGallery.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/surge/EHGallery.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/surge/EHGallery.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/loon/EHGallery.list,policy=<policy>,tag=EHGallery,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/quantumult-x/EHGallery.list, tag=EHGallery, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/egern/EHGallery.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/shadowrocket/EHGallery.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "EHGallery",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/sing-box/EHGallery.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "EHGallery",
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

#### EHGallery.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/surge/EHGallery.list
```

#### EHGallery.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/surge/EHGallery.domainset
```

### Loon

#### EHGallery.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FEHGallery%2Floon%2FEHGallery.list)


### Quantumult X

#### EHGallery.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FEHGallery%2Fquantumult-x%2FEHGallery.list%2C%20tag%3DEHGallery%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### EHGallery.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FEHGallery%2Fegern%2FEHGallery.yaml)


### Shadowrocket

#### EHGallery.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/shadowrocket/EHGallery.list
```

### sing-box

#### EHGallery.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/sing-box/EHGallery.srs
```

## Artifacts

### mrs(ipcidr)

#### EHGallery_IP.mrs

GitHub: [EHGallery_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/mihomo/EHGallery_IP.mrs)
Text: [EHGallery_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/mihomo/EHGallery_IP.txt)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/mihomo/EHGallery_IP.mrs
```

### mrs(domain)

#### EHGallery_Domain.mrs

GitHub: [EHGallery_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/mihomo/EHGallery_Domain.mrs)
Text: [EHGallery_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/mihomo/EHGallery_Domain.txt)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/mihomo/EHGallery_Domain.mrs
```

### yaml(remaining)

#### EHGallery.yaml

GitHub: [EHGallery.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/mihomo/EHGallery.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/mihomo/EHGallery.yaml
```

### Surge

#### EHGallery.list

GitHub: [EHGallery.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/surge/EHGallery.list)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/surge/EHGallery.list
```

#### EHGallery.domainset

GitHub: [EHGallery.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/surge/EHGallery.domainset)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/surge/EHGallery.domainset
```

### Loon

#### EHGallery.list

GitHub: [EHGallery.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/loon/EHGallery.list)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/loon/EHGallery.list
```

### Quantumult X

#### EHGallery.list

GitHub: [EHGallery.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/quantumult-x/EHGallery.list)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/quantumult-x/EHGallery.list
```

### Egern

#### EHGallery.yaml

GitHub: [EHGallery.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/egern/EHGallery.yaml)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/egern/EHGallery.yaml
```

### Shadowrocket

#### EHGallery.list

GitHub: [EHGallery.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/shadowrocket/EHGallery.list)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/shadowrocket/EHGallery.list
```

### sing-box

#### EHGallery.json

GitHub: [EHGallery.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/sing-box/EHGallery.json)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/sing-box/EHGallery.json
```

#### EHGallery.srs

GitHub: [EHGallery.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/sing-box/EHGallery.srs)
Source: [EHGallery.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/EHGallery/EHGallery.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/EHGallery/sing-box/EHGallery.srs
```
