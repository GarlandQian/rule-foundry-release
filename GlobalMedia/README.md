# GlobalMedia

Source config: [GlobalMedia.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/GlobalMedia/GlobalMedia.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| GlobalMedia | GlobalMedia | true | http | classical | yaml | rules |  | [GlobalMedia_Classical_No_Resolve.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/GlobalMedia/GlobalMedia_Classical_No_Resolve.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "GlobalMedia"
    type: select
    proxies: []
rules:
  - RULE-SET,GlobalMedia_Domain,GlobalMedia
  - RULE-SET,GlobalMedia,GlobalMedia,no-resolve
  - RULE-SET,GlobalMedia_IP,GlobalMedia,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  GlobalMedia_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/mihomo/GlobalMedia_Domain.mrs }
  GlobalMedia: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/mihomo/GlobalMedia.yaml }
  GlobalMedia_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/mihomo/GlobalMedia_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/surge/GlobalMedia.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/surge/GlobalMedia.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/loon/GlobalMedia.list,policy=<policy>,tag=GlobalMedia,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/quantumult-x/GlobalMedia.list, tag=GlobalMedia, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/egern/GlobalMedia.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/shadowrocket/GlobalMedia.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "GlobalMedia",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/sing-box/GlobalMedia.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "GlobalMedia",
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

#### GlobalMedia.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/surge/GlobalMedia.list
```

#### GlobalMedia.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/surge/GlobalMedia.domainset
```

### Loon

#### GlobalMedia.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGlobalMedia%2Floon%2FGlobalMedia.list)


### Quantumult X

#### GlobalMedia.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGlobalMedia%2Fquantumult-x%2FGlobalMedia.list%2C%20tag%3DGlobalMedia%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### GlobalMedia.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGlobalMedia%2Fegern%2FGlobalMedia.yaml)


### Shadowrocket

#### GlobalMedia.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/shadowrocket/GlobalMedia.list
```

### sing-box

#### GlobalMedia.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/sing-box/GlobalMedia.srs
```

## Artifacts

### mrs(ipcidr)

#### GlobalMedia_IP.mrs

GitHub: [GlobalMedia_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/mihomo/GlobalMedia_IP.mrs)
Text: [GlobalMedia_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/mihomo/GlobalMedia_IP.txt)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/mihomo/GlobalMedia_IP.mrs
```

### mrs(domain)

#### GlobalMedia_Domain.mrs

GitHub: [GlobalMedia_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/mihomo/GlobalMedia_Domain.mrs)
Text: [GlobalMedia_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/mihomo/GlobalMedia_Domain.txt)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/mihomo/GlobalMedia_Domain.mrs
```

### yaml(remaining)

#### GlobalMedia.yaml

GitHub: [GlobalMedia.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/mihomo/GlobalMedia.yaml)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/mihomo/GlobalMedia.yaml
```

### Surge

#### GlobalMedia.list

GitHub: [GlobalMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/surge/GlobalMedia.list)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/surge/GlobalMedia.list
```

#### GlobalMedia.domainset

GitHub: [GlobalMedia.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/surge/GlobalMedia.domainset)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/surge/GlobalMedia.domainset
```

### Loon

#### GlobalMedia.list

GitHub: [GlobalMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/loon/GlobalMedia.list)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/loon/GlobalMedia.list
```

### Quantumult X

#### GlobalMedia.list

GitHub: [GlobalMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/quantumult-x/GlobalMedia.list)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/quantumult-x/GlobalMedia.list
```

### Egern

#### GlobalMedia.yaml

GitHub: [GlobalMedia.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/egern/GlobalMedia.yaml)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/egern/GlobalMedia.yaml
```

### Shadowrocket

#### GlobalMedia.list

GitHub: [GlobalMedia.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/shadowrocket/GlobalMedia.list)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/shadowrocket/GlobalMedia.list
```

### sing-box

#### GlobalMedia.json

GitHub: [GlobalMedia.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/sing-box/GlobalMedia.json)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/sing-box/GlobalMedia.json
```

#### GlobalMedia.srs

GitHub: [GlobalMedia.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/sing-box/GlobalMedia.srs)
Source: [GlobalMedia.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GlobalMedia/GlobalMedia.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GlobalMedia/sing-box/GlobalMedia.srs
```
