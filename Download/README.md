# Download

Source config: [Download.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Download/Download.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Download | Download | true | http | classical | yaml | rules |  | [Download.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Download/Download.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Download"
    type: select
    proxies: []
rules:
  - RULE-SET,Download_Domain,Download
  - RULE-SET,Download,Download,no-resolve
  - RULE-SET,Download_IP,Download,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Download_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/mihomo/Download_Domain.mrs }
  Download: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/mihomo/Download.yaml }
  Download_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/mihomo/Download_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/surge/Download.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/surge/Download.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/loon/Download.list,policy=<policy>,tag=Download,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/quantumult-x/Download.list, tag=Download, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/egern/Download.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/shadowrocket/Download.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Download",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/sing-box/Download.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Download",
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

#### Download.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/surge/Download.list
```

#### Download.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/surge/Download.domainset
```

### Loon

#### Download.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDownload%2Floon%2FDownload.list)


### Quantumult X

#### Download.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDownload%2Fquantumult-x%2FDownload.list%2C%20tag%3DDownload%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Download.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FDownload%2Fegern%2FDownload.yaml)


### Shadowrocket

#### Download.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/shadowrocket/Download.list
```

### sing-box

#### Download.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/sing-box/Download.srs
```

## Artifacts

### mrs(ipcidr)

#### Download_IP.mrs

GitHub: [Download_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/mihomo/Download_IP.mrs)
Text: [Download_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/mihomo/Download_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/mihomo/Download_IP.mrs
```

### mrs(domain)

#### Download_Domain.mrs

GitHub: [Download_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/mihomo/Download_Domain.mrs)
Text: [Download_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/mihomo/Download_Domain.txt)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/mihomo/Download_Domain.mrs
```

### yaml(remaining)

#### Download.yaml

GitHub: [Download.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/mihomo/Download.yaml)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/mihomo/Download.yaml
```

### Surge

#### Download.list

GitHub: [Download.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/surge/Download.list)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/surge/Download.list
```

#### Download.domainset

GitHub: [Download.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/surge/Download.domainset)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/surge/Download.domainset
```

### Loon

#### Download.list

GitHub: [Download.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/loon/Download.list)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/loon/Download.list
```

### Quantumult X

#### Download.list

GitHub: [Download.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/quantumult-x/Download.list)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/quantumult-x/Download.list
```

### Egern

#### Download.yaml

GitHub: [Download.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/egern/Download.yaml)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/egern/Download.yaml
```

### Shadowrocket

#### Download.list

GitHub: [Download.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/shadowrocket/Download.list)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/shadowrocket/Download.list
```

### sing-box

#### Download.json

GitHub: [Download.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/sing-box/Download.json)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/sing-box/Download.json
```

#### Download.srs

GitHub: [Download.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/sing-box/Download.srs)
Source: [Download.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Download/Download.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Download/sing-box/Download.srs
```
