# Apple_AppStore

Source config: [Apple_AppStore.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Apple_AppStore/Apple_AppStore.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Apple_AppStore | Apple_AppStore | true | http | classical | yaml | rules |  | [AppStore.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/AppStore/AppStore.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Apple_AppStore"
    type: select
    proxies: []
rules:
  - RULE-SET,Apple_AppStore_Domain,Apple_AppStore
  - RULE-SET,Apple_AppStore,Apple_AppStore,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,Apple_AppStore_IP,Apple_AppStore,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Apple_AppStore_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/mihomo/Apple_AppStore_Domain.mrs }
  Apple_AppStore: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/mihomo/Apple_AppStore.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  Apple_AppStore_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/mihomo/Apple_AppStore_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/surge/Apple_AppStore.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/surge/Apple_AppStore.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/loon/Apple_AppStore.list,policy=<policy>,tag=Apple_AppStore,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/quantumult-x/Apple_AppStore.list, tag=Apple_AppStore, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/egern/Apple_AppStore.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/shadowrocket/Apple_AppStore.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Apple_AppStore",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/sing-box/Apple_AppStore.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Apple_AppStore",
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

#### Apple_AppStore.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/surge/Apple_AppStore.list
```

#### Apple_AppStore.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/surge/Apple_AppStore.domainset
```

### Loon

#### Apple_AppStore.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_AppStore%2Floon%2FApple_AppStore.list)


### Quantumult X

#### Apple_AppStore.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_AppStore%2Fquantumult-x%2FApple_AppStore.list%2C%20tag%3DApple_AppStore%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Apple_AppStore.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FApple_AppStore%2Fegern%2FApple_AppStore.yaml)


### Shadowrocket

#### Apple_AppStore.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/shadowrocket/Apple_AppStore.list
```

### sing-box

#### Apple_AppStore.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/sing-box/Apple_AppStore.srs
```

## Artifacts

### mrs(ipcidr)

#### Apple_AppStore_IP.mrs

GitHub: [Apple_AppStore_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/mihomo/Apple_AppStore_IP.mrs)
Text: [Apple_AppStore_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/mihomo/Apple_AppStore_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/mihomo/Apple_AppStore_IP.mrs
```

### mrs(domain)

#### Apple_AppStore_Domain.mrs

GitHub: [Apple_AppStore_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/mihomo/Apple_AppStore_Domain.mrs)
Text: [Apple_AppStore_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/mihomo/Apple_AppStore_Domain.txt)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/mihomo/Apple_AppStore_Domain.mrs
```

### yaml(remaining)

#### Apple_AppStore.yaml

GitHub: [Apple_AppStore.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/mihomo/Apple_AppStore.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/mihomo/Apple_AppStore.yaml
```

### Surge

#### Apple_AppStore.list

GitHub: [Apple_AppStore.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/surge/Apple_AppStore.list)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/surge/Apple_AppStore.list
```

#### Apple_AppStore.domainset

GitHub: [Apple_AppStore.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/surge/Apple_AppStore.domainset)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/surge/Apple_AppStore.domainset
```

### Loon

#### Apple_AppStore.list

GitHub: [Apple_AppStore.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/loon/Apple_AppStore.list)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/loon/Apple_AppStore.list
```

### Quantumult X

#### Apple_AppStore.list

GitHub: [Apple_AppStore.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/quantumult-x/Apple_AppStore.list)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/quantumult-x/Apple_AppStore.list
```

### Egern

#### Apple_AppStore.yaml

GitHub: [Apple_AppStore.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/egern/Apple_AppStore.yaml)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/egern/Apple_AppStore.yaml
```

### Shadowrocket

#### Apple_AppStore.list

GitHub: [Apple_AppStore.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/shadowrocket/Apple_AppStore.list)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/shadowrocket/Apple_AppStore.list
```

### sing-box

#### Apple_AppStore.json

GitHub: [Apple_AppStore.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/sing-box/Apple_AppStore.json)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/sing-box/Apple_AppStore.json
```

#### Apple_AppStore.srs

GitHub: [Apple_AppStore.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/sing-box/Apple_AppStore.srs)
Source: [Apple_AppStore.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Apple_AppStore/Apple_AppStore.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Apple_AppStore/sing-box/Apple_AppStore.srs
```
