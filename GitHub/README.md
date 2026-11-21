# GitHub

Source config: [GitHub.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/GitHub/GitHub.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| GitHub | GitHub-specific rules from MagicRule | true | magicrule | classical | yaml | rules |  | [magicrule.pages.dev](https://magicrule.pages.dev/#/c/Mihomo/r/0d72ebdc-b43a-4720-8079-060a946a059f) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "GitHub"
    type: select
    proxies: []
rules:
  - RULE-SET,GitHub_Domain,GitHub
  - RULE-SET,GitHub,GitHub,no-resolve
  - RULE-SET,GitHub_IP,GitHub,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  GitHub_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/mihomo/GitHub_Domain.mrs }
  GitHub: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/mihomo/GitHub.yaml }
  GitHub_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/mihomo/GitHub_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/surge/GitHub.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/surge/GitHub.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/loon/GitHub.list,policy=<policy>,tag=GitHub,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/quantumult-x/GitHub.list, tag=GitHub, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/egern/GitHub.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/shadowrocket/GitHub.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "GitHub",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/sing-box/GitHub.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "GitHub",
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

#### GitHub.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/surge/GitHub.list
```

#### GitHub.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/surge/GitHub.domainset
```

### Loon

#### GitHub.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGitHub%2Floon%2FGitHub.list)


### Quantumult X

#### GitHub.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGitHub%2Fquantumult-x%2FGitHub.list%2C%20tag%3DGitHub%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### GitHub.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGitHub%2Fegern%2FGitHub.yaml)


### Shadowrocket

#### GitHub.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/shadowrocket/GitHub.list
```

### sing-box

#### GitHub.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/sing-box/GitHub.srs
```

## Artifacts

### mrs(ipcidr)

#### GitHub_IP.mrs

GitHub: [GitHub_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/mihomo/GitHub_IP.mrs)
Text: [GitHub_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/mihomo/GitHub_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/mihomo/GitHub_IP.mrs
```

### mrs(domain)

#### GitHub_Domain.mrs

GitHub: [GitHub_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/mihomo/GitHub_Domain.mrs)
Text: [GitHub_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/mihomo/GitHub_Domain.txt)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/mihomo/GitHub_Domain.mrs
```

### yaml(remaining)

#### GitHub.yaml

GitHub: [GitHub.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/mihomo/GitHub.yaml)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/mihomo/GitHub.yaml
```

### Surge

#### GitHub.list

GitHub: [GitHub.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/surge/GitHub.list)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/surge/GitHub.list
```

#### GitHub.domainset

GitHub: [GitHub.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/surge/GitHub.domainset)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/surge/GitHub.domainset
```

### Loon

#### GitHub.list

GitHub: [GitHub.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/loon/GitHub.list)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/loon/GitHub.list
```

### Quantumult X

#### GitHub.list

GitHub: [GitHub.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/quantumult-x/GitHub.list)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/quantumult-x/GitHub.list
```

### Egern

#### GitHub.yaml

GitHub: [GitHub.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/egern/GitHub.yaml)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/egern/GitHub.yaml
```

### Shadowrocket

#### GitHub.list

GitHub: [GitHub.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/shadowrocket/GitHub.list)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/shadowrocket/GitHub.list
```

### sing-box

#### GitHub.json

GitHub: [GitHub.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/sing-box/GitHub.json)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/sing-box/GitHub.json
```

#### GitHub.srs

GitHub: [GitHub.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/sing-box/GitHub.srs)
Source: [GitHub.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/GitHub/GitHub.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/GitHub/sing-box/GitHub.srs
```
