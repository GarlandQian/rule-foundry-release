# Crypto

Source config: [Crypto.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Crypto/Crypto.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Crypto | Cryptocurrency rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [crypto.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/crypto.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Crypto"
    type: select
    proxies: []
rules:
  - RULE-SET,Crypto_Domain,Crypto
  - RULE-SET,Crypto,Crypto,no-resolve
  - RULE-SET,Crypto_IP,Crypto,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Crypto_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/mihomo/Crypto_Domain.mrs }
  Crypto: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/mihomo/Crypto.yaml }
  Crypto_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/mihomo/Crypto_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/surge/Crypto.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/surge/Crypto.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/loon/Crypto.list,policy=<policy>,tag=Crypto,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/quantumult-x/Crypto.list, tag=Crypto, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/egern/Crypto.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/shadowrocket/Crypto.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Crypto",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/sing-box/Crypto.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Crypto",
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

#### Crypto.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/surge/Crypto.list
```

#### Crypto.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/surge/Crypto.domainset
```

### Loon

#### Crypto.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCrypto%2Floon%2FCrypto.list)


### Quantumult X

#### Crypto.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCrypto%2Fquantumult-x%2FCrypto.list%2C%20tag%3DCrypto%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Crypto.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCrypto%2Fegern%2FCrypto.yaml)


### Shadowrocket

#### Crypto.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/shadowrocket/Crypto.list
```

### sing-box

#### Crypto.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/sing-box/Crypto.srs
```

## Artifacts

### mrs(ipcidr)

#### Crypto_IP.mrs

GitHub: [Crypto_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/mihomo/Crypto_IP.mrs)
Text: [Crypto_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/mihomo/Crypto_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/mihomo/Crypto_IP.mrs
```

### mrs(domain)

#### Crypto_Domain.mrs

GitHub: [Crypto_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/mihomo/Crypto_Domain.mrs)
Text: [Crypto_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/mihomo/Crypto_Domain.txt)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/mihomo/Crypto_Domain.mrs
```

### yaml(remaining)

#### Crypto.yaml

GitHub: [Crypto.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/mihomo/Crypto.yaml)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/mihomo/Crypto.yaml
```

### Surge

#### Crypto.list

GitHub: [Crypto.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/surge/Crypto.list)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/surge/Crypto.list
```

#### Crypto.domainset

GitHub: [Crypto.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/surge/Crypto.domainset)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/surge/Crypto.domainset
```

### Loon

#### Crypto.list

GitHub: [Crypto.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/loon/Crypto.list)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/loon/Crypto.list
```

### Quantumult X

#### Crypto.list

GitHub: [Crypto.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/quantumult-x/Crypto.list)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/quantumult-x/Crypto.list
```

### Egern

#### Crypto.yaml

GitHub: [Crypto.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/egern/Crypto.yaml)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/egern/Crypto.yaml
```

### Shadowrocket

#### Crypto.list

GitHub: [Crypto.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/shadowrocket/Crypto.list)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/shadowrocket/Crypto.list
```

### sing-box

#### Crypto.json

GitHub: [Crypto.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/sing-box/Crypto.json)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/sing-box/Crypto.json
```

#### Crypto.srs

GitHub: [Crypto.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/sing-box/Crypto.srs)
Source: [Crypto.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Crypto/Crypto.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Crypto/sing-box/Crypto.srs
```
