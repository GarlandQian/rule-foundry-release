# FakeIPFilter

Source config: [FakeIPFilter.yaml](https://github.com/GarlandQian/rule-foundry/blob/main/source/FakeIPFilter/FakeIPFilter.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| FakeIPFilter | Fake IP filter rules from QuixoticHeart/rule-set | true | http | classical | text | fake-ip-filter |  | [fake-ip-filter.list](https://raw.githubusercontent.com/QuixoticHeart/rule-set/ruleset/meta/domain/fake-ip-filter.list) |  |  |

## Mihomo Config

```yaml
dns:
  # other fields
  fake-ip-filter-mode: blacklist
  fake-ip-filter:
    - "rule-set:FakeIPFilter_Domain"
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
rule-providers:
  FakeIPFilter_Domain: { <<: *domain, url: https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/FakeIPFilter/mihomo/FakeIPFilter_Domain.mrs }
```

## Artifacts

### mrs(domain)

#### FakeIPFilter_Domain.mrs

GitHub: [FakeIPFilter_Domain.mrs](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/mihomo/FakeIPFilter_Domain.mrs)
Text: [FakeIPFilter_Domain.txt](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/mihomo/FakeIPFilter_Domain.txt)
Source: [FakeIPFilter.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/FakeIPFilter.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/FakeIPFilter/mihomo/FakeIPFilter_Domain.mrs
```

### sing-box

#### FakeIPFilter.json

GitHub: [FakeIPFilter.json](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/sing-box/FakeIPFilter.json)
Source: [FakeIPFilter.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/FakeIPFilter.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/FakeIPFilter/sing-box/FakeIPFilter.json
```

#### FakeIPFilter.srs

GitHub: [FakeIPFilter.srs](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/sing-box/FakeIPFilter.srs)
Source: [FakeIPFilter.original.list](https://github.com/GarlandQian/rule-foundry-release/blob/release/FakeIPFilter/FakeIPFilter.original.list)

```text
https://raw.githubusercontent.com/GarlandQian/rule-foundry-release/release/FakeIPFilter/sing-box/FakeIPFilter.srs
```
