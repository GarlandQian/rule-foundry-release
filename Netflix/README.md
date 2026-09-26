# Netflix

Source config: [Netflix.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Netflix/Netflix.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Netflix | Netflix rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [netflix.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/netflix.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Netflix"
    type: select
    proxies: []
rules:
  - RULE-SET,Netflix_Domain,Netflix
  - RULE-SET,Netflix,Netflix,no-resolve
  - RULE-SET,Netflix_IP,Netflix,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Netflix_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/mihomo/Netflix_Domain.mrs }
  Netflix: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/mihomo/Netflix.yaml }
  Netflix_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/mihomo/Netflix_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/surge/Netflix.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/surge/Netflix.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/loon/Netflix.list,policy=<policy>,tag=Netflix,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/quantumult-x/Netflix.list, tag=Netflix, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/egern/Netflix.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/shadowrocket/Netflix.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Netflix",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/sing-box/Netflix.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Netflix",
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

#### Netflix.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/surge/Netflix.list
```

#### Netflix.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/surge/Netflix.domainset
```

### Loon

#### Netflix.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNetflix%2Floon%2FNetflix.list)


### Quantumult X

#### Netflix.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNetflix%2Fquantumult-x%2FNetflix.list%2C%20tag%3DNetflix%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Netflix.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNetflix%2Fegern%2FNetflix.yaml)


### Shadowrocket

#### Netflix.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/shadowrocket/Netflix.list
```

### sing-box

#### Netflix.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/sing-box/Netflix.srs
```

## Artifacts

### mrs(ipcidr)

#### Netflix_IP.mrs

GitHub: [Netflix_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/mihomo/Netflix_IP.mrs)
Text: [Netflix_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/mihomo/Netflix_IP.txt)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/mihomo/Netflix_IP.mrs
```

### mrs(domain)

#### Netflix_Domain.mrs

GitHub: [Netflix_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/mihomo/Netflix_Domain.mrs)
Text: [Netflix_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/mihomo/Netflix_Domain.txt)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/mihomo/Netflix_Domain.mrs
```

### yaml(remaining)

#### Netflix.yaml

GitHub: [Netflix.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/mihomo/Netflix.yaml)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/mihomo/Netflix.yaml
```

### Surge

#### Netflix.list

GitHub: [Netflix.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/surge/Netflix.list)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/surge/Netflix.list
```

#### Netflix.domainset

GitHub: [Netflix.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/surge/Netflix.domainset)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/surge/Netflix.domainset
```

### Loon

#### Netflix.list

GitHub: [Netflix.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/loon/Netflix.list)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/loon/Netflix.list
```

### Quantumult X

#### Netflix.list

GitHub: [Netflix.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/quantumult-x/Netflix.list)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/quantumult-x/Netflix.list
```

### Egern

#### Netflix.yaml

GitHub: [Netflix.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/egern/Netflix.yaml)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/egern/Netflix.yaml
```

### Shadowrocket

#### Netflix.list

GitHub: [Netflix.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/shadowrocket/Netflix.list)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/shadowrocket/Netflix.list
```

### sing-box

#### Netflix.json

GitHub: [Netflix.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/sing-box/Netflix.json)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/sing-box/Netflix.json
```

#### Netflix.srs

GitHub: [Netflix.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/sing-box/Netflix.srs)
Source: [Netflix.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Netflix/Netflix.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Netflix/sing-box/Netflix.srs
```
