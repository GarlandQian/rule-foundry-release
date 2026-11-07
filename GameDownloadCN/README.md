# GameDownloadCN

Source config: [GameDownloadCN.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/GameDownloadCN/GameDownloadCN.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| GameDownloadCN | China game platform downloads from Yuu518/Yuu-rules | true | http | classical | text | rules |  | [category-game-platforms-download@cn.list](https://raw.githubusercontent.com/Yuu518/Yuu-rules/rule-set/mihomo/geosite/classical/category-game-platforms-download%40cn.list) |  |  |
| GameDownloadCN_Local | Preserve the legacy download domains missing from the Yuu set | true | inline | classical | yaml | rules |  |  |  | [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml) |

## Mihomo Config

```yaml
proxy-groups:
  - name: "GameDownloadCN"
    type: select
    proxies: []
rules:
  - RULE-SET,GameDownloadCN_Domain,GameDownloadCN
  - RULE-SET,GameDownloadCN,GameDownloadCN,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,GameDownloadCN_IP,GameDownloadCN,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  GameDownloadCN_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/mihomo/GameDownloadCN_Domain.mrs }
  GameDownloadCN: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/mihomo/GameDownloadCN.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  GameDownloadCN_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/mihomo/GameDownloadCN_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/surge/GameDownloadCN.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/surge/GameDownloadCN.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/loon/GameDownloadCN.list,policy=<policy>,tag=GameDownloadCN,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/quantumult-x/GameDownloadCN.list, tag=GameDownloadCN, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/egern/GameDownloadCN.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/shadowrocket/GameDownloadCN.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "GameDownloadCN",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/sing-box/GameDownloadCN.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "GameDownloadCN",
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

#### GameDownloadCN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/surge/GameDownloadCN.list
```

#### GameDownloadCN.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/surge/GameDownloadCN.domainset
```

### Loon

#### GameDownloadCN.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGameDownloadCN%2Floon%2FGameDownloadCN.list)


### Quantumult X

#### GameDownloadCN.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGameDownloadCN%2Fquantumult-x%2FGameDownloadCN.list%2C%20tag%3DGameDownloadCN%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### GameDownloadCN.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGameDownloadCN%2Fegern%2FGameDownloadCN.yaml)


### Shadowrocket

#### GameDownloadCN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/shadowrocket/GameDownloadCN.list
```

### sing-box

#### GameDownloadCN.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/sing-box/GameDownloadCN.srs
```

## Artifacts

### mrs(ipcidr)

#### GameDownloadCN_IP.mrs

GitHub: [GameDownloadCN_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/mihomo/GameDownloadCN_IP.mrs)
Text: [GameDownloadCN_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/mihomo/GameDownloadCN_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/mihomo/GameDownloadCN_IP.mrs
```

### mrs(domain)

#### GameDownloadCN_Domain.mrs

GitHub: [GameDownloadCN_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/mihomo/GameDownloadCN_Domain.mrs)
Text: [GameDownloadCN_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/mihomo/GameDownloadCN_Domain.txt)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/mihomo/GameDownloadCN_Domain.mrs
```

### yaml(remaining)

#### GameDownloadCN.yaml

GitHub: [GameDownloadCN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/mihomo/GameDownloadCN.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/mihomo/GameDownloadCN.yaml
```

### Surge

#### GameDownloadCN.list

GitHub: [GameDownloadCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/surge/GameDownloadCN.list)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/surge/GameDownloadCN.list
```

#### GameDownloadCN.domainset

GitHub: [GameDownloadCN.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/surge/GameDownloadCN.domainset)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/surge/GameDownloadCN.domainset
```

### Loon

#### GameDownloadCN.list

GitHub: [GameDownloadCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/loon/GameDownloadCN.list)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/loon/GameDownloadCN.list
```

### Quantumult X

#### GameDownloadCN.list

GitHub: [GameDownloadCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/quantumult-x/GameDownloadCN.list)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/quantumult-x/GameDownloadCN.list
```

### Egern

#### GameDownloadCN.yaml

GitHub: [GameDownloadCN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/egern/GameDownloadCN.yaml)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/egern/GameDownloadCN.yaml
```

### Shadowrocket

#### GameDownloadCN.list

GitHub: [GameDownloadCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/shadowrocket/GameDownloadCN.list)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/shadowrocket/GameDownloadCN.list
```

### sing-box

#### GameDownloadCN.json

GitHub: [GameDownloadCN.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/sing-box/GameDownloadCN.json)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/sing-box/GameDownloadCN.json
```

#### GameDownloadCN.srs

GitHub: [GameDownloadCN.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/sing-box/GameDownloadCN.srs)
Sources: [GameDownloadCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN.original.list), [GameDownloadCN_Local.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownloadCN/GameDownloadCN_Local.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownloadCN/sing-box/GameDownloadCN.srs
```
