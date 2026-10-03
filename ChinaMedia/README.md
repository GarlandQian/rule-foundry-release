# ChinaMedia

Source config: [ChinaMedia.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/ChinaMedia/ChinaMedia.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| ChinaMedia | ChinaMedia | true | http | classical | yaml | rules |  | [ChinaMedia.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/ChinaMedia/ChinaMedia.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "ChinaMedia"
    type: select
    proxies: []
rules:
  - RULE-SET,ChinaMedia_Domain,ChinaMedia
  - RULE-SET,ChinaMedia,ChinaMedia,no-resolve
  - RULE-SET,ChinaMedia_IP,ChinaMedia,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  ChinaMedia_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/mihomo/ChinaMedia_Domain.mrs }
  ChinaMedia: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/mihomo/ChinaMedia.yaml }
  ChinaMedia_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/mihomo/ChinaMedia_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/surge/ChinaMedia.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/surge/ChinaMedia.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/loon/ChinaMedia.list,policy=<policy>,tag=ChinaMedia,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/quantumult-x/ChinaMedia.list, tag=ChinaMedia, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/egern/ChinaMedia.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/shadowrocket/ChinaMedia.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "ChinaMedia",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/sing-box/ChinaMedia.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "ChinaMedia",
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

#### ChinaMedia.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/surge/ChinaMedia.list
```

#### ChinaMedia.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/surge/ChinaMedia.domainset
```

### Loon

#### ChinaMedia.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FChinaMedia%2Floon%2FChinaMedia.list)


### Quantumult X

#### ChinaMedia.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FChinaMedia%2Fquantumult-x%2FChinaMedia.list%2C%20tag%3DChinaMedia%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### ChinaMedia.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FChinaMedia%2Fegern%2FChinaMedia.yaml)


### Shadowrocket

#### ChinaMedia.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/shadowrocket/ChinaMedia.list
```

### sing-box

#### ChinaMedia.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/sing-box/ChinaMedia.srs
```

## Artifacts

### mrs(ipcidr)

#### ChinaMedia_IP.mrs

GitHub: [ChinaMedia_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/mihomo/ChinaMedia_IP.mrs)
Text: [ChinaMedia_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/mihomo/ChinaMedia_IP.txt)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/mihomo/ChinaMedia_IP.mrs
```

### mrs(domain)

#### ChinaMedia_Domain.mrs

GitHub: [ChinaMedia_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/mihomo/ChinaMedia_Domain.mrs)
Text: [ChinaMedia_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/mihomo/ChinaMedia_Domain.txt)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/mihomo/ChinaMedia_Domain.mrs
```

### yaml(remaining)

#### ChinaMedia.yaml

GitHub: [ChinaMedia.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/mihomo/ChinaMedia.yaml)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/mihomo/ChinaMedia.yaml
```

### Surge

#### ChinaMedia.list

GitHub: [ChinaMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/surge/ChinaMedia.list)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/surge/ChinaMedia.list
```

#### ChinaMedia.domainset

GitHub: [ChinaMedia.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/surge/ChinaMedia.domainset)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/surge/ChinaMedia.domainset
```

### Loon

#### ChinaMedia.list

GitHub: [ChinaMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/loon/ChinaMedia.list)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/loon/ChinaMedia.list
```

### Quantumult X

#### ChinaMedia.list

GitHub: [ChinaMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/quantumult-x/ChinaMedia.list)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/quantumult-x/ChinaMedia.list
```

### Egern

#### ChinaMedia.yaml

GitHub: [ChinaMedia.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/egern/ChinaMedia.yaml)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/egern/ChinaMedia.yaml
```

### Shadowrocket

#### ChinaMedia.list

GitHub: [ChinaMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/shadowrocket/ChinaMedia.list)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/shadowrocket/ChinaMedia.list
```

### sing-box

#### ChinaMedia.json

GitHub: [ChinaMedia.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/sing-box/ChinaMedia.json)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/sing-box/ChinaMedia.json
```

#### ChinaMedia.srs

GitHub: [ChinaMedia.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/sing-box/ChinaMedia.srs)
Source: [ChinaMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/ChinaMedia/ChinaMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/ChinaMedia/sing-box/ChinaMedia.srs
```
