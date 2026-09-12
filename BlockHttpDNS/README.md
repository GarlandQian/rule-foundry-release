# BlockHttpDNS

Source config: [BlockHttpDNS.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/BlockHttpDNS/BlockHttpDNS.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| BlockHttpDNS | HTTPDNS blocking rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [httpdns.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/httpdns.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "BlockHttpDNS"
    type: select
    proxies: []
rules:
  - RULE-SET,BlockHttpDNS_Domain,BlockHttpDNS
  - RULE-SET,BlockHttpDNS_IP,BlockHttpDNS,no-resolve
  - RULE-SET,BlockHttpDNS,BlockHttpDNS,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  BlockHttpDNS_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/mihomo/BlockHttpDNS_Domain.mrs }
  BlockHttpDNS_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/mihomo/BlockHttpDNS_IP.mrs }
  BlockHttpDNS: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/mihomo/BlockHttpDNS.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/surge/BlockHttpDNS.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/surge/BlockHttpDNS.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/loon/BlockHttpDNS.list,policy=<policy>,tag=BlockHttpDNS,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/quantumult-x/BlockHttpDNS.list, tag=BlockHttpDNS, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/egern/BlockHttpDNS.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/shadowrocket/BlockHttpDNS.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "BlockHttpDNS",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/sing-box/BlockHttpDNS.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "BlockHttpDNS",
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

#### BlockHttpDNS.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/surge/BlockHttpDNS.list
```

#### BlockHttpDNS.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/surge/BlockHttpDNS.domainset
```

### Loon

#### BlockHttpDNS.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBlockHttpDNS%2Floon%2FBlockHttpDNS.list)


### Quantumult X

#### BlockHttpDNS.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBlockHttpDNS%2Fquantumult-x%2FBlockHttpDNS.list%2C%20tag%3DBlockHttpDNS%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### BlockHttpDNS.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBlockHttpDNS%2Fegern%2FBlockHttpDNS.yaml)


### Shadowrocket

#### BlockHttpDNS.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/shadowrocket/BlockHttpDNS.list
```

### sing-box

#### BlockHttpDNS.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/sing-box/BlockHttpDNS.srs
```

## Artifacts

### mrs(ipcidr)

#### BlockHttpDNS_IP.mrs

GitHub: [BlockHttpDNS_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/mihomo/BlockHttpDNS_IP.mrs)
Text: [BlockHttpDNS_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/mihomo/BlockHttpDNS_IP.txt)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/mihomo/BlockHttpDNS_IP.mrs
```

### mrs(domain)

#### BlockHttpDNS_Domain.mrs

GitHub: [BlockHttpDNS_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/mihomo/BlockHttpDNS_Domain.mrs)
Text: [BlockHttpDNS_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/mihomo/BlockHttpDNS_Domain.txt)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/mihomo/BlockHttpDNS_Domain.mrs
```

### yaml(remaining)

#### BlockHttpDNS.yaml

GitHub: [BlockHttpDNS.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/mihomo/BlockHttpDNS.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/mihomo/BlockHttpDNS.yaml
```

### Surge

#### BlockHttpDNS.list

GitHub: [BlockHttpDNS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/surge/BlockHttpDNS.list)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/surge/BlockHttpDNS.list
```

#### BlockHttpDNS.domainset

GitHub: [BlockHttpDNS.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/surge/BlockHttpDNS.domainset)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/surge/BlockHttpDNS.domainset
```

### Loon

#### BlockHttpDNS.list

GitHub: [BlockHttpDNS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/loon/BlockHttpDNS.list)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/loon/BlockHttpDNS.list
```

### Quantumult X

#### BlockHttpDNS.list

GitHub: [BlockHttpDNS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/quantumult-x/BlockHttpDNS.list)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/quantumult-x/BlockHttpDNS.list
```

### Egern

#### BlockHttpDNS.yaml

GitHub: [BlockHttpDNS.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/egern/BlockHttpDNS.yaml)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/egern/BlockHttpDNS.yaml
```

### Shadowrocket

#### BlockHttpDNS.list

GitHub: [BlockHttpDNS.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/shadowrocket/BlockHttpDNS.list)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/shadowrocket/BlockHttpDNS.list
```

### sing-box

#### BlockHttpDNS.json

GitHub: [BlockHttpDNS.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/sing-box/BlockHttpDNS.json)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/sing-box/BlockHttpDNS.json
```

#### BlockHttpDNS.srs

GitHub: [BlockHttpDNS.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/sing-box/BlockHttpDNS.srs)
Source: [BlockHttpDNS.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/BlockHttpDNS/BlockHttpDNS.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/BlockHttpDNS/sing-box/BlockHttpDNS.srs
```
