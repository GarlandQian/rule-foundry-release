# Lan

Source config: [Lan.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Lan/Lan.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Lan | Private network rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [private.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/private.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Lan"
    type: select
    proxies: []
rules:
  - RULE-SET,Lan_Domain,Lan
  - RULE-SET,Lan,Lan,no-resolve
  - RULE-SET,Lan_IP,Lan,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Lan_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/mihomo/Lan_Domain.mrs }
  Lan: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/mihomo/Lan.yaml }
  Lan_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/mihomo/Lan_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/surge/Lan.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/surge/Lan.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/loon/Lan.list,policy=<policy>,tag=Lan,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/quantumult-x/Lan.list, tag=Lan, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/egern/Lan.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/shadowrocket/Lan.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Lan",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/sing-box/Lan.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Lan",
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

#### Lan.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/surge/Lan.list
```

#### Lan.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/surge/Lan.domainset
```

### Loon

#### Lan.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLan%2Floon%2FLan.list)


### Quantumult X

#### Lan.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLan%2Fquantumult-x%2FLan.list%2C%20tag%3DLan%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Lan.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLan%2Fegern%2FLan.yaml)


### Shadowrocket

#### Lan.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/shadowrocket/Lan.list
```

### sing-box

#### Lan.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/sing-box/Lan.srs
```

## Artifacts

### mrs(ipcidr)

#### Lan_IP.mrs

GitHub: [Lan_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/mihomo/Lan_IP.mrs)
Text: [Lan_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/mihomo/Lan_IP.txt)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/mihomo/Lan_IP.mrs
```

### mrs(domain)

#### Lan_Domain.mrs

GitHub: [Lan_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/mihomo/Lan_Domain.mrs)
Text: [Lan_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/mihomo/Lan_Domain.txt)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/mihomo/Lan_Domain.mrs
```

### yaml(remaining)

#### Lan.yaml

GitHub: [Lan.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/mihomo/Lan.yaml)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/mihomo/Lan.yaml
```

### Surge

#### Lan.list

GitHub: [Lan.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/surge/Lan.list)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/surge/Lan.list
```

#### Lan.domainset

GitHub: [Lan.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/surge/Lan.domainset)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/surge/Lan.domainset
```

### Loon

#### Lan.list

GitHub: [Lan.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/loon/Lan.list)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/loon/Lan.list
```

### Quantumult X

#### Lan.list

GitHub: [Lan.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/quantumult-x/Lan.list)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/quantumult-x/Lan.list
```

### Egern

#### Lan.yaml

GitHub: [Lan.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/egern/Lan.yaml)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/egern/Lan.yaml
```

### Shadowrocket

#### Lan.list

GitHub: [Lan.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/shadowrocket/Lan.list)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/shadowrocket/Lan.list
```

### sing-box

#### Lan.json

GitHub: [Lan.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/sing-box/Lan.json)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/sing-box/Lan.json
```

#### Lan.srs

GitHub: [Lan.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/sing-box/Lan.srs)
Source: [Lan.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Lan/Lan.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Lan/sing-box/Lan.srs
```
