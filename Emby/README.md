# Emby

Source config: [Emby.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Emby/Emby.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Emby | Emby rules from MagicRule | true | magicrule | classical | yaml | rules |  | [magicrule.pages.dev](https://magicrule.pages.dev/#/c/Mihomo/r/6ca859f7-d779-4599-9da7-6da623d9554e) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Emby"
    type: select
    proxies: []
rules:
  - RULE-SET,Emby_Domain,Emby
  - RULE-SET,Emby,Emby,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,Emby_IP,Emby,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Emby_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/mihomo/Emby_Domain.mrs }
  Emby: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/mihomo/Emby.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  Emby_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/mihomo/Emby_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/surge/Emby.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/surge/Emby.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/loon/Emby.list,policy=<policy>,tag=Emby,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/quantumult-x/Emby.list, tag=Emby, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/egern/Emby.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/shadowrocket/Emby.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Emby",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/sing-box/Emby.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Emby",
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

#### Emby.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/surge/Emby.list
```

#### Emby.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/surge/Emby.domainset
```

### Loon

#### Emby.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FEmby%2Floon%2FEmby.list)


### Quantumult X

#### Emby.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FEmby%2Fquantumult-x%2FEmby.list%2C%20tag%3DEmby%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Emby.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FEmby%2Fegern%2FEmby.yaml)


### Shadowrocket

#### Emby.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/shadowrocket/Emby.list
```

### sing-box

#### Emby.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/sing-box/Emby.srs
```

## Artifacts

### mrs(ipcidr)

#### Emby_IP.mrs

GitHub: [Emby_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/mihomo/Emby_IP.mrs)
Text: [Emby_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/mihomo/Emby_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/mihomo/Emby_IP.mrs
```

### mrs(domain)

#### Emby_Domain.mrs

GitHub: [Emby_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/mihomo/Emby_Domain.mrs)
Text: [Emby_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/mihomo/Emby_Domain.txt)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/mihomo/Emby_Domain.mrs
```

### yaml(remaining)

#### Emby.yaml

GitHub: [Emby.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/mihomo/Emby.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/mihomo/Emby.yaml
```

### Surge

#### Emby.list

GitHub: [Emby.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/surge/Emby.list)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/surge/Emby.list
```

#### Emby.domainset

GitHub: [Emby.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/surge/Emby.domainset)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/surge/Emby.domainset
```

### Loon

#### Emby.list

GitHub: [Emby.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/loon/Emby.list)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/loon/Emby.list
```

### Quantumult X

#### Emby.list

GitHub: [Emby.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/quantumult-x/Emby.list)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/quantumult-x/Emby.list
```

### Egern

#### Emby.yaml

GitHub: [Emby.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/egern/Emby.yaml)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/egern/Emby.yaml
```

### Shadowrocket

#### Emby.list

GitHub: [Emby.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/shadowrocket/Emby.list)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/shadowrocket/Emby.list
```

### sing-box

#### Emby.json

GitHub: [Emby.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/sing-box/Emby.json)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/sing-box/Emby.json
```

#### Emby.srs

GitHub: [Emby.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/sing-box/Emby.srs)
Source: [Emby.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Emby/Emby.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Emby/sing-box/Emby.srs
```
