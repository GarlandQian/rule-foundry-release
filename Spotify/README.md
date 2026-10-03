# Spotify

Source config: [Spotify.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/Spotify/Spotify.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| Spotify | Spotify rules from QuixoticHeart/rule-set | true | http | classical | text | rules |  | [spotify.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/spotify.list) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "Spotify"
    type: select
    proxies: []
rules:
  - RULE-SET,Spotify_Domain,Spotify
  - RULE-SET,Spotify,Spotify,no-resolve
  - RULE-SET,Spotify_IP,Spotify,no-resolve
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  Spotify_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/mihomo/Spotify_Domain.mrs }
  Spotify: { <<: *yaml, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/mihomo/Spotify.yaml }
  Spotify_IP: { <<: *ip, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/mihomo/Spotify_IP.mrs }
```

## Client Configs

### Surge



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/surge/Spotify.list,<policy>
# DOMAIN-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/surge/Spotify.domainset,<policy>
```

### Loon



```ini
[Remote Rule]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/loon/Spotify.list,policy=<policy>,tag=Spotify,enabled=true
```

### Quantumult X



```ini
[filter_remote]
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/quantumult-x/Spotify.list, tag=Spotify, force-policy=<policy>, enabled=true
```

### Egern



```yaml
rules:
  - rule_set:
      match: "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/egern/Spotify.yaml"
      policy: <policy>
      update_interval: 86400
```

### Shadowrocket



```ini
[Rule]
RULE-SET,https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/shadowrocket/Spotify.list,<policy>
```

### sing-box



```json
{
  "route": {
    "rule_set": [
      {
        "type": "remote",
        "tag": "Spotify",
        "format": "binary",
        "url": "https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/sing-box/Spotify.srs",
        "http_client": "<http-client>",
        "update_interval": "1d"
      }
    ],
    "rules": [
      {
        "rule_set": "Spotify",
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

#### Spotify.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/surge/Spotify.list
```

#### Spotify.domainset

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/surge/Spotify.domainset
```

### Loon

#### Spotify.list

Universal Link: [Open](https://www.nsloon.com/openloon/import?rules=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSpotify%2Floon%2FSpotify.list)


### Quantumult X

#### Spotify.list

Universal Link: [Open](https://quantumult.app/x/open-app/add-resource?remote-resource=%7B%22filter_remote%22%3A%5B%22https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSpotify%2Fquantumult-x%2FSpotify.list%2C%20tag%3DSpotify%2C%20force-policy%3D%3Cpolicy%3E%2C%20enabled%3Dtrue%22%5D%7D)


### Egern

#### Spotify.yaml

Universal Link: [Open](https://egernapp.com/rules/new/?type=rule_set&match=https%3A%2F%2Fraw.githubusercontent.com%2FGarlandQian%2Frule-foundry-release%2Frelease%2FSpotify%2Fegern%2FSpotify.yaml)


### Shadowrocket

#### Spotify.list

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/shadowrocket/Spotify.list
```

### sing-box

#### Spotify.srs

Copy URL:

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/sing-box/Spotify.srs
```

## Artifacts

### mrs(ipcidr)

#### Spotify_IP.mrs

GitHub: [Spotify_IP.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/mihomo/Spotify_IP.mrs)
Text: [Spotify_IP.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/mihomo/Spotify_IP.txt)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/mihomo/Spotify_IP.mrs
```

### mrs(domain)

#### Spotify_Domain.mrs

GitHub: [Spotify_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/mihomo/Spotify_Domain.mrs)
Text: [Spotify_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/mihomo/Spotify_Domain.txt)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/mihomo/Spotify_Domain.mrs
```

### yaml(remaining)

#### Spotify.yaml

GitHub: [Spotify.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/mihomo/Spotify.yaml)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/mihomo/Spotify.yaml
```

### Surge

#### Spotify.list

GitHub: [Spotify.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/surge/Spotify.list)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/surge/Spotify.list
```

#### Spotify.domainset

GitHub: [Spotify.domainset](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/surge/Spotify.domainset)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/surge/Spotify.domainset
```

### Loon

#### Spotify.list

GitHub: [Spotify.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/loon/Spotify.list)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/loon/Spotify.list
```

### Quantumult X

#### Spotify.list

GitHub: [Spotify.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/quantumult-x/Spotify.list)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/quantumult-x/Spotify.list
```

### Egern

#### Spotify.yaml

GitHub: [Spotify.yaml](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/egern/Spotify.yaml)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/egern/Spotify.yaml
```

### Shadowrocket

#### Spotify.list

GitHub: [Spotify.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/shadowrocket/Spotify.list)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/shadowrocket/Spotify.list
```

### sing-box

#### Spotify.json

GitHub: [Spotify.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/sing-box/Spotify.json)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/sing-box/Spotify.json
```

#### Spotify.srs

GitHub: [Spotify.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/sing-box/Spotify.srs)
Source: [Spotify.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/Spotify/Spotify.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/Spotify/sing-box/Spotify.srs
```
