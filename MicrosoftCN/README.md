# MicrosoftCN

Source config: [MicrosoftCN.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/MicrosoftCN/MicrosoftCN.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| MicrosoftCN | Microsoft China rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [microsoft-cn.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/microsoft-cn.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "MicrosoftCN"
    type: select
    proxies: []
rules:
  - RULE-SET,MicrosoftCN_Domain,MicrosoftCN
  - RULE-SET,MicrosoftCN,MicrosoftCN,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,MicrosoftCN_IP,MicrosoftCN,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  MicrosoftCN_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/mihomo/MicrosoftCN_Domain.mrs }
  MicrosoftCN: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/mihomo/MicrosoftCN.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  MicrosoftCN_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/mihomo/MicrosoftCN_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/surge/MicrosoftCN.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/surge/MicrosoftCN.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/loon/MicrosoftCN.list,policy=<policy>,tag=MicrosoftCN,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/quantumult-x/MicrosoftCN.list, tag=MicrosoftCN, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/egern/MicrosoftCN.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/shadowrocket/MicrosoftCN.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "MicrosoftCN",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/sing-box/MicrosoftCN.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "MicrosoftCN",
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

#### MicrosoftCN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/surge/MicrosoftCN.list
```

#### MicrosoftCN.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/surge/MicrosoftCN.domainset
```

### Loon

#### MicrosoftCN.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FMicrosoftCN%2Floon%2FMicrosoftCN.list)


### Quantumult X

#### MicrosoftCN.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FMicrosoftCN%2Fquantumult-x%2FMicrosoftCN.list%2C%20tag%3DMicrosoftCN%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### MicrosoftCN.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FMicrosoftCN%2Fegern%2FMicrosoftCN.yaml)


### Shadowrocket

#### MicrosoftCN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/shadowrocket/MicrosoftCN.list
```

### sing-box

#### MicrosoftCN.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/sing-box/MicrosoftCN.srs
```

## Artifacts

### mrs(ipcidr)

#### MicrosoftCN_IP.mrs

GitHub: [MicrosoftCN_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/mihomo/MicrosoftCN_IP.mrs)
Text: [MicrosoftCN_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/mihomo/MicrosoftCN_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/mihomo/MicrosoftCN_IP.mrs
```

### mrs(domain)

#### MicrosoftCN_Domain.mrs

GitHub: [MicrosoftCN_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/mihomo/MicrosoftCN_Domain.mrs)
Text: [MicrosoftCN_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/mihomo/MicrosoftCN_Domain.txt)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/mihomo/MicrosoftCN_Domain.mrs
```

### yaml(remaining)

#### MicrosoftCN.yaml

GitHub: [MicrosoftCN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/mihomo/MicrosoftCN.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/mihomo/MicrosoftCN.yaml
```

### Surge

#### MicrosoftCN.list

GitHub: [MicrosoftCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/surge/MicrosoftCN.list)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/surge/MicrosoftCN.list
```

#### MicrosoftCN.domainset

GitHub: [MicrosoftCN.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/surge/MicrosoftCN.domainset)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/surge/MicrosoftCN.domainset
```

### Loon

#### MicrosoftCN.list

GitHub: [MicrosoftCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/loon/MicrosoftCN.list)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/loon/MicrosoftCN.list
```

### Quantumult X

#### MicrosoftCN.list

GitHub: [MicrosoftCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/quantumult-x/MicrosoftCN.list)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/quantumult-x/MicrosoftCN.list
```

### Egern

#### MicrosoftCN.yaml

GitHub: [MicrosoftCN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/egern/MicrosoftCN.yaml)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/egern/MicrosoftCN.yaml
```

### Shadowrocket

#### MicrosoftCN.list

GitHub: [MicrosoftCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/shadowrocket/MicrosoftCN.list)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/shadowrocket/MicrosoftCN.list
```

### sing-box

#### MicrosoftCN.json

GitHub: [MicrosoftCN.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/sing-box/MicrosoftCN.json)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/sing-box/MicrosoftCN.json
```

#### MicrosoftCN.srs

GitHub: [MicrosoftCN.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/sing-box/MicrosoftCN.srs)
Source: [MicrosoftCN.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/MicrosoftCN/MicrosoftCN.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/MicrosoftCN/sing-box/MicrosoftCN.srs
```
