# AppleProxy

Source config: [AppleProxy.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/AppleProxy/AppleProxy.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| AppleProxy | Apple proxy rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [apple-proxy.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/apple-proxy.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "AppleProxy"
    type: select
    proxies: []
rules:
  - RULE-SET,AppleProxy_Domain,AppleProxy
  - RULE-SET,AppleProxy,AppleProxy,no-resolve
  - RULE-SET,AppleProxy_IP,AppleProxy,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  AppleProxy_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/mihomo/AppleProxy_Domain.mrs }
  AppleProxy: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/mihomo/AppleProxy.yaml }
  AppleProxy_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/mihomo/AppleProxy_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/surge/AppleProxy.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/surge/AppleProxy.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/loon/AppleProxy.list,policy=<policy>,tag=AppleProxy,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/quantumult-x/AppleProxy.list, tag=AppleProxy, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/egern/AppleProxy.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/shadowrocket/AppleProxy.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "AppleProxy",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/sing-box/AppleProxy.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "AppleProxy",
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

#### AppleProxy.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/surge/AppleProxy.list
```

#### AppleProxy.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/surge/AppleProxy.domainset
```

### Loon

#### AppleProxy.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleProxy%2Floon%2FAppleProxy.list)


### Quantumult X

#### AppleProxy.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleProxy%2Fquantumult-x%2FAppleProxy.list%2C%20tag%3DAppleProxy%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### AppleProxy.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FAppleProxy%2Fegern%2FAppleProxy.yaml)


### Shadowrocket

#### AppleProxy.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/shadowrocket/AppleProxy.list
```

### sing-box

#### AppleProxy.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/sing-box/AppleProxy.srs
```

## Artifacts

### mrs(ipcidr)

#### AppleProxy_IP.mrs

GitHub: [AppleProxy_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/mihomo/AppleProxy_IP.mrs)
Text: [AppleProxy_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/mihomo/AppleProxy_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/mihomo/AppleProxy_IP.mrs
```

### mrs(domain)

#### AppleProxy_Domain.mrs

GitHub: [AppleProxy_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/mihomo/AppleProxy_Domain.mrs)
Text: [AppleProxy_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/mihomo/AppleProxy_Domain.txt)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/mihomo/AppleProxy_Domain.mrs
```

### yaml(remaining)

#### AppleProxy.yaml

GitHub: [AppleProxy.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/mihomo/AppleProxy.yaml)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/mihomo/AppleProxy.yaml
```

### Surge

#### AppleProxy.list

GitHub: [AppleProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/surge/AppleProxy.list)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/surge/AppleProxy.list
```

#### AppleProxy.domainset

GitHub: [AppleProxy.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/surge/AppleProxy.domainset)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/surge/AppleProxy.domainset
```

### Loon

#### AppleProxy.list

GitHub: [AppleProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/loon/AppleProxy.list)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/loon/AppleProxy.list
```

### Quantumult X

#### AppleProxy.list

GitHub: [AppleProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/quantumult-x/AppleProxy.list)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/quantumult-x/AppleProxy.list
```

### Egern

#### AppleProxy.yaml

GitHub: [AppleProxy.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/egern/AppleProxy.yaml)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/egern/AppleProxy.yaml
```

### Shadowrocket

#### AppleProxy.list

GitHub: [AppleProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/shadowrocket/AppleProxy.list)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/shadowrocket/AppleProxy.list
```

### sing-box

#### AppleProxy.json

GitHub: [AppleProxy.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/sing-box/AppleProxy.json)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/sing-box/AppleProxy.json
```

#### AppleProxy.srs

GitHub: [AppleProxy.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/sing-box/AppleProxy.srs)
Source: [AppleProxy.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/AppleProxy/AppleProxy.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/AppleProxy/sing-box/AppleProxy.srs
```
