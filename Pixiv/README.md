# Pixiv

Source config: [Pixiv.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Pixiv/Pixiv.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Pixiv | Pixiv | true | http | classical | yaml | rules |  | [Pixiv.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Pixiv/Pixiv.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Pixiv"
    type: select
    proxies: []
rules:
  - RULE-SET,Pixiv_Domain,Pixiv
  - RULE-SET,Pixiv,Pixiv,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,Pixiv_IP,Pixiv,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Pixiv_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/mihomo/Pixiv_Domain.mrs }
  Pixiv: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/mihomo/Pixiv.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  Pixiv_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/mihomo/Pixiv_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/surge/Pixiv.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/surge/Pixiv.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/loon/Pixiv.list,policy=<policy>,tag=Pixiv,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/quantumult-x/Pixiv.list, tag=Pixiv, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/egern/Pixiv.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/shadowrocket/Pixiv.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Pixiv",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/sing-box/Pixiv.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Pixiv",
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

#### Pixiv.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/surge/Pixiv.list
```

#### Pixiv.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/surge/Pixiv.domainset
```

### Loon

#### Pixiv.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPixiv%2Floon%2FPixiv.list)


### Quantumult X

#### Pixiv.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPixiv%2Fquantumult-x%2FPixiv.list%2C%20tag%3DPixiv%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Pixiv.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FPixiv%2Fegern%2FPixiv.yaml)


### Shadowrocket

#### Pixiv.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/shadowrocket/Pixiv.list
```

### sing-box

#### Pixiv.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/sing-box/Pixiv.srs
```

## Artifacts

### mrs(ipcidr)

#### Pixiv_IP.mrs

GitHub: [Pixiv_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/mihomo/Pixiv_IP.mrs)
Text: [Pixiv_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/mihomo/Pixiv_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/mihomo/Pixiv_IP.mrs
```

### mrs(domain)

#### Pixiv_Domain.mrs

GitHub: [Pixiv_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/mihomo/Pixiv_Domain.mrs)
Text: [Pixiv_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/mihomo/Pixiv_Domain.txt)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/mihomo/Pixiv_Domain.mrs
```

### yaml(remaining)

#### Pixiv.yaml

GitHub: [Pixiv.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/mihomo/Pixiv.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/mihomo/Pixiv.yaml
```

### Surge

#### Pixiv.list

GitHub: [Pixiv.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/surge/Pixiv.list)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/surge/Pixiv.list
```

#### Pixiv.domainset

GitHub: [Pixiv.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/surge/Pixiv.domainset)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/surge/Pixiv.domainset
```

### Loon

#### Pixiv.list

GitHub: [Pixiv.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/loon/Pixiv.list)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/loon/Pixiv.list
```

### Quantumult X

#### Pixiv.list

GitHub: [Pixiv.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/quantumult-x/Pixiv.list)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/quantumult-x/Pixiv.list
```

### Egern

#### Pixiv.yaml

GitHub: [Pixiv.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/egern/Pixiv.yaml)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/egern/Pixiv.yaml
```

### Shadowrocket

#### Pixiv.list

GitHub: [Pixiv.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/shadowrocket/Pixiv.list)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/shadowrocket/Pixiv.list
```

### sing-box

#### Pixiv.json

GitHub: [Pixiv.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/sing-box/Pixiv.json)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/sing-box/Pixiv.json
```

#### Pixiv.srs

GitHub: [Pixiv.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/sing-box/Pixiv.srs)
Source: [Pixiv.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Pixiv/Pixiv.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Pixiv/sing-box/Pixiv.srs
```
