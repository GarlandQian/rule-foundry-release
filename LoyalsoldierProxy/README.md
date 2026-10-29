# LoyalsoldierProxy

Source config: [LoyalsoldierProxy.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/LoyalsoldierProxy/LoyalsoldierProxy.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| LoyalsoldierProxy | Loyalsoldier Proxy Rules | true | http | domain | yaml | rules |  | [proxy.txt](https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/proxy.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "LoyalsoldierProxy"
    type: select
    proxies: []
rules:
  - RULE-SET,LoyalsoldierProxy_Domain,LoyalsoldierProxy
  - RULE-SET,LoyalsoldierProxy,LoyalsoldierProxy,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,LoyalsoldierProxy_IP,LoyalsoldierProxy,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  LoyalsoldierProxy_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_Domain.mrs }
  LoyalsoldierProxy: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  LoyalsoldierProxy_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/loon/LoyalsoldierProxy.list,policy=<policy>,tag=LoyalsoldierProxy,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/quantumult-x/LoyalsoldierProxy.list, tag=LoyalsoldierProxy, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/egern/LoyalsoldierProxy.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/shadowrocket/LoyalsoldierProxy.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "LoyalsoldierProxy",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/sing-box/LoyalsoldierProxy.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "LoyalsoldierProxy",
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

#### LoyalsoldierProxy.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.list
```

#### LoyalsoldierProxy.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.domainset
```

### Loon

#### LoyalsoldierProxy.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierProxy%2Floon%2FLoyalsoldierProxy.list)


### Quantumult X

#### LoyalsoldierProxy.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierProxy%2Fquantumult-x%2FLoyalsoldierProxy.list%2C%20tag%3DLoyalsoldierProxy%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### LoyalsoldierProxy.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FLoyalsoldierProxy%2Fegern%2FLoyalsoldierProxy.yaml)


### Shadowrocket

#### LoyalsoldierProxy.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/shadowrocket/LoyalsoldierProxy.list
```

### sing-box

#### LoyalsoldierProxy.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/sing-box/LoyalsoldierProxy.srs
```

## Artifacts

### mrs(ipcidr)

#### LoyalsoldierProxy_IP.mrs

GitHub: [LoyalsoldierProxy_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_IP.mrs)
Text: [LoyalsoldierProxy_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_IP.mrs
```

### mrs(domain)

#### LoyalsoldierProxy_Domain.mrs

GitHub: [LoyalsoldierProxy_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_Domain.mrs)
Text: [LoyalsoldierProxy_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_Domain.txt)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy_Domain.mrs
```

### yaml(remaining)

#### LoyalsoldierProxy.yaml

GitHub: [LoyalsoldierProxy.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/mihomo/LoyalsoldierProxy.yaml
```

### Surge

#### LoyalsoldierProxy.list

GitHub: [LoyalsoldierProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.list)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.list
```

#### LoyalsoldierProxy.domainset

GitHub: [LoyalsoldierProxy.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.domainset)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/surge/LoyalsoldierProxy.domainset
```

### Loon

#### LoyalsoldierProxy.list

GitHub: [LoyalsoldierProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/loon/LoyalsoldierProxy.list)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/loon/LoyalsoldierProxy.list
```

### Quantumult X

#### LoyalsoldierProxy.list

GitHub: [LoyalsoldierProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/quantumult-x/LoyalsoldierProxy.list)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/quantumult-x/LoyalsoldierProxy.list
```

### Egern

#### LoyalsoldierProxy.yaml

GitHub: [LoyalsoldierProxy.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/egern/LoyalsoldierProxy.yaml)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/egern/LoyalsoldierProxy.yaml
```

### Shadowrocket

#### LoyalsoldierProxy.list

GitHub: [LoyalsoldierProxy.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/shadowrocket/LoyalsoldierProxy.list)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/shadowrocket/LoyalsoldierProxy.list
```

### sing-box

#### LoyalsoldierProxy.json

GitHub: [LoyalsoldierProxy.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/sing-box/LoyalsoldierProxy.json)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/sing-box/LoyalsoldierProxy.json
```

#### LoyalsoldierProxy.srs

GitHub: [LoyalsoldierProxy.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/sing-box/LoyalsoldierProxy.srs)
Source: [LoyalsoldierProxy.original.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/LoyalsoldierProxy/LoyalsoldierProxy.original.txt)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/LoyalsoldierProxy/sing-box/LoyalsoldierProxy.srs
```
