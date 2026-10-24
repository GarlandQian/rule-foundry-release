# Facebook

Source config: [Facebook.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Facebook/Facebook.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Facebook | Facebook from blackmatrix7/ios_rule_script | true | http | classical | yaml | rules |  | [Facebook.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Facebook/Facebook.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Facebook"
    type: select
    proxies: []
rules:
  - RULE-SET,Facebook_Domain,Facebook
  - RULE-SET,Facebook,Facebook,no-resolve
  - RULE-SET,Facebook_IP,Facebook,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Facebook_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/mihomo/Facebook_Domain.mrs }
  Facebook: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/mihomo/Facebook.yaml }
  Facebook_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/mihomo/Facebook_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/surge/Facebook.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/surge/Facebook.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/loon/Facebook.list,policy=<policy>,tag=Facebook,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/quantumult-x/Facebook.list, tag=Facebook, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/egern/Facebook.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/shadowrocket/Facebook.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Facebook",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/sing-box/Facebook.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Facebook",
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

#### Facebook.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/surge/Facebook.list
```

#### Facebook.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/surge/Facebook.domainset
```

### Loon

#### Facebook.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FFacebook%2Floon%2FFacebook.list)


### Quantumult X

#### Facebook.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FFacebook%2Fquantumult-x%2FFacebook.list%2C%20tag%3DFacebook%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Facebook.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FFacebook%2Fegern%2FFacebook.yaml)


### Shadowrocket

#### Facebook.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/shadowrocket/Facebook.list
```

### sing-box

#### Facebook.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/sing-box/Facebook.srs
```

## Artifacts

### mrs(ipcidr)

#### Facebook_IP.mrs

GitHub: [Facebook_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/mihomo/Facebook_IP.mrs)
Text: [Facebook_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/mihomo/Facebook_IP.txt)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/mihomo/Facebook_IP.mrs
```

### mrs(domain)

#### Facebook_Domain.mrs

GitHub: [Facebook_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/mihomo/Facebook_Domain.mrs)
Text: [Facebook_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/mihomo/Facebook_Domain.txt)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/mihomo/Facebook_Domain.mrs
```

### yaml(remaining)

#### Facebook.yaml

GitHub: [Facebook.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/mihomo/Facebook.yaml)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/mihomo/Facebook.yaml
```

### Surge

#### Facebook.list

GitHub: [Facebook.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/surge/Facebook.list)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/surge/Facebook.list
```

#### Facebook.domainset

GitHub: [Facebook.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/surge/Facebook.domainset)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/surge/Facebook.domainset
```

### Loon

#### Facebook.list

GitHub: [Facebook.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/loon/Facebook.list)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/loon/Facebook.list
```

### Quantumult X

#### Facebook.list

GitHub: [Facebook.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/quantumult-x/Facebook.list)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/quantumult-x/Facebook.list
```

### Egern

#### Facebook.yaml

GitHub: [Facebook.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/egern/Facebook.yaml)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/egern/Facebook.yaml
```

### Shadowrocket

#### Facebook.list

GitHub: [Facebook.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/shadowrocket/Facebook.list)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/shadowrocket/Facebook.list
```

### sing-box

#### Facebook.json

GitHub: [Facebook.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/sing-box/Facebook.json)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/sing-box/Facebook.json
```

#### Facebook.srs

GitHub: [Facebook.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/sing-box/Facebook.srs)
Source: [Facebook.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Facebook/Facebook.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Facebook/sing-box/Facebook.srs
```
