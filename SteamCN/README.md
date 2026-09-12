# SteamCN

Source config: [SteamCN.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/SteamCN/SteamCN.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| SteamCN | SteamCN | true | http | classical | yaml | rules |  | [SteamCN.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/SteamCN/SteamCN.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "SteamCN"
    type: select
    proxies: []
rules:
  - RULE-SET,SteamCN_Domain,SteamCN
  - RULE-SET,SteamCN,SteamCN,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,SteamCN_IP,SteamCN,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  SteamCN_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/mihomo/SteamCN_Domain.mrs }
  SteamCN: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/mihomo/SteamCN.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  SteamCN_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/mihomo/SteamCN_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/surge/SteamCN.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/surge/SteamCN.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/loon/SteamCN.list,policy=<policy>,tag=SteamCN,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/quantumult-x/SteamCN.list, tag=SteamCN, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/egern/SteamCN.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/shadowrocket/SteamCN.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "SteamCN",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/sing-box/SteamCN.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "SteamCN",
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

#### SteamCN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/surge/SteamCN.list
```

#### SteamCN.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/surge/SteamCN.domainset
```

### Loon

#### SteamCN.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteamCN%2Floon%2FSteamCN.list)


### Quantumult X

#### SteamCN.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteamCN%2Fquantumult-x%2FSteamCN.list%2C%20tag%3DSteamCN%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### SteamCN.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSteamCN%2Fegern%2FSteamCN.yaml)


### Shadowrocket

#### SteamCN.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/shadowrocket/SteamCN.list
```

### sing-box

#### SteamCN.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/sing-box/SteamCN.srs
```

## Artifacts

### mrs(ipcidr)

#### SteamCN_IP.mrs

GitHub: [SteamCN_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/mihomo/SteamCN_IP.mrs)
Text: [SteamCN_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/mihomo/SteamCN_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/mihomo/SteamCN_IP.mrs
```

### mrs(domain)

#### SteamCN_Domain.mrs

GitHub: [SteamCN_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/mihomo/SteamCN_Domain.mrs)
Text: [SteamCN_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/mihomo/SteamCN_Domain.txt)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/mihomo/SteamCN_Domain.mrs
```

### yaml(remaining)

#### SteamCN.yaml

GitHub: [SteamCN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/mihomo/SteamCN.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/mihomo/SteamCN.yaml
```

### Surge

#### SteamCN.list

GitHub: [SteamCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/surge/SteamCN.list)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/surge/SteamCN.list
```

#### SteamCN.domainset

GitHub: [SteamCN.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/surge/SteamCN.domainset)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/surge/SteamCN.domainset
```

### Loon

#### SteamCN.list

GitHub: [SteamCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/loon/SteamCN.list)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/loon/SteamCN.list
```

### Quantumult X

#### SteamCN.list

GitHub: [SteamCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/quantumult-x/SteamCN.list)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/quantumult-x/SteamCN.list
```

### Egern

#### SteamCN.yaml

GitHub: [SteamCN.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/egern/SteamCN.yaml)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/egern/SteamCN.yaml
```

### Shadowrocket

#### SteamCN.list

GitHub: [SteamCN.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/shadowrocket/SteamCN.list)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/shadowrocket/SteamCN.list
```

### sing-box

#### SteamCN.json

GitHub: [SteamCN.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/sing-box/SteamCN.json)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/sing-box/SteamCN.json
```

#### SteamCN.srs

GitHub: [SteamCN.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/sing-box/SteamCN.srs)
Source: [SteamCN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/SteamCN/SteamCN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/SteamCN/sing-box/SteamCN.srs
```
