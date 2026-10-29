# PayPal

Source config: [PayPal.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/PayPal/PayPal.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| PayPal | PayPal rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [paypal.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/paypal.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "PayPal"
    type: select
    proxies: []
rules:
  - RULE-SET,PayPal_Domain,PayPal
  - RULE-SET,PayPal,PayPal,no-resolve
  - RULE-SET,PayPal_IP,PayPal,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  PayPal_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/mihomo/PayPal_Domain.mrs }
  PayPal: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/mihomo/PayPal.yaml }
  PayPal_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/mihomo/PayPal_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/surge/PayPal.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/surge/PayPal.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/loon/PayPal.list,policy=<policy>,tag=PayPal,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/quantumult-x/PayPal.list, tag=PayPal, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/egern/PayPal.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/shadowrocket/PayPal.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "PayPal",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/sing-box/PayPal.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "PayPal",
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

#### PayPal.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/surge/PayPal.list
```

#### PayPal.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/surge/PayPal.domainset
```

### Loon

#### PayPal.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPayPal%2Floon%2FPayPal.list)


### Quantumult X

#### PayPal.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPayPal%2Fquantumult-x%2FPayPal.list%2C%20tag%3DPayPal%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### PayPal.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPayPal%2Fegern%2FPayPal.yaml)


### Shadowrocket

#### PayPal.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/shadowrocket/PayPal.list
```

### sing-box

#### PayPal.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/sing-box/PayPal.srs
```

## Artifacts

### mrs(ipcidr)

#### PayPal_IP.mrs

GitHub: [PayPal_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/mihomo/PayPal_IP.mrs)
Text: [PayPal_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/mihomo/PayPal_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/mihomo/PayPal_IP.mrs
```

### mrs(domain)

#### PayPal_Domain.mrs

GitHub: [PayPal_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/mihomo/PayPal_Domain.mrs)
Text: [PayPal_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/mihomo/PayPal_Domain.txt)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/mihomo/PayPal_Domain.mrs
```

### yaml(remaining)

#### PayPal.yaml

GitHub: [PayPal.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/mihomo/PayPal.yaml)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/mihomo/PayPal.yaml
```

### Surge

#### PayPal.list

GitHub: [PayPal.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/surge/PayPal.list)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/surge/PayPal.list
```

#### PayPal.domainset

GitHub: [PayPal.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/surge/PayPal.domainset)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/surge/PayPal.domainset
```

### Loon

#### PayPal.list

GitHub: [PayPal.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/loon/PayPal.list)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/loon/PayPal.list
```

### Quantumult X

#### PayPal.list

GitHub: [PayPal.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/quantumult-x/PayPal.list)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/quantumult-x/PayPal.list
```

### Egern

#### PayPal.yaml

GitHub: [PayPal.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/egern/PayPal.yaml)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/egern/PayPal.yaml
```

### Shadowrocket

#### PayPal.list

GitHub: [PayPal.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/shadowrocket/PayPal.list)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/shadowrocket/PayPal.list
```

### sing-box

#### PayPal.json

GitHub: [PayPal.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/sing-box/PayPal.json)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/sing-box/PayPal.json
```

#### PayPal.srs

GitHub: [PayPal.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/sing-box/PayPal.srs)
Source: [PayPal.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/PayPal/PayPal.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/PayPal/sing-box/PayPal.srs
```
