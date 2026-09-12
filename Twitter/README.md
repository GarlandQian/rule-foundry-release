# Twitter

Source config: [Twitter.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Twitter/Twitter.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Twitter | Twitter | true | http | classical | yaml | rules |  | [Twitter.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Twitter/Twitter.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Twitter"
    type: select
    proxies: []
rules:
  - RULE-SET,Twitter_Domain,Twitter
  - RULE-SET,Twitter,Twitter,no-resolve
  - RULE-SET,Twitter_IP,Twitter,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Twitter_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/mihomo/Twitter_Domain.mrs }
  Twitter: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/mihomo/Twitter.yaml }
  Twitter_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/mihomo/Twitter_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/surge/Twitter.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/surge/Twitter.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/loon/Twitter.list,policy=<policy>,tag=Twitter,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/quantumult-x/Twitter.list, tag=Twitter, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/egern/Twitter.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/shadowrocket/Twitter.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Twitter",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/sing-box/Twitter.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Twitter",
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

#### Twitter.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/surge/Twitter.list
```

#### Twitter.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/surge/Twitter.domainset
```

### Loon

#### Twitter.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTwitter%2Floon%2FTwitter.list)


### Quantumult X

#### Twitter.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTwitter%2Fquantumult-x%2FTwitter.list%2C%20tag%3DTwitter%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Twitter.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FTwitter%2Fegern%2FTwitter.yaml)


### Shadowrocket

#### Twitter.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/shadowrocket/Twitter.list
```

### sing-box

#### Twitter.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/sing-box/Twitter.srs
```

## Artifacts

### mrs(ipcidr)

#### Twitter_IP.mrs

GitHub: [Twitter_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/mihomo/Twitter_IP.mrs)
Text: [Twitter_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/mihomo/Twitter_IP.txt)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/mihomo/Twitter_IP.mrs
```

### mrs(domain)

#### Twitter_Domain.mrs

GitHub: [Twitter_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/mihomo/Twitter_Domain.mrs)
Text: [Twitter_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/mihomo/Twitter_Domain.txt)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/mihomo/Twitter_Domain.mrs
```

### yaml(remaining)

#### Twitter.yaml

GitHub: [Twitter.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/mihomo/Twitter.yaml)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/mihomo/Twitter.yaml
```

### Surge

#### Twitter.list

GitHub: [Twitter.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/surge/Twitter.list)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/surge/Twitter.list
```

#### Twitter.domainset

GitHub: [Twitter.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/surge/Twitter.domainset)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/surge/Twitter.domainset
```

### Loon

#### Twitter.list

GitHub: [Twitter.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/loon/Twitter.list)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/loon/Twitter.list
```

### Quantumult X

#### Twitter.list

GitHub: [Twitter.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/quantumult-x/Twitter.list)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/quantumult-x/Twitter.list
```

### Egern

#### Twitter.yaml

GitHub: [Twitter.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/egern/Twitter.yaml)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/egern/Twitter.yaml
```

### Shadowrocket

#### Twitter.list

GitHub: [Twitter.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/shadowrocket/Twitter.list)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/shadowrocket/Twitter.list
```

### sing-box

#### Twitter.json

GitHub: [Twitter.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/sing-box/Twitter.json)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/sing-box/Twitter.json
```

#### Twitter.srs

GitHub: [Twitter.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/sing-box/Twitter.srs)
Source: [Twitter.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Twitter/Twitter.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Twitter/sing-box/Twitter.srs
```
