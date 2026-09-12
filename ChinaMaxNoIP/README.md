# ChinaMaxNoIP

Source config: [ChinaMaxNoIP.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/ChinaMaxNoIP/ChinaMaxNoIP.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| ChinaMaxNoIP | China domain rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [cn.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/cn.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "ChinaMaxNoIP"
    type: select
    proxies: []
rules:
  - RULE-SET,ChinaMaxNoIP_Domain,ChinaMaxNoIP
  - RULE-SET,ChinaMaxNoIP,ChinaMaxNoIP,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,ChinaMaxNoIP_IP,ChinaMaxNoIP,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  ChinaMaxNoIP_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_Domain.mrs }
  ChinaMaxNoIP: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  ChinaMaxNoIP_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/loon/ChinaMaxNoIP.list,policy=<policy>,tag=ChinaMaxNoIP,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/quantumult-x/ChinaMaxNoIP.list, tag=ChinaMaxNoIP, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/egern/ChinaMaxNoIP.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/shadowrocket/ChinaMaxNoIP.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "ChinaMaxNoIP",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/sing-box/ChinaMaxNoIP.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "ChinaMaxNoIP",
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

#### ChinaMaxNoIP.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.list
```

#### ChinaMaxNoIP.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.domainset
```

### Loon

#### ChinaMaxNoIP.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FChinaMaxNoIP%2Floon%2FChinaMaxNoIP.list)


### Quantumult X

#### ChinaMaxNoIP.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FChinaMaxNoIP%2Fquantumult-x%2FChinaMaxNoIP.list%2C%20tag%3DChinaMaxNoIP%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### ChinaMaxNoIP.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FChinaMaxNoIP%2Fegern%2FChinaMaxNoIP.yaml)


### Shadowrocket

#### ChinaMaxNoIP.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/shadowrocket/ChinaMaxNoIP.list
```

### sing-box

#### ChinaMaxNoIP.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/sing-box/ChinaMaxNoIP.srs
```

## Artifacts

### mrs(ipcidr)

#### ChinaMaxNoIP_IP.mrs

GitHub: [ChinaMaxNoIP_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_IP.mrs)
Text: [ChinaMaxNoIP_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_IP.mrs
```

### mrs(domain)

#### ChinaMaxNoIP_Domain.mrs

GitHub: [ChinaMaxNoIP_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_Domain.mrs)
Text: [ChinaMaxNoIP_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_Domain.txt)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP_Domain.mrs
```

### yaml(remaining)

#### ChinaMaxNoIP.yaml

GitHub: [ChinaMaxNoIP.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/mihomo/ChinaMaxNoIP.yaml
```

### Surge

#### ChinaMaxNoIP.list

GitHub: [ChinaMaxNoIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.list)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.list
```

#### ChinaMaxNoIP.domainset

GitHub: [ChinaMaxNoIP.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.domainset)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/surge/ChinaMaxNoIP.domainset
```

### Loon

#### ChinaMaxNoIP.list

GitHub: [ChinaMaxNoIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/loon/ChinaMaxNoIP.list)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/loon/ChinaMaxNoIP.list
```

### Quantumult X

#### ChinaMaxNoIP.list

GitHub: [ChinaMaxNoIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/quantumult-x/ChinaMaxNoIP.list)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/quantumult-x/ChinaMaxNoIP.list
```

### Egern

#### ChinaMaxNoIP.yaml

GitHub: [ChinaMaxNoIP.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/egern/ChinaMaxNoIP.yaml)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/egern/ChinaMaxNoIP.yaml
```

### Shadowrocket

#### ChinaMaxNoIP.list

GitHub: [ChinaMaxNoIP.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/shadowrocket/ChinaMaxNoIP.list)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/shadowrocket/ChinaMaxNoIP.list
```

### sing-box

#### ChinaMaxNoIP.json

GitHub: [ChinaMaxNoIP.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/sing-box/ChinaMaxNoIP.json)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/sing-box/ChinaMaxNoIP.json
```

#### ChinaMaxNoIP.srs

GitHub: [ChinaMaxNoIP.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/sing-box/ChinaMaxNoIP.srs)
Source: [ChinaMaxNoIP.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMaxNoIP/ChinaMaxNoIP.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMaxNoIP/sing-box/ChinaMaxNoIP.srs
```
