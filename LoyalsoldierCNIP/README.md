# LoyalsoldierCNIP

Source config: [LoyalsoldierCNIP.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/LoyalsoldierCNIP/LoyalsoldierCNIP.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| LoyalsoldierCNIP | China CIDR rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [cncidr.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/cncidr.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "LoyalsoldierCNIP"
    type: select
    proxies: []
rules:
  - RULE-SET,LoyalsoldierCNIP_IP,LoyalsoldierCNIP,no-resolve
  - RULE-SET,LoyalsoldierCNIP_Domain,LoyalsoldierCNIP # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,LoyalsoldierCNIP,LoyalsoldierCNIP,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  LoyalsoldierCNIP_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_IP.mrs }
  LoyalsoldierCNIP_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  LoyalsoldierCNIP: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/surge/LoyalsoldierCNIP.list,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/loon/LoyalsoldierCNIP.list,policy=<policy>,tag=LoyalsoldierCNIP,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/quantumult-x/LoyalsoldierCNIP.list, tag=LoyalsoldierCNIP, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/egern/LoyalsoldierCNIP.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/shadowrocket/LoyalsoldierCNIP.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "LoyalsoldierCNIP",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/sing-box/LoyalsoldierCNIP.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "LoyalsoldierCNIP",
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

#### LoyalsoldierCNIP.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/surge/LoyalsoldierCNIP.list
```

### Loon

#### LoyalsoldierCNIP.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierCNIP%2Floon%2FLoyalsoldierCNIP.list)


### Quantumult X

#### LoyalsoldierCNIP.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierCNIP%2Fquantumult-x%2FLoyalsoldierCNIP.list%2C%20tag%3DLoyalsoldierCNIP%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### LoyalsoldierCNIP.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierCNIP%2Fegern%2FLoyalsoldierCNIP.yaml)


### Shadowrocket

#### LoyalsoldierCNIP.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/shadowrocket/LoyalsoldierCNIP.list
```

### sing-box

#### LoyalsoldierCNIP.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/sing-box/LoyalsoldierCNIP.srs
```

## Artifacts

### mrs(ipcidr)

#### LoyalsoldierCNIP_IP.mrs

GitHub: [LoyalsoldierCNIP_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_IP.mrs)
Text: [LoyalsoldierCNIP_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_IP.txt)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_IP.mrs
```

### mrs(domain)

#### LoyalsoldierCNIP_Domain.mrs

GitHub: [LoyalsoldierCNIP_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_Domain.mrs)
Text: [LoyalsoldierCNIP_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP_Domain.mrs
```

### yaml(remaining)

#### LoyalsoldierCNIP.yaml

GitHub: [LoyalsoldierCNIP.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/mihomo/LoyalsoldierCNIP.yaml
```

### Surge

#### LoyalsoldierCNIP.list

GitHub: [LoyalsoldierCNIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/surge/LoyalsoldierCNIP.list)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/surge/LoyalsoldierCNIP.list
```

### Loon

#### LoyalsoldierCNIP.list

GitHub: [LoyalsoldierCNIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/loon/LoyalsoldierCNIP.list)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/loon/LoyalsoldierCNIP.list
```

### Quantumult X

#### LoyalsoldierCNIP.list

GitHub: [LoyalsoldierCNIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/quantumult-x/LoyalsoldierCNIP.list)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/quantumult-x/LoyalsoldierCNIP.list
```

### Egern

#### LoyalsoldierCNIP.yaml

GitHub: [LoyalsoldierCNIP.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/egern/LoyalsoldierCNIP.yaml)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/egern/LoyalsoldierCNIP.yaml
```

### Shadowrocket

#### LoyalsoldierCNIP.list

GitHub: [LoyalsoldierCNIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/shadowrocket/LoyalsoldierCNIP.list)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/shadowrocket/LoyalsoldierCNIP.list
```

### sing-box

#### LoyalsoldierCNIP.json

GitHub: [LoyalsoldierCNIP.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/sing-box/LoyalsoldierCNIP.json)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/sing-box/LoyalsoldierCNIP.json
```

#### LoyalsoldierCNIP.srs

GitHub: [LoyalsoldierCNIP.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/sing-box/LoyalsoldierCNIP.srs)
Source: [LoyalsoldierCNIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierCNIP/LoyalsoldierCNIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierCNIP/sing-box/LoyalsoldierCNIP.srs
```
