# Nvidia

Source config: [Nvidia.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Nvidia/Nvidia.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Nvidia | Nvidia rules from MagicRule | true | magicrule | classical | yaml | rules |  | [magicrule.pages.dev](https://magicrule.pages.dev/#/c/Mihomo/r/6ef578c7-e491-4928-a661-de42a7d56f4e) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Nvidia"
    type: select
    proxies: []
rules:
  - RULE-SET,Nvidia_Domain,Nvidia
  - RULE-SET,Nvidia,Nvidia,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,Nvidia_IP,Nvidia,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Nvidia_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/mihomo/Nvidia_Domain.mrs }
  Nvidia: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/mihomo/Nvidia.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  Nvidia_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/mihomo/Nvidia_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/surge/Nvidia.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/surge/Nvidia.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/loon/Nvidia.list,policy=<policy>,tag=Nvidia,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/quantumult-x/Nvidia.list, tag=Nvidia, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/egern/Nvidia.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/shadowrocket/Nvidia.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Nvidia",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/sing-box/Nvidia.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Nvidia",
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

#### Nvidia.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/surge/Nvidia.list
```

#### Nvidia.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/surge/Nvidia.domainset
```

### Loon

#### Nvidia.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNvidia%2Floon%2FNvidia.list)


### Quantumult X

#### Nvidia.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNvidia%2Fquantumult-x%2FNvidia.list%2C%20tag%3DNvidia%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Nvidia.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNvidia%2Fegern%2FNvidia.yaml)


### Shadowrocket

#### Nvidia.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/shadowrocket/Nvidia.list
```

### sing-box

#### Nvidia.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/sing-box/Nvidia.srs
```

## Artifacts

### mrs(ipcidr)

#### Nvidia_IP.mrs

GitHub: [Nvidia_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/mihomo/Nvidia_IP.mrs)
Text: [Nvidia_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/mihomo/Nvidia_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/mihomo/Nvidia_IP.mrs
```

### mrs(domain)

#### Nvidia_Domain.mrs

GitHub: [Nvidia_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/mihomo/Nvidia_Domain.mrs)
Text: [Nvidia_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/mihomo/Nvidia_Domain.txt)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/mihomo/Nvidia_Domain.mrs
```

### yaml(remaining)

#### Nvidia.yaml

GitHub: [Nvidia.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/mihomo/Nvidia.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/mihomo/Nvidia.yaml
```

### Surge

#### Nvidia.list

GitHub: [Nvidia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/surge/Nvidia.list)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/surge/Nvidia.list
```

#### Nvidia.domainset

GitHub: [Nvidia.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/surge/Nvidia.domainset)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/surge/Nvidia.domainset
```

### Loon

#### Nvidia.list

GitHub: [Nvidia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/loon/Nvidia.list)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/loon/Nvidia.list
```

### Quantumult X

#### Nvidia.list

GitHub: [Nvidia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/quantumult-x/Nvidia.list)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/quantumult-x/Nvidia.list
```

### Egern

#### Nvidia.yaml

GitHub: [Nvidia.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/egern/Nvidia.yaml)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/egern/Nvidia.yaml
```

### Shadowrocket

#### Nvidia.list

GitHub: [Nvidia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/shadowrocket/Nvidia.list)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/shadowrocket/Nvidia.list
```

### sing-box

#### Nvidia.json

GitHub: [Nvidia.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/sing-box/Nvidia.json)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/sing-box/Nvidia.json
```

#### Nvidia.srs

GitHub: [Nvidia.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/sing-box/Nvidia.srs)
Source: [Nvidia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Nvidia/Nvidia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Nvidia/sing-box/Nvidia.srs
```
