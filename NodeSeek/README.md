# NodeSeek

Source config: [NodeSeek.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/NodeSeek/NodeSeek.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| NodeSeek | NodeSeek domain suffixes from Ethan2258/rules | true | http | classical | yaml | rules |  | [Nodeseek.yaml](https://raw.githubusercontent.com/Ethan2258/rules/main/Nodeseek.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "NodeSeek"
    type: select
    proxies: []
rules:
  - RULE-SET,NodeSeek_Domain,NodeSeek
  - RULE-SET,NodeSeek,NodeSeek,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,NodeSeek_IP,NodeSeek,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  NodeSeek_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/mihomo/NodeSeek_Domain.mrs }
  NodeSeek: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/mihomo/NodeSeek.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  NodeSeek_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/mihomo/NodeSeek_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/surge/NodeSeek.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/surge/NodeSeek.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/loon/NodeSeek.list,policy=<policy>,tag=NodeSeek,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/quantumult-x/NodeSeek.list, tag=NodeSeek, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/egern/NodeSeek.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/shadowrocket/NodeSeek.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "NodeSeek",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/sing-box/NodeSeek.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "NodeSeek",
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

#### NodeSeek.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/surge/NodeSeek.list
```

#### NodeSeek.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/surge/NodeSeek.domainset
```

### Loon

#### NodeSeek.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNodeSeek%2Floon%2FNodeSeek.list)


### Quantumult X

#### NodeSeek.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNodeSeek%2Fquantumult-x%2FNodeSeek.list%2C%20tag%3DNodeSeek%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### NodeSeek.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FNodeSeek%2Fegern%2FNodeSeek.yaml)


### Shadowrocket

#### NodeSeek.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/shadowrocket/NodeSeek.list
```

### sing-box

#### NodeSeek.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/sing-box/NodeSeek.srs
```

## Artifacts

### mrs(ipcidr)

#### NodeSeek_IP.mrs

GitHub: [NodeSeek_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/mihomo/NodeSeek_IP.mrs)
Text: [NodeSeek_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/mihomo/NodeSeek_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/mihomo/NodeSeek_IP.mrs
```

### mrs(domain)

#### NodeSeek_Domain.mrs

GitHub: [NodeSeek_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/mihomo/NodeSeek_Domain.mrs)
Text: [NodeSeek_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/mihomo/NodeSeek_Domain.txt)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/mihomo/NodeSeek_Domain.mrs
```

### yaml(remaining)

#### NodeSeek.yaml

GitHub: [NodeSeek.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/mihomo/NodeSeek.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/mihomo/NodeSeek.yaml
```

### Surge

#### NodeSeek.list

GitHub: [NodeSeek.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/surge/NodeSeek.list)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/surge/NodeSeek.list
```

#### NodeSeek.domainset

GitHub: [NodeSeek.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/surge/NodeSeek.domainset)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/surge/NodeSeek.domainset
```

### Loon

#### NodeSeek.list

GitHub: [NodeSeek.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/loon/NodeSeek.list)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/loon/NodeSeek.list
```

### Quantumult X

#### NodeSeek.list

GitHub: [NodeSeek.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/quantumult-x/NodeSeek.list)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/quantumult-x/NodeSeek.list
```

### Egern

#### NodeSeek.yaml

GitHub: [NodeSeek.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/egern/NodeSeek.yaml)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/egern/NodeSeek.yaml
```

### Shadowrocket

#### NodeSeek.list

GitHub: [NodeSeek.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/shadowrocket/NodeSeek.list)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/shadowrocket/NodeSeek.list
```

### sing-box

#### NodeSeek.json

GitHub: [NodeSeek.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/sing-box/NodeSeek.json)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/sing-box/NodeSeek.json
```

#### NodeSeek.srs

GitHub: [NodeSeek.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/sing-box/NodeSeek.srs)
Source: [NodeSeek.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/NodeSeek/NodeSeek.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/NodeSeek/sing-box/NodeSeek.srs
```
