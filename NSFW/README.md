# NSFW

Source config: [NSFW.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/NSFW/NSFW.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| NSFW | OISD NSFW full domain rules | true | http | classical | text | rules |  | [oisd_nsfw_surge.list](https://dl.oisd.nl/oisd_nsfw_surge.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "NSFW"
    type: select
    proxies: []
rules:
  - RULE-SET,NSFW_Domain,NSFW
  - RULE-SET,NSFW,NSFW,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,NSFW_IP,NSFW,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  NSFW_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/mihomo/NSFW_Domain.mrs }
  NSFW: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/mihomo/NSFW.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  NSFW_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/mihomo/NSFW_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/surge/NSFW.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/surge/NSFW.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/loon/NSFW.list,policy=<policy>,tag=NSFW,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/quantumult-x/NSFW.list, tag=NSFW, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/egern/NSFW.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/shadowrocket/NSFW.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "NSFW",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/sing-box/NSFW.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "NSFW",
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

#### NSFW.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/surge/NSFW.list
```

#### NSFW.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/surge/NSFW.domainset
```

### Loon

#### NSFW.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNSFW%2Floon%2FNSFW.list)


### Quantumult X

#### NSFW.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNSFW%2Fquantumult-x%2FNSFW.list%2C%20tag%3DNSFW%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### NSFW.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNSFW%2Fegern%2FNSFW.yaml)


### Shadowrocket

#### NSFW.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/shadowrocket/NSFW.list
```

### sing-box

#### NSFW.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/sing-box/NSFW.srs
```

## Artifacts

### mrs(ipcidr)

#### NSFW_IP.mrs

GitHub: [NSFW_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/mihomo/NSFW_IP.mrs)
Text: [NSFW_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/mihomo/NSFW_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/mihomo/NSFW_IP.mrs
```

### mrs(domain)

#### NSFW_Domain.mrs

GitHub: [NSFW_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/mihomo/NSFW_Domain.mrs)
Text: [NSFW_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/mihomo/NSFW_Domain.txt)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/mihomo/NSFW_Domain.mrs
```

### yaml(remaining)

#### NSFW.yaml

GitHub: [NSFW.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/mihomo/NSFW.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/mihomo/NSFW.yaml
```

### Surge

#### NSFW.list

GitHub: [NSFW.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/surge/NSFW.list)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/surge/NSFW.list
```

#### NSFW.domainset

GitHub: [NSFW.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/surge/NSFW.domainset)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/surge/NSFW.domainset
```

### Loon

#### NSFW.list

GitHub: [NSFW.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/loon/NSFW.list)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/loon/NSFW.list
```

### Quantumult X

#### NSFW.list

GitHub: [NSFW.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/quantumult-x/NSFW.list)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/quantumult-x/NSFW.list
```

### Egern

#### NSFW.yaml

GitHub: [NSFW.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/egern/NSFW.yaml)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/egern/NSFW.yaml
```

### Shadowrocket

#### NSFW.list

GitHub: [NSFW.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/shadowrocket/NSFW.list)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/shadowrocket/NSFW.list
```

### sing-box

#### NSFW.json

GitHub: [NSFW.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/sing-box/NSFW.json)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/sing-box/NSFW.json
```

#### NSFW.srs

GitHub: [NSFW.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/sing-box/NSFW.srs)
Source: [NSFW.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NSFW/NSFW.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NSFW/sing-box/NSFW.srs
```
