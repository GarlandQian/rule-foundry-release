# linuxdo

Source config: [linuxdo.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/linuxdo/linuxdo.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| linuxdo | LinuxDo from MetaCubeX/meta-rules-dat | true | http | domain | text | rules |  | [linuxdo.list](https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geosite/linuxdo.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "linuxdo"
    type: select
    proxies: []
rules:
  - RULE-SET,linuxdo_Domain,linuxdo
  - RULE-SET,linuxdo,linuxdo,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,linuxdo_IP,linuxdo,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  linuxdo_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/mihomo/linuxdo_Domain.mrs }
  linuxdo: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/mihomo/linuxdo.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  linuxdo_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/mihomo/linuxdo_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/surge/linuxdo.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/surge/linuxdo.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/loon/linuxdo.list,policy=<policy>,tag=linuxdo,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/quantumult-x/linuxdo.list, tag=linuxdo, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/egern/linuxdo.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/shadowrocket/linuxdo.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "linuxdo",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/sing-box/linuxdo.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "linuxdo",
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

#### linuxdo.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/surge/linuxdo.list
```

#### linuxdo.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/surge/linuxdo.domainset
```

### Loon

#### linuxdo.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2Flinuxdo%2Floon%2Flinuxdo.list)


### Quantumult X

#### linuxdo.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2Flinuxdo%2Fquantumult-x%2Flinuxdo.list%2C%20tag%3Dlinuxdo%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### linuxdo.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2Flinuxdo%2Fegern%2Flinuxdo.yaml)


### Shadowrocket

#### linuxdo.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/shadowrocket/linuxdo.list
```

### sing-box

#### linuxdo.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/sing-box/linuxdo.srs
```

## Artifacts

### mrs(ipcidr)

#### linuxdo_IP.mrs

GitHub: [linuxdo_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/mihomo/linuxdo_IP.mrs)
Text: [linuxdo_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/mihomo/linuxdo_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/mihomo/linuxdo_IP.mrs
```

### mrs(domain)

#### linuxdo_Domain.mrs

GitHub: [linuxdo_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/mihomo/linuxdo_Domain.mrs)
Text: [linuxdo_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/mihomo/linuxdo_Domain.txt)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/mihomo/linuxdo_Domain.mrs
```

### yaml(remaining)

#### linuxdo.yaml

GitHub: [linuxdo.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/mihomo/linuxdo.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/mihomo/linuxdo.yaml
```

### Surge

#### linuxdo.list

GitHub: [linuxdo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/surge/linuxdo.list)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/surge/linuxdo.list
```

#### linuxdo.domainset

GitHub: [linuxdo.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/surge/linuxdo.domainset)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/surge/linuxdo.domainset
```

### Loon

#### linuxdo.list

GitHub: [linuxdo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/loon/linuxdo.list)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/loon/linuxdo.list
```

### Quantumult X

#### linuxdo.list

GitHub: [linuxdo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/quantumult-x/linuxdo.list)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/quantumult-x/linuxdo.list
```

### Egern

#### linuxdo.yaml

GitHub: [linuxdo.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/egern/linuxdo.yaml)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/egern/linuxdo.yaml
```

### Shadowrocket

#### linuxdo.list

GitHub: [linuxdo.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/shadowrocket/linuxdo.list)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/shadowrocket/linuxdo.list
```

### sing-box

#### linuxdo.json

GitHub: [linuxdo.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/sing-box/linuxdo.json)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/sing-box/linuxdo.json
```

#### linuxdo.srs

GitHub: [linuxdo.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/sing-box/linuxdo.srs)
Source: [linuxdo.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/linuxdo/linuxdo.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/linuxdo/sing-box/linuxdo.srs
```
