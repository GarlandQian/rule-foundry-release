# Custom_Proxy_Classical

Source config: [Custom_Proxy_Classical.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Custom_Proxy_Classical/Custom_Proxy_Classical.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Custom_Proxy_Classical | Custom_Proxy_Classical | true | http | classical | yaml | rules |  | [Custom_Proxy_Classical_IP.yaml](https://raw.githubusercontent.com/Aethersailor/Custom_OpenClash_Rules/main/rule/Custom_Proxy_Classical_IP.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Custom_Proxy_Classical"
    type: select
    proxies: []
rules:
  - RULE-SET,Custom_Proxy_Classical_IP,Custom_Proxy_Classical,no-resolve
  - RULE-SET,Custom_Proxy_Classical_Domain,Custom_Proxy_Classical # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,Custom_Proxy_Classical,Custom_Proxy_Classical,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Custom_Proxy_Classical_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_IP.mrs }
  Custom_Proxy_Classical_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  Custom_Proxy_Classical: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/surge/Custom_Proxy_Classical.list,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/loon/Custom_Proxy_Classical.list,policy=<policy>,tag=Custom_Proxy_Classical,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/quantumult-x/Custom_Proxy_Classical.list, tag=Custom_Proxy_Classical, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/egern/Custom_Proxy_Classical.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/shadowrocket/Custom_Proxy_Classical.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Custom_Proxy_Classical",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/sing-box/Custom_Proxy_Classical.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Custom_Proxy_Classical",
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

#### Custom_Proxy_Classical.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/surge/Custom_Proxy_Classical.list
```

### Loon

#### Custom_Proxy_Classical.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCustom_Proxy_Classical%2Floon%2FCustom_Proxy_Classical.list)


### Quantumult X

#### Custom_Proxy_Classical.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCustom_Proxy_Classical%2Fquantumult-x%2FCustom_Proxy_Classical.list%2C%20tag%3DCustom_Proxy_Classical%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Custom_Proxy_Classical.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FCustom_Proxy_Classical%2Fegern%2FCustom_Proxy_Classical.yaml)


### Shadowrocket

#### Custom_Proxy_Classical.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/shadowrocket/Custom_Proxy_Classical.list
```

### sing-box

#### Custom_Proxy_Classical.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/sing-box/Custom_Proxy_Classical.srs
```

## Artifacts

### mrs(ipcidr)

#### Custom_Proxy_Classical_IP.mrs

GitHub: [Custom_Proxy_Classical_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_IP.mrs)
Text: [Custom_Proxy_Classical_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_IP.txt)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_IP.mrs
```

### mrs(domain)

#### Custom_Proxy_Classical_Domain.mrs

GitHub: [Custom_Proxy_Classical_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_Domain.mrs)
Text: [Custom_Proxy_Classical_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical_Domain.mrs
```

### yaml(remaining)

#### Custom_Proxy_Classical.yaml

GitHub: [Custom_Proxy_Classical.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/mihomo/Custom_Proxy_Classical.yaml
```

### Surge

#### Custom_Proxy_Classical.list

GitHub: [Custom_Proxy_Classical.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/surge/Custom_Proxy_Classical.list)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/surge/Custom_Proxy_Classical.list
```

### Loon

#### Custom_Proxy_Classical.list

GitHub: [Custom_Proxy_Classical.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/loon/Custom_Proxy_Classical.list)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/loon/Custom_Proxy_Classical.list
```

### Quantumult X

#### Custom_Proxy_Classical.list

GitHub: [Custom_Proxy_Classical.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/quantumult-x/Custom_Proxy_Classical.list)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/quantumult-x/Custom_Proxy_Classical.list
```

### Egern

#### Custom_Proxy_Classical.yaml

GitHub: [Custom_Proxy_Classical.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/egern/Custom_Proxy_Classical.yaml)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/egern/Custom_Proxy_Classical.yaml
```

### Shadowrocket

#### Custom_Proxy_Classical.list

GitHub: [Custom_Proxy_Classical.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/shadowrocket/Custom_Proxy_Classical.list)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/shadowrocket/Custom_Proxy_Classical.list
```

### sing-box

#### Custom_Proxy_Classical.json

GitHub: [Custom_Proxy_Classical.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/sing-box/Custom_Proxy_Classical.json)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/sing-box/Custom_Proxy_Classical.json
```

#### Custom_Proxy_Classical.srs

GitHub: [Custom_Proxy_Classical.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/sing-box/Custom_Proxy_Classical.srs)
Source: [Custom_Proxy_Classical.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Proxy_Classical/Custom_Proxy_Classical.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Proxy_Classical/sing-box/Custom_Proxy_Classical.srs
```
