# Google

Source config: [Google.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Google/Google.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Google | Google rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [google.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/google.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Google"
    type: select
    proxies: []
rules:
  - RULE-SET,Google_Domain,Google
  - RULE-SET,Google,Google,no-resolve
  - RULE-SET,Google_IP,Google,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Google_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/mihomo/Google_Domain.mrs }
  Google: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/mihomo/Google.yaml }
  Google_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/mihomo/Google_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/surge/Google.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/surge/Google.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/loon/Google.list,policy=<policy>,tag=Google,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/quantumult-x/Google.list, tag=Google, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/egern/Google.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/shadowrocket/Google.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Google",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/sing-box/Google.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Google",
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

#### Google.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/surge/Google.list
```

#### Google.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/surge/Google.domainset
```

### Loon

#### Google.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGoogle%2Floon%2FGoogle.list)


### Quantumult X

#### Google.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGoogle%2Fquantumult-x%2FGoogle.list%2C%20tag%3DGoogle%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Google.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGoogle%2Fegern%2FGoogle.yaml)


### Shadowrocket

#### Google.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/shadowrocket/Google.list
```

### sing-box

#### Google.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/sing-box/Google.srs
```

## Artifacts

### mrs(ipcidr)

#### Google_IP.mrs

GitHub: [Google_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/mihomo/Google_IP.mrs)
Text: [Google_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/mihomo/Google_IP.txt)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/mihomo/Google_IP.mrs
```

### mrs(domain)

#### Google_Domain.mrs

GitHub: [Google_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/mihomo/Google_Domain.mrs)
Text: [Google_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/mihomo/Google_Domain.txt)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/mihomo/Google_Domain.mrs
```

### yaml(remaining)

#### Google.yaml

GitHub: [Google.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/mihomo/Google.yaml)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/mihomo/Google.yaml
```

### Surge

#### Google.list

GitHub: [Google.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/surge/Google.list)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/surge/Google.list
```

#### Google.domainset

GitHub: [Google.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/surge/Google.domainset)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/surge/Google.domainset
```

### Loon

#### Google.list

GitHub: [Google.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/loon/Google.list)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/loon/Google.list
```

### Quantumult X

#### Google.list

GitHub: [Google.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/quantumult-x/Google.list)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/quantumult-x/Google.list
```

### Egern

#### Google.yaml

GitHub: [Google.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/egern/Google.yaml)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/egern/Google.yaml
```

### Shadowrocket

#### Google.list

GitHub: [Google.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/shadowrocket/Google.list)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/shadowrocket/Google.list
```

### sing-box

#### Google.json

GitHub: [Google.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/sing-box/Google.json)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/sing-box/Google.json
```

#### Google.srs

GitHub: [Google.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/sing-box/Google.srs)
Source: [Google.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Google/Google.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Google/sing-box/Google.srs
```
