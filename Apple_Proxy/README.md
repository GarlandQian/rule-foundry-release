# Apple_Proxy

Source config: [Apple_Proxy.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Apple_Proxy/Apple_Proxy.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Apple_Proxy | Apple proxy rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [apple-proxy.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/apple-proxy.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Apple_Proxy"
    type: select
    proxies: []
rules:
  - RULE-SET,Apple_Proxy_Domain,Apple_Proxy
  - RULE-SET,Apple_Proxy,Apple_Proxy,no-resolve
  - RULE-SET,Apple_Proxy_IP,Apple_Proxy,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Apple_Proxy_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/mihomo/Apple_Proxy_Domain.mrs }
  Apple_Proxy: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/mihomo/Apple_Proxy.yaml }
  Apple_Proxy_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/mihomo/Apple_Proxy_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/surge/Apple_Proxy.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/surge/Apple_Proxy.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/loon/Apple_Proxy.list,policy=<policy>,tag=Apple_Proxy,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/quantumult-x/Apple_Proxy.list, tag=Apple_Proxy, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/egern/Apple_Proxy.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/shadowrocket/Apple_Proxy.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Apple_Proxy",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/sing-box/Apple_Proxy.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Apple_Proxy",
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

#### Apple_Proxy.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/surge/Apple_Proxy.list
```

#### Apple_Proxy.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/surge/Apple_Proxy.domainset
```

### Loon

#### Apple_Proxy.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_Proxy%2Floon%2FApple_Proxy.list)


### Quantumult X

#### Apple_Proxy.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_Proxy%2Fquantumult-x%2FApple_Proxy.list%2C%20tag%3DApple_Proxy%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Apple_Proxy.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_Proxy%2Fegern%2FApple_Proxy.yaml)


### Shadowrocket

#### Apple_Proxy.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/shadowrocket/Apple_Proxy.list
```

### sing-box

#### Apple_Proxy.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/sing-box/Apple_Proxy.srs
```

## Artifacts

### mrs(ipcidr)

#### Apple_Proxy_IP.mrs

GitHub: [Apple_Proxy_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/mihomo/Apple_Proxy_IP.mrs)
Text: [Apple_Proxy_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/mihomo/Apple_Proxy_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/mihomo/Apple_Proxy_IP.mrs
```

### mrs(domain)

#### Apple_Proxy_Domain.mrs

GitHub: [Apple_Proxy_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/mihomo/Apple_Proxy_Domain.mrs)
Text: [Apple_Proxy_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/mihomo/Apple_Proxy_Domain.txt)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/mihomo/Apple_Proxy_Domain.mrs
```

### yaml(remaining)

#### Apple_Proxy.yaml

GitHub: [Apple_Proxy.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/mihomo/Apple_Proxy.yaml)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/mihomo/Apple_Proxy.yaml
```

### Surge

#### Apple_Proxy.list

GitHub: [Apple_Proxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/surge/Apple_Proxy.list)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/surge/Apple_Proxy.list
```

#### Apple_Proxy.domainset

GitHub: [Apple_Proxy.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/surge/Apple_Proxy.domainset)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/surge/Apple_Proxy.domainset
```

### Loon

#### Apple_Proxy.list

GitHub: [Apple_Proxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/loon/Apple_Proxy.list)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/loon/Apple_Proxy.list
```

### Quantumult X

#### Apple_Proxy.list

GitHub: [Apple_Proxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/quantumult-x/Apple_Proxy.list)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/quantumult-x/Apple_Proxy.list
```

### Egern

#### Apple_Proxy.yaml

GitHub: [Apple_Proxy.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/egern/Apple_Proxy.yaml)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/egern/Apple_Proxy.yaml
```

### Shadowrocket

#### Apple_Proxy.list

GitHub: [Apple_Proxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/shadowrocket/Apple_Proxy.list)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/shadowrocket/Apple_Proxy.list
```

### sing-box

#### Apple_Proxy.json

GitHub: [Apple_Proxy.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/sing-box/Apple_Proxy.json)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/sing-box/Apple_Proxy.json
```

#### Apple_Proxy.srs

GitHub: [Apple_Proxy.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/sing-box/Apple_Proxy.srs)
Source: [Apple_Proxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_Proxy/Apple_Proxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_Proxy/sing-box/Apple_Proxy.srs
```
