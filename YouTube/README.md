# YouTube

Source config: [YouTube.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/YouTube/YouTube.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| YouTube | YouTube rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [youtube.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/youtube.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "YouTube"
    type: select
    proxies: []
rules:
  - RULE-SET,YouTube_Domain,YouTube
  - RULE-SET,YouTube,YouTube,no-resolve
  - RULE-SET,YouTube_IP,YouTube,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  YouTube_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/mihomo/YouTube_Domain.mrs }
  YouTube: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/mihomo/YouTube.yaml }
  YouTube_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/mihomo/YouTube_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/surge/YouTube.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/surge/YouTube.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/loon/YouTube.list,policy=<policy>,tag=YouTube,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/quantumult-x/YouTube.list, tag=YouTube, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/egern/YouTube.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/shadowrocket/YouTube.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "YouTube",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/sing-box/YouTube.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "YouTube",
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

#### YouTube.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/surge/YouTube.list
```

#### YouTube.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/surge/YouTube.domainset
```

### Loon

#### YouTube.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FYouTube%2Floon%2FYouTube.list)


### Quantumult X

#### YouTube.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FYouTube%2Fquantumult-x%2FYouTube.list%2C%20tag%3DYouTube%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### YouTube.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FYouTube%2Fegern%2FYouTube.yaml)


### Shadowrocket

#### YouTube.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/shadowrocket/YouTube.list
```

### sing-box

#### YouTube.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/sing-box/YouTube.srs
```

## Artifacts

### mrs(ipcidr)

#### YouTube_IP.mrs

GitHub: [YouTube_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/mihomo/YouTube_IP.mrs)
Text: [YouTube_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/mihomo/YouTube_IP.txt)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/mihomo/YouTube_IP.mrs
```

### mrs(domain)

#### YouTube_Domain.mrs

GitHub: [YouTube_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/mihomo/YouTube_Domain.mrs)
Text: [YouTube_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/mihomo/YouTube_Domain.txt)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/mihomo/YouTube_Domain.mrs
```

### yaml(remaining)

#### YouTube.yaml

GitHub: [YouTube.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/mihomo/YouTube.yaml)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/mihomo/YouTube.yaml
```

### Surge

#### YouTube.list

GitHub: [YouTube.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/surge/YouTube.list)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/surge/YouTube.list
```

#### YouTube.domainset

GitHub: [YouTube.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/surge/YouTube.domainset)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/surge/YouTube.domainset
```

### Loon

#### YouTube.list

GitHub: [YouTube.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/loon/YouTube.list)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/loon/YouTube.list
```

### Quantumult X

#### YouTube.list

GitHub: [YouTube.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/quantumult-x/YouTube.list)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/quantumult-x/YouTube.list
```

### Egern

#### YouTube.yaml

GitHub: [YouTube.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/egern/YouTube.yaml)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/egern/YouTube.yaml
```

### Shadowrocket

#### YouTube.list

GitHub: [YouTube.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/shadowrocket/YouTube.list)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/shadowrocket/YouTube.list
```

### sing-box

#### YouTube.json

GitHub: [YouTube.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/sing-box/YouTube.json)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/sing-box/YouTube.json
```

#### YouTube.srs

GitHub: [YouTube.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/sing-box/YouTube.srs)
Source: [YouTube.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/YouTube/YouTube.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/YouTube/sing-box/YouTube.srs
```
