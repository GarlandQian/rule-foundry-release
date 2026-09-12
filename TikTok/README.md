# TikTok

Source config: [TikTok.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/TikTok/TikTok.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| TikTok | TikTok rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [tiktok.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/tiktok.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "TikTok"
    type: select
    proxies: []
rules:
  - RULE-SET,TikTok_Domain,TikTok
  - RULE-SET,TikTok,TikTok,no-resolve
  - RULE-SET,TikTok_IP,TikTok,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  TikTok_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/mihomo/TikTok_Domain.mrs }
  TikTok: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/mihomo/TikTok.yaml }
  TikTok_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/mihomo/TikTok_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/surge/TikTok.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/surge/TikTok.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/loon/TikTok.list,policy=<policy>,tag=TikTok,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/quantumult-x/TikTok.list, tag=TikTok, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/egern/TikTok.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/shadowrocket/TikTok.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "TikTok",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/sing-box/TikTok.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "TikTok",
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

#### TikTok.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/surge/TikTok.list
```

#### TikTok.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/surge/TikTok.domainset
```

### Loon

#### TikTok.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTikTok%2Floon%2FTikTok.list)


### Quantumult X

#### TikTok.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTikTok%2Fquantumult-x%2FTikTok.list%2C%20tag%3DTikTok%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### TikTok.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTikTok%2Fegern%2FTikTok.yaml)


### Shadowrocket

#### TikTok.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/shadowrocket/TikTok.list
```

### sing-box

#### TikTok.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/sing-box/TikTok.srs
```

## Artifacts

### mrs(ipcidr)

#### TikTok_IP.mrs

GitHub: [TikTok_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/mihomo/TikTok_IP.mrs)
Text: [TikTok_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/mihomo/TikTok_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/mihomo/TikTok_IP.mrs
```

### mrs(domain)

#### TikTok_Domain.mrs

GitHub: [TikTok_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/mihomo/TikTok_Domain.mrs)
Text: [TikTok_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/mihomo/TikTok_Domain.txt)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/mihomo/TikTok_Domain.mrs
```

### yaml(remaining)

#### TikTok.yaml

GitHub: [TikTok.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/mihomo/TikTok.yaml)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/mihomo/TikTok.yaml
```

### Surge

#### TikTok.list

GitHub: [TikTok.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/surge/TikTok.list)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/surge/TikTok.list
```

#### TikTok.domainset

GitHub: [TikTok.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/surge/TikTok.domainset)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/surge/TikTok.domainset
```

### Loon

#### TikTok.list

GitHub: [TikTok.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/loon/TikTok.list)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/loon/TikTok.list
```

### Quantumult X

#### TikTok.list

GitHub: [TikTok.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/quantumult-x/TikTok.list)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/quantumult-x/TikTok.list
```

### Egern

#### TikTok.yaml

GitHub: [TikTok.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/egern/TikTok.yaml)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/egern/TikTok.yaml
```

### Shadowrocket

#### TikTok.list

GitHub: [TikTok.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/shadowrocket/TikTok.list)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/shadowrocket/TikTok.list
```

### sing-box

#### TikTok.json

GitHub: [TikTok.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/sing-box/TikTok.json)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/sing-box/TikTok.json
```

#### TikTok.srs

GitHub: [TikTok.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/sing-box/TikTok.srs)
Source: [TikTok.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/TikTok/TikTok.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/TikTok/sing-box/TikTok.srs
```
