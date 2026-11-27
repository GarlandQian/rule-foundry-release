# LINE

Source config: [LINE.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/LINE/LINE.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| LINE | LINE messaging rules from MagicRule | true | magicrule | classical | yaml | rules |  | [magicrule.pages.dev](https://magicrule.pages.dev/#/c/Mihomo/r/1c912e48-0681-42cc-ac3c-4fbd3d8de289) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "LINE"
    type: select
    proxies: []
rules:
  - RULE-SET,LINE_Domain,LINE
  - RULE-SET,LINE_IP,LINE,no-resolve
  - RULE-SET,LINE,LINE,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  LINE_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/mihomo/LINE_Domain.mrs }
  LINE_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/mihomo/LINE_IP.mrs }
  LINE: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/mihomo/LINE.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/surge/LINE.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/surge/LINE.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/loon/LINE.list,policy=<policy>,tag=LINE,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/quantumult-x/LINE.list, tag=LINE, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/egern/LINE.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/shadowrocket/LINE.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "LINE",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/sing-box/LINE.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "LINE",
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

#### LINE.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/surge/LINE.list
```

#### LINE.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/surge/LINE.domainset
```

### Loon

#### LINE.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLINE%2Floon%2FLINE.list)


### Quantumult X

#### LINE.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLINE%2Fquantumult-x%2FLINE.list%2C%20tag%3DLINE%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### LINE.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLINE%2Fegern%2FLINE.yaml)


### Shadowrocket

#### LINE.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/shadowrocket/LINE.list
```

### sing-box

#### LINE.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/sing-box/LINE.srs
```

## Artifacts

### mrs(ipcidr)

#### LINE_IP.mrs

GitHub: [LINE_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/mihomo/LINE_IP.mrs)
Text: [LINE_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/mihomo/LINE_IP.txt)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/mihomo/LINE_IP.mrs
```

### mrs(domain)

#### LINE_Domain.mrs

GitHub: [LINE_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/mihomo/LINE_Domain.mrs)
Text: [LINE_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/mihomo/LINE_Domain.txt)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/mihomo/LINE_Domain.mrs
```

### yaml(remaining)

#### LINE.yaml

GitHub: [LINE.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/mihomo/LINE.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/mihomo/LINE.yaml
```

### Surge

#### LINE.list

GitHub: [LINE.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/surge/LINE.list)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/surge/LINE.list
```

#### LINE.domainset

GitHub: [LINE.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/surge/LINE.domainset)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/surge/LINE.domainset
```

### Loon

#### LINE.list

GitHub: [LINE.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/loon/LINE.list)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/loon/LINE.list
```

### Quantumult X

#### LINE.list

GitHub: [LINE.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/quantumult-x/LINE.list)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/quantumult-x/LINE.list
```

### Egern

#### LINE.yaml

GitHub: [LINE.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/egern/LINE.yaml)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/egern/LINE.yaml
```

### Shadowrocket

#### LINE.list

GitHub: [LINE.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/shadowrocket/LINE.list)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/shadowrocket/LINE.list
```

### sing-box

#### LINE.json

GitHub: [LINE.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/sing-box/LINE.json)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/sing-box/LINE.json
```

#### LINE.srs

GitHub: [LINE.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/sing-box/LINE.srs)
Source: [LINE.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LINE/LINE.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LINE/sing-box/LINE.srs
```
