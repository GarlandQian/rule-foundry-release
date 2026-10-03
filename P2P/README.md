# P2P

Source config: [P2P.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/P2P/P2P.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| STUN | STUN | true | http | classical | yaml | rules |  | [STUN.yaml](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/STUN/STUN.yaml) |  |  |
| huya | huya | true | http | classical | text | rules |  | [Simple_Reject_Rule.list](https://gist.githubusercontent.com/sec7et/0c17021dec65107ff099e6a638a20d52/raw/Simple_Reject_Rule.list) |  |  |
| WebRTC | WebRTC | true | http | classical | text | rules |  | [WebRTC.list](https://raw.githubusercontent.com/GitMetaio/Surfing/refs/heads/rm/Home/rules/WebRTC.list) |  |  |
| P2P | P2P | true | inline | classical | yaml | rules |  |  |  | [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml) |

## Mihomo Config

```yaml
proxy-groups:
  - name: "P2P"
    type: select
    proxies: []
rules:
  - RULE-SET,P2P_Domain,P2P
  - RULE-SET,P2P,P2P,no-resolve
  - RULE-SET,P2P_IP,P2P,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  P2P_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/mihomo/P2P_Domain.mrs }
  P2P: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/mihomo/P2P.yaml }
  P2P_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/mihomo/P2P_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/surge/P2P.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/surge/P2P.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/loon/P2P.list,policy=<policy>,tag=P2P,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/quantumult-x/P2P.list, tag=P2P, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/egern/P2P.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/shadowrocket/P2P.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "P2P",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/sing-box/P2P.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "P2P",
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

#### P2P.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/surge/P2P.list
```

#### P2P.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/surge/P2P.domainset
```

### Loon

#### P2P.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FP2P%2Floon%2FP2P.list)


### Quantumult X

#### P2P.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FP2P%2Fquantumult-x%2FP2P.list%2C%20tag%3DP2P%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### P2P.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FP2P%2Fegern%2FP2P.yaml)


### Shadowrocket

#### P2P.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/shadowrocket/P2P.list
```

### sing-box

#### P2P.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/sing-box/P2P.srs
```

## Artifacts

### mrs(ipcidr)

#### P2P_IP.mrs

GitHub: [P2P_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/mihomo/P2P_IP.mrs)
Text: [P2P_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/mihomo/P2P_IP.txt)
Source: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/mihomo/P2P_IP.mrs
```

### mrs(domain)

#### P2P_Domain.mrs

GitHub: [P2P_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/mihomo/P2P_Domain.mrs)
Text: [P2P_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/mihomo/P2P_Domain.txt)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/mihomo/P2P_Domain.mrs
```

### yaml(remaining)

#### P2P.yaml

GitHub: [P2P.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/mihomo/P2P.yaml)
Sources: [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/mihomo/P2P.yaml
```

### Surge

#### P2P.list

GitHub: [P2P.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/surge/P2P.list)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/surge/P2P.list
```

#### P2P.domainset

GitHub: [P2P.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/surge/P2P.domainset)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/surge/P2P.domainset
```

### Loon

#### P2P.list

GitHub: [P2P.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/loon/P2P.list)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/loon/P2P.list
```

### Quantumult X

#### P2P.list

GitHub: [P2P.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/quantumult-x/P2P.list)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/quantumult-x/P2P.list
```

### Egern

#### P2P.yaml

GitHub: [P2P.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/egern/P2P.yaml)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/egern/P2P.yaml
```

### Shadowrocket

#### P2P.list

GitHub: [P2P.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/shadowrocket/P2P.list)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/shadowrocket/P2P.list
```

### sing-box

#### P2P.json

GitHub: [P2P.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/sing-box/P2P.json)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/sing-box/P2P.json
```

#### P2P.srs

GitHub: [P2P.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/sing-box/P2P.srs)
Sources: [STUN.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/STUN.original.yaml), [huya.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/huya.original.list), [WebRTC.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/WebRTC.original.list), [P2P.original.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/P2P/P2P.original.yaml)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/P2P/sing-box/P2P.srs
```
