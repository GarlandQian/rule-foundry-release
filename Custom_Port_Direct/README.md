# Custom_Port_Direct

Source config: [Custom_Port_Direct.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Custom_Port_Direct/Custom_Port_Direct.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Custom_Port_Direct | Custom_Port_Direct | true | http | classical | yaml | rules |  | [Custom_Port_Direct.yaml](https://raw.githubusercontent.com/Aethersailor/Custom_OpenClash_Rules/refs/heads/main/rule/Custom_Port_Direct.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Custom_Port_Direct"
    type: select
    proxies: []
rules:
  - RULE-SET,Custom_Port_Direct,Custom_Port_Direct,no-resolve
  - RULE-SET,Custom_Port_Direct_Domain,Custom_Port_Direct # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,Custom_Port_Direct_IP,Custom_Port_Direct,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Custom_Port_Direct: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/mihomo/Custom_Port_Direct.yaml }
  Custom_Port_Direct_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  Custom_Port_Direct_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/surge/Custom_Port_Direct.list,<policy>
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/shadowrocket/Custom_Port_Direct.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Custom_Port_Direct",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/sing-box/Custom_Port_Direct.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Custom_Port_Direct",
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

#### Custom_Port_Direct.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/surge/Custom_Port_Direct.list
```

### Shadowrocket

#### Custom_Port_Direct.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/shadowrocket/Custom_Port_Direct.list
```

### sing-box

#### Custom_Port_Direct.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/sing-box/Custom_Port_Direct.srs
```

## Artifacts

### mrs(ipcidr)

#### Custom_Port_Direct_IP.mrs

GitHub: [Custom_Port_Direct_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_IP.mrs)
Text: [Custom_Port_Direct_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_IP.mrs
```

### mrs(domain)

#### Custom_Port_Direct_Domain.mrs

GitHub: [Custom_Port_Direct_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_Domain.mrs)
Text: [Custom_Port_Direct_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/mihomo/Custom_Port_Direct_Domain.mrs
```

### yaml(remaining)

#### Custom_Port_Direct.yaml

GitHub: [Custom_Port_Direct.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/mihomo/Custom_Port_Direct.yaml)
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/mihomo/Custom_Port_Direct.yaml
```

### Surge

#### Custom_Port_Direct.list

GitHub: [Custom_Port_Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/surge/Custom_Port_Direct.list)
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/surge/Custom_Port_Direct.list
```

### Shadowrocket

#### Custom_Port_Direct.list

GitHub: [Custom_Port_Direct.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/shadowrocket/Custom_Port_Direct.list)
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/shadowrocket/Custom_Port_Direct.list
```

### sing-box

#### Custom_Port_Direct.json

GitHub: [Custom_Port_Direct.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/sing-box/Custom_Port_Direct.json)
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/sing-box/Custom_Port_Direct.json
```

#### Custom_Port_Direct.srs

GitHub: [Custom_Port_Direct.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/sing-box/Custom_Port_Direct.srs)
Source: [Custom_Port_Direct.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Custom_Port_Direct/Custom_Port_Direct.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Custom_Port_Direct/sing-box/Custom_Port_Direct.srs
```
