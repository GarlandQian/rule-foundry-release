# GameDownload

Source config: [GameDownload.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/GameDownload/GameDownload.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| GameDownload | GameDownload | true | http | classical | yaml | rules |  | [GameDownload.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Game/GameDownload/GameDownload.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "GameDownload"
    type: select
    proxies: []
rules:
  - RULE-SET,GameDownload_Domain,GameDownload
  - RULE-SET,GameDownload,GameDownload,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,GameDownload_IP,GameDownload,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  GameDownload_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/mihomo/GameDownload_Domain.mrs }
  GameDownload: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/mihomo/GameDownload.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  GameDownload_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/mihomo/GameDownload_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/surge/GameDownload.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/surge/GameDownload.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/loon/GameDownload.list,policy=<policy>,tag=GameDownload,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/quantumult-x/GameDownload.list, tag=GameDownload, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/egern/GameDownload.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/shadowrocket/GameDownload.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "GameDownload",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/sing-box/GameDownload.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "GameDownload",
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

#### GameDownload.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/surge/GameDownload.list
```

#### GameDownload.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/surge/GameDownload.domainset
```

### Loon

#### GameDownload.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGameDownload%2Floon%2FGameDownload.list)


### Quantumult X

#### GameDownload.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGameDownload%2Fquantumult-x%2FGameDownload.list%2C%20tag%3DGameDownload%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### GameDownload.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGameDownload%2Fegern%2FGameDownload.yaml)


### Shadowrocket

#### GameDownload.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/shadowrocket/GameDownload.list
```

### sing-box

#### GameDownload.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/sing-box/GameDownload.srs
```

## Artifacts

### mrs(ipcidr)

#### GameDownload_IP.mrs

GitHub: [GameDownload_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/mihomo/GameDownload_IP.mrs)
Text: [GameDownload_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/mihomo/GameDownload_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/mihomo/GameDownload_IP.mrs
```

### mrs(domain)

#### GameDownload_Domain.mrs

GitHub: [GameDownload_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/mihomo/GameDownload_Domain.mrs)
Text: [GameDownload_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/mihomo/GameDownload_Domain.txt)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/mihomo/GameDownload_Domain.mrs
```

### yaml(remaining)

#### GameDownload.yaml

GitHub: [GameDownload.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/mihomo/GameDownload.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/mihomo/GameDownload.yaml
```

### Surge

#### GameDownload.list

GitHub: [GameDownload.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/surge/GameDownload.list)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/surge/GameDownload.list
```

#### GameDownload.domainset

GitHub: [GameDownload.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/surge/GameDownload.domainset)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/surge/GameDownload.domainset
```

### Loon

#### GameDownload.list

GitHub: [GameDownload.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/loon/GameDownload.list)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/loon/GameDownload.list
```

### Quantumult X

#### GameDownload.list

GitHub: [GameDownload.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/quantumult-x/GameDownload.list)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/quantumult-x/GameDownload.list
```

### Egern

#### GameDownload.yaml

GitHub: [GameDownload.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/egern/GameDownload.yaml)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/egern/GameDownload.yaml
```

### Shadowrocket

#### GameDownload.list

GitHub: [GameDownload.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/shadowrocket/GameDownload.list)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/shadowrocket/GameDownload.list
```

### sing-box

#### GameDownload.json

GitHub: [GameDownload.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/sing-box/GameDownload.json)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/sing-box/GameDownload.json
```

#### GameDownload.srs

GitHub: [GameDownload.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/sing-box/GameDownload.srs)
Source: [GameDownload.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GameDownload/GameDownload.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GameDownload/sing-box/GameDownload.srs
```
