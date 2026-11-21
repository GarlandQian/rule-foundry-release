# Bahamut

Source config: [Bahamut.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Bahamut/Bahamut.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Bahamut | Bahamut rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [bahamut.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/bahamut.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Bahamut"
    type: select
    proxies: []
rules:
  - RULE-SET,Bahamut_Domain,Bahamut
  - RULE-SET,Bahamut,Bahamut,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,Bahamut_IP,Bahamut,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Bahamut_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/mihomo/Bahamut_Domain.mrs }
  Bahamut: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/mihomo/Bahamut.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  Bahamut_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/mihomo/Bahamut_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/surge/Bahamut.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/surge/Bahamut.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/loon/Bahamut.list,policy=<policy>,tag=Bahamut,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/quantumult-x/Bahamut.list, tag=Bahamut, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/egern/Bahamut.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/shadowrocket/Bahamut.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Bahamut",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/sing-box/Bahamut.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Bahamut",
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

#### Bahamut.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/surge/Bahamut.list
```

#### Bahamut.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/surge/Bahamut.domainset
```

### Loon

#### Bahamut.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBahamut%2Floon%2FBahamut.list)


### Quantumult X

#### Bahamut.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBahamut%2Fquantumult-x%2FBahamut.list%2C%20tag%3DBahamut%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Bahamut.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FBahamut%2Fegern%2FBahamut.yaml)


### Shadowrocket

#### Bahamut.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/shadowrocket/Bahamut.list
```

### sing-box

#### Bahamut.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/sing-box/Bahamut.srs
```

## Artifacts

### mrs(ipcidr)

#### Bahamut_IP.mrs

GitHub: [Bahamut_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/mihomo/Bahamut_IP.mrs)
Text: [Bahamut_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/mihomo/Bahamut_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/mihomo/Bahamut_IP.mrs
```

### mrs(domain)

#### Bahamut_Domain.mrs

GitHub: [Bahamut_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/mihomo/Bahamut_Domain.mrs)
Text: [Bahamut_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/mihomo/Bahamut_Domain.txt)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/mihomo/Bahamut_Domain.mrs
```

### yaml(remaining)

#### Bahamut.yaml

GitHub: [Bahamut.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/mihomo/Bahamut.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/mihomo/Bahamut.yaml
```

### Surge

#### Bahamut.list

GitHub: [Bahamut.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/surge/Bahamut.list)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/surge/Bahamut.list
```

#### Bahamut.domainset

GitHub: [Bahamut.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/surge/Bahamut.domainset)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/surge/Bahamut.domainset
```

### Loon

#### Bahamut.list

GitHub: [Bahamut.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/loon/Bahamut.list)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/loon/Bahamut.list
```

### Quantumult X

#### Bahamut.list

GitHub: [Bahamut.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/quantumult-x/Bahamut.list)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/quantumult-x/Bahamut.list
```

### Egern

#### Bahamut.yaml

GitHub: [Bahamut.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/egern/Bahamut.yaml)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/egern/Bahamut.yaml
```

### Shadowrocket

#### Bahamut.list

GitHub: [Bahamut.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/shadowrocket/Bahamut.list)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/shadowrocket/Bahamut.list
```

### sing-box

#### Bahamut.json

GitHub: [Bahamut.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/sing-box/Bahamut.json)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/sing-box/Bahamut.json
```

#### Bahamut.srs

GitHub: [Bahamut.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/sing-box/Bahamut.srs)
Source: [Bahamut.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Bahamut/Bahamut.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Bahamut/sing-box/Bahamut.srs
```
