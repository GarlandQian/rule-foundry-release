# Game

Source config: [Game.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Game/Game.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Game | Game rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [games.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/games.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Game"
    type: select
    proxies: []
rules:
  - RULE-SET,Game_Domain,Game
  - RULE-SET,Game,Game,no-resolve
  - RULE-SET,Game_IP,Game,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Game_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/mihomo/Game_Domain.mrs }
  Game: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/mihomo/Game.yaml }
  Game_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/mihomo/Game_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/surge/Game.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/surge/Game.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/loon/Game.list,policy=<policy>,tag=Game,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/quantumult-x/Game.list, tag=Game, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/egern/Game.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/shadowrocket/Game.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Game",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/sing-box/Game.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Game",
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

#### Game.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/surge/Game.list
```

#### Game.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/surge/Game.domainset
```

### Loon

#### Game.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGame%2Floon%2FGame.list)


### Quantumult X

#### Game.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGame%2Fquantumult-x%2FGame.list%2C%20tag%3DGame%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Game.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FGame%2Fegern%2FGame.yaml)


### Shadowrocket

#### Game.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/shadowrocket/Game.list
```

### sing-box

#### Game.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/sing-box/Game.srs
```

## Artifacts

### mrs(ipcidr)

#### Game_IP.mrs

GitHub: [Game_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/mihomo/Game_IP.mrs)
Text: [Game_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/mihomo/Game_IP.txt)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/mihomo/Game_IP.mrs
```

### mrs(domain)

#### Game_Domain.mrs

GitHub: [Game_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/mihomo/Game_Domain.mrs)
Text: [Game_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/mihomo/Game_Domain.txt)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/mihomo/Game_Domain.mrs
```

### yaml(remaining)

#### Game.yaml

GitHub: [Game.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/mihomo/Game.yaml)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/mihomo/Game.yaml
```

### Surge

#### Game.list

GitHub: [Game.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/surge/Game.list)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/surge/Game.list
```

#### Game.domainset

GitHub: [Game.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/surge/Game.domainset)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/surge/Game.domainset
```

### Loon

#### Game.list

GitHub: [Game.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/loon/Game.list)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/loon/Game.list
```

### Quantumult X

#### Game.list

GitHub: [Game.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/quantumult-x/Game.list)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/quantumult-x/Game.list
```

### Egern

#### Game.yaml

GitHub: [Game.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/egern/Game.yaml)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/egern/Game.yaml
```

### Shadowrocket

#### Game.list

GitHub: [Game.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/shadowrocket/Game.list)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/shadowrocket/Game.list
```

### sing-box

#### Game.json

GitHub: [Game.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/sing-box/Game.json)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/sing-box/Game.json
```

#### Game.srs

GitHub: [Game.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/sing-box/Game.srs)
Source: [Game.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Game/Game.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Game/sing-box/Game.srs
```
