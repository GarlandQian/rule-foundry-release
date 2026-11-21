# IPCheck

Source config: [IPCheck.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/IPCheck/IPCheck.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| IPCheck | IP geolocation and network diagnostic rules from Yuu518/Yuu-rules | true | http | classical | text | rules |  | [category-ip-geo-detect.list](https://raw.githubusercontent.com/Yuu518/Yuu-rules/rule-set/mihomo/geosite/classical/category-ip-geo-detect.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "IPCheck"
    type: select
    proxies: []
rules:
  - RULE-SET,IPCheck_Domain,IPCheck
  - RULE-SET,IPCheck,IPCheck,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,IPCheck_IP,IPCheck,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  IPCheck_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/mihomo/IPCheck_Domain.mrs }
  IPCheck: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/mihomo/IPCheck.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  IPCheck_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/mihomo/IPCheck_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/surge/IPCheck.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/surge/IPCheck.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/loon/IPCheck.list,policy=<policy>,tag=IPCheck,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/quantumult-x/IPCheck.list, tag=IPCheck, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/egern/IPCheck.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/shadowrocket/IPCheck.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "IPCheck",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/sing-box/IPCheck.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "IPCheck",
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

#### IPCheck.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/surge/IPCheck.list
```

#### IPCheck.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/surge/IPCheck.domainset
```

### Loon

#### IPCheck.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FIPCheck%2Floon%2FIPCheck.list)


### Quantumult X

#### IPCheck.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FIPCheck%2Fquantumult-x%2FIPCheck.list%2C%20tag%3DIPCheck%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### IPCheck.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FIPCheck%2Fegern%2FIPCheck.yaml)


### Shadowrocket

#### IPCheck.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/shadowrocket/IPCheck.list
```

### sing-box

#### IPCheck.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/sing-box/IPCheck.srs
```

## Artifacts

### mrs(ipcidr)

#### IPCheck_IP.mrs

GitHub: [IPCheck_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/mihomo/IPCheck_IP.mrs)
Text: [IPCheck_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/mihomo/IPCheck_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/mihomo/IPCheck_IP.mrs
```

### mrs(domain)

#### IPCheck_Domain.mrs

GitHub: [IPCheck_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/mihomo/IPCheck_Domain.mrs)
Text: [IPCheck_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/mihomo/IPCheck_Domain.txt)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/mihomo/IPCheck_Domain.mrs
```

### yaml(remaining)

#### IPCheck.yaml

GitHub: [IPCheck.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/mihomo/IPCheck.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/mihomo/IPCheck.yaml
```

### Surge

#### IPCheck.list

GitHub: [IPCheck.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/surge/IPCheck.list)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/surge/IPCheck.list
```

#### IPCheck.domainset

GitHub: [IPCheck.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/surge/IPCheck.domainset)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/surge/IPCheck.domainset
```

### Loon

#### IPCheck.list

GitHub: [IPCheck.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/loon/IPCheck.list)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/loon/IPCheck.list
```

### Quantumult X

#### IPCheck.list

GitHub: [IPCheck.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/quantumult-x/IPCheck.list)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/quantumult-x/IPCheck.list
```

### Egern

#### IPCheck.yaml

GitHub: [IPCheck.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/egern/IPCheck.yaml)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/egern/IPCheck.yaml
```

### Shadowrocket

#### IPCheck.list

GitHub: [IPCheck.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/shadowrocket/IPCheck.list)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/shadowrocket/IPCheck.list
```

### sing-box

#### IPCheck.json

GitHub: [IPCheck.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/sing-box/IPCheck.json)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/sing-box/IPCheck.json
```

#### IPCheck.srs

GitHub: [IPCheck.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/sing-box/IPCheck.srs)
Source: [IPCheck.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/IPCheck/IPCheck.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/IPCheck/sing-box/IPCheck.srs
```
