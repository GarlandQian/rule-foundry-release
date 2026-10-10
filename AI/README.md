# AI

Source config: [AI.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/AI/AI.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| MetaCubeX | Non-China AI geosite domains from MetaCubeX/meta-rules-dat | true | http | domain | text | rules |  | [category-ai-!cn.list](https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geosite/category-ai-!cn.list) |  |  |
| iKeLee | Supplemental AI domains and Anthropic official service CIDRs | true | http | classical | yaml | rules | User-Agent: Loon/649 CFNetwork/1492.0.1 Darwin/23.3.0 | [AI.yaml](https://kelee.one/Tool/Clash/Rule/AI.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "AI"
    type: select
    proxies: []
rules:
  - RULE-SET,AI_Domain,AI
  - RULE-SET,AI_IP,AI,no-resolve
  - RULE-SET,AI,AI,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  AI_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_Domain.mrs }
  AI_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_IP.mrs }
  AI: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/loon/AI.list,policy=<policy>,tag=AI,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/quantumult-x/AI.list, tag=AI, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/egern/AI.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/shadowrocket/AI.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "AI",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "AI",
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

#### AI.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.list
```

#### AI.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.domainset
```

### Loon

#### AI.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAI%2Floon%2FAI.list)


### Quantumult X

#### AI.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAI%2Fquantumult-x%2FAI.list%2C%20tag%3DAI%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### AI.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAI%2Fegern%2FAI.yaml)


### Shadowrocket

#### AI.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/shadowrocket/AI.list
```

### sing-box

#### AI.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.srs
```

## Artifacts

### mrs(ipcidr)

#### AI_IP.mrs

GitHub: [AI_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_IP.mrs)
Text: [AI_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_IP.txt)
Source: [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_IP.mrs
```

### mrs(domain)

#### AI_Domain.mrs

GitHub: [AI_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_Domain.mrs)
Text: [AI_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI_Domain.txt)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI_Domain.mrs
```

### yaml(remaining)

#### AI.yaml

GitHub: [AI.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/mihomo/AI.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/mihomo/AI.yaml
```

### Surge

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/surge/AI.list)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.list
```

#### AI.domainset

GitHub: [AI.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/surge/AI.domainset)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/surge/AI.domainset
```

### Loon

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/loon/AI.list)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/loon/AI.list
```

### Quantumult X

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/quantumult-x/AI.list)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/quantumult-x/AI.list
```

### Egern

#### AI.yaml

GitHub: [AI.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/egern/AI.yaml)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/egern/AI.yaml
```

### Shadowrocket

#### AI.list

GitHub: [AI.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/shadowrocket/AI.list)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/shadowrocket/AI.list
```

### sing-box

#### AI.json

GitHub: [AI.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/sing-box/AI.json)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.json
```

#### AI.srs

GitHub: [AI.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/sing-box/AI.srs)
Sources: [MetaCubeX.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/MetaCubeX.original.list), [iKeLee.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AI/iKeLee.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AI/sing-box/AI.srs
```
