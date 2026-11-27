# PublicTracker

Source config: [PublicTracker.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/PublicTracker/PublicTracker.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| PublicTracker | Public BitTorrent tracker domains from Yuu518/Yuu-rules | true | http | classical | text | rules |  | [category-public-tracker.list](https://raw.githubusercontent.com/Yuu518/Yuu-rules/rule-set/surge/geosite/category-public-tracker.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "PublicTracker"
    type: select
    proxies: []
rules:
  - RULE-SET,PublicTracker_Domain,PublicTracker
  - RULE-SET,PublicTracker,PublicTracker,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,PublicTracker_IP,PublicTracker,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  PublicTracker_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/mihomo/PublicTracker_Domain.mrs }
  PublicTracker: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/mihomo/PublicTracker.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  PublicTracker_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/mihomo/PublicTracker_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/surge/PublicTracker.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/surge/PublicTracker.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/loon/PublicTracker.list,policy=<policy>,tag=PublicTracker,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/quantumult-x/PublicTracker.list, tag=PublicTracker, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/egern/PublicTracker.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/shadowrocket/PublicTracker.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "PublicTracker",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/sing-box/PublicTracker.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "PublicTracker",
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

#### PublicTracker.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/surge/PublicTracker.list
```

#### PublicTracker.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/surge/PublicTracker.domainset
```

### Loon

#### PublicTracker.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPublicTracker%2Floon%2FPublicTracker.list)


### Quantumult X

#### PublicTracker.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPublicTracker%2Fquantumult-x%2FPublicTracker.list%2C%20tag%3DPublicTracker%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### PublicTracker.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPublicTracker%2Fegern%2FPublicTracker.yaml)


### Shadowrocket

#### PublicTracker.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/shadowrocket/PublicTracker.list
```

### sing-box

#### PublicTracker.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/sing-box/PublicTracker.srs
```

## Artifacts

### mrs(ipcidr)

#### PublicTracker_IP.mrs

GitHub: [PublicTracker_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/mihomo/PublicTracker_IP.mrs)
Text: [PublicTracker_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/mihomo/PublicTracker_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/mihomo/PublicTracker_IP.mrs
```

### mrs(domain)

#### PublicTracker_Domain.mrs

GitHub: [PublicTracker_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/mihomo/PublicTracker_Domain.mrs)
Text: [PublicTracker_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/mihomo/PublicTracker_Domain.txt)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/mihomo/PublicTracker_Domain.mrs
```

### yaml(remaining)

#### PublicTracker.yaml

GitHub: [PublicTracker.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/mihomo/PublicTracker.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/mihomo/PublicTracker.yaml
```

### Surge

#### PublicTracker.list

GitHub: [PublicTracker.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/surge/PublicTracker.list)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/surge/PublicTracker.list
```

#### PublicTracker.domainset

GitHub: [PublicTracker.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/surge/PublicTracker.domainset)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/surge/PublicTracker.domainset
```

### Loon

#### PublicTracker.list

GitHub: [PublicTracker.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/loon/PublicTracker.list)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/loon/PublicTracker.list
```

### Quantumult X

#### PublicTracker.list

GitHub: [PublicTracker.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/quantumult-x/PublicTracker.list)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/quantumult-x/PublicTracker.list
```

### Egern

#### PublicTracker.yaml

GitHub: [PublicTracker.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/egern/PublicTracker.yaml)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/egern/PublicTracker.yaml
```

### Shadowrocket

#### PublicTracker.list

GitHub: [PublicTracker.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/shadowrocket/PublicTracker.list)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/shadowrocket/PublicTracker.list
```

### sing-box

#### PublicTracker.json

GitHub: [PublicTracker.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/sing-box/PublicTracker.json)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/sing-box/PublicTracker.json
```

#### PublicTracker.srs

GitHub: [PublicTracker.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/sing-box/PublicTracker.srs)
Source: [PublicTracker.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PublicTracker/PublicTracker.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PublicTracker/sing-box/PublicTracker.srs
```
