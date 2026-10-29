# PrimeVideo

Source config: [PrimeVideo.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/PrimeVideo/PrimeVideo.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| PrimeVideo | Prime Video rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [primevideo.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/primevideo.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "PrimeVideo"
    type: select
    proxies: []
rules:
  - RULE-SET,PrimeVideo_Domain,PrimeVideo
  - RULE-SET,PrimeVideo,PrimeVideo,no-resolve
  - RULE-SET,PrimeVideo_IP,PrimeVideo,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  PrimeVideo_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/mihomo/PrimeVideo_Domain.mrs }
  PrimeVideo: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/mihomo/PrimeVideo.yaml }
  PrimeVideo_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/mihomo/PrimeVideo_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/surge/PrimeVideo.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/surge/PrimeVideo.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/loon/PrimeVideo.list,policy=<policy>,tag=PrimeVideo,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/quantumult-x/PrimeVideo.list, tag=PrimeVideo, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/egern/PrimeVideo.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/shadowrocket/PrimeVideo.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "PrimeVideo",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/sing-box/PrimeVideo.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "PrimeVideo",
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

#### PrimeVideo.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/surge/PrimeVideo.list
```

#### PrimeVideo.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/surge/PrimeVideo.domainset
```

### Loon

#### PrimeVideo.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPrimeVideo%2Floon%2FPrimeVideo.list)


### Quantumult X

#### PrimeVideo.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPrimeVideo%2Fquantumult-x%2FPrimeVideo.list%2C%20tag%3DPrimeVideo%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### PrimeVideo.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPrimeVideo%2Fegern%2FPrimeVideo.yaml)


### Shadowrocket

#### PrimeVideo.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/shadowrocket/PrimeVideo.list
```

### sing-box

#### PrimeVideo.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/sing-box/PrimeVideo.srs
```

## Artifacts

### mrs(ipcidr)

#### PrimeVideo_IP.mrs

GitHub: [PrimeVideo_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/mihomo/PrimeVideo_IP.mrs)
Text: [PrimeVideo_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/mihomo/PrimeVideo_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/mihomo/PrimeVideo_IP.mrs
```

### mrs(domain)

#### PrimeVideo_Domain.mrs

GitHub: [PrimeVideo_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/mihomo/PrimeVideo_Domain.mrs)
Text: [PrimeVideo_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/mihomo/PrimeVideo_Domain.txt)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/mihomo/PrimeVideo_Domain.mrs
```

### yaml(remaining)

#### PrimeVideo.yaml

GitHub: [PrimeVideo.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/mihomo/PrimeVideo.yaml)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/mihomo/PrimeVideo.yaml
```

### Surge

#### PrimeVideo.list

GitHub: [PrimeVideo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/surge/PrimeVideo.list)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/surge/PrimeVideo.list
```

#### PrimeVideo.domainset

GitHub: [PrimeVideo.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/surge/PrimeVideo.domainset)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/surge/PrimeVideo.domainset
```

### Loon

#### PrimeVideo.list

GitHub: [PrimeVideo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/loon/PrimeVideo.list)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/loon/PrimeVideo.list
```

### Quantumult X

#### PrimeVideo.list

GitHub: [PrimeVideo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/quantumult-x/PrimeVideo.list)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/quantumult-x/PrimeVideo.list
```

### Egern

#### PrimeVideo.yaml

GitHub: [PrimeVideo.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/egern/PrimeVideo.yaml)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/egern/PrimeVideo.yaml
```

### Shadowrocket

#### PrimeVideo.list

GitHub: [PrimeVideo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/shadowrocket/PrimeVideo.list)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/shadowrocket/PrimeVideo.list
```

### sing-box

#### PrimeVideo.json

GitHub: [PrimeVideo.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/sing-box/PrimeVideo.json)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/sing-box/PrimeVideo.json
```

#### PrimeVideo.srs

GitHub: [PrimeVideo.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/sing-box/PrimeVideo.srs)
Source: [PrimeVideo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PrimeVideo/PrimeVideo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PrimeVideo/sing-box/PrimeVideo.srs
```
