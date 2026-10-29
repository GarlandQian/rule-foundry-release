# adblock

Source config: [adblock.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/adblock/adblock.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| adblock | Ad-blocking rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [adrules.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/adrules.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "adblock"
    type: select
    proxies: []
rules:
  - RULE-SET,adblock_Domain,adblock
  - RULE-SET,adblock,adblock,no-resolve
  - RULE-SET,adblock_IP,adblock,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  adblock_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/mihomo/adblock_Domain.mrs }
  adblock: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/mihomo/adblock.yaml }
  adblock_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/mihomo/adblock_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/surge/adblock.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/surge/adblock.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/loon/adblock.list,policy=<policy>,tag=adblock,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/quantumult-x/adblock.list, tag=adblock, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/egern/adblock.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/shadowrocket/adblock.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "adblock",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/sing-box/adblock.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "adblock",
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

#### adblock.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/surge/adblock.list
```

#### adblock.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/surge/adblock.domainset
```

### Loon

#### adblock.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2Fadblock%2Floon%2Fadblock.list)


### Quantumult X

#### adblock.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2Fadblock%2Fquantumult-x%2Fadblock.list%2C%20tag%3Dadblock%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### adblock.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2Fadblock%2Fegern%2Fadblock.yaml)


### Shadowrocket

#### adblock.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/shadowrocket/adblock.list
```

### sing-box

#### adblock.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/sing-box/adblock.srs
```

## Artifacts

### mrs(ipcidr)

#### adblock_IP.mrs

GitHub: [adblock_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/mihomo/adblock_IP.mrs)
Text: [adblock_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/mihomo/adblock_IP.txt)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/mihomo/adblock_IP.mrs
```

### mrs(domain)

#### adblock_Domain.mrs

GitHub: [adblock_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/mihomo/adblock_Domain.mrs)
Text: [adblock_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/mihomo/adblock_Domain.txt)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/mihomo/adblock_Domain.mrs
```

### yaml(remaining)

#### adblock.yaml

GitHub: [adblock.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/mihomo/adblock.yaml)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/mihomo/adblock.yaml
```

### Surge

#### adblock.list

GitHub: [adblock.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/surge/adblock.list)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/surge/adblock.list
```

#### adblock.domainset

GitHub: [adblock.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/surge/adblock.domainset)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/surge/adblock.domainset
```

### Loon

#### adblock.list

GitHub: [adblock.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/loon/adblock.list)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/loon/adblock.list
```

### Quantumult X

#### adblock.list

GitHub: [adblock.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/quantumult-x/adblock.list)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/quantumult-x/adblock.list
```

### Egern

#### adblock.yaml

GitHub: [adblock.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/egern/adblock.yaml)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/egern/adblock.yaml
```

### Shadowrocket

#### adblock.list

GitHub: [adblock.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/shadowrocket/adblock.list)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/shadowrocket/adblock.list
```

### sing-box

#### adblock.json

GitHub: [adblock.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/sing-box/adblock.json)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/sing-box/adblock.json
```

#### adblock.srs

GitHub: [adblock.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/sing-box/adblock.srs)
Source: [adblock.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/adblock/adblock.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/adblock/sing-box/adblock.srs
```
