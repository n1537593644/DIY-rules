基于 [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) 的自用补充规则

---

## 使用方式
[config](https://github.com/haha12358/DIY-rules/blob/main/config.yaml)
```yaml
rule-anchor:
  mrs: &mrs {type: http, interval: 86400, behavior: domain, format: mrs}
  domain: &domain {type: http, interval: 86400, behavior: domain, format: yaml}
  ip: &ip {type: http, interval: 86400, behavior: ipcidr, format: yaml}
  class: &class {type: http, interval: 86400, behavior: classical, format: yaml}

rule-providers:
  reject: {<<: *mrs, url: "https://raw.githubusercontent.com/217heidai/adblockfilters/main/rules/adblockmihomo.mrs"}
  fakeipfilter: {<<: *mrs, url: "https://raw.githubusercontent.com/wwqgtxx/clash-rules/release/fakeip-filter.mrs"}
  
  icloud: {<<: *domain, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/icloud.txt"}
  apple: {<<: *domain, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/apple.txt"}
  google: {<<: *domain, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/google.txt"}
  proxy: {<<: *domain, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/proxy.txt"}
  direct: {<<: *domain, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/direct.txt"}
  private: {<<: *domain, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/private.txt"}

  telegramcidr: {<<: *ip, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/telegramcidr.txt"}
  cncidr: {<<: *ip, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/cncidr.txt"}
  lancidr: {<<: *ip, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/lancidr.txt"}

  applications: {<<: *class, url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/applications.txt"}
  diy-direct: {<<: *class, url: "https://raw.githubusercontent.com/haha12358/DIY-rules/refs/heads/main/diy-direct.yaml"}
  diy-proxy: {<<: *class, url: "https://raw.githubusercontent.com/haha12358/DIY-rules/refs/heads/main/diy-proxy.yaml"}
```

```yaml
rules:
  - RULE-SET,applications,➡️ 直连
  - DOMAIN,clash.razord.top,➡️ 直连
  - DOMAIN,yacd.haishan.me,➡️ 直连

  - RULE-SET,private,➡️ 直连
  - RULE-SET,reject,🚫 广告

  - RULE-SET,diy-direct,➡️ 直连
  - RULE-SET,diy-proxy,🚀 默认

  - RULE-SET,icloud,➡️ 直连
  - RULE-SET,apple,➡️ 直连
  - RULE-SET,google,🚀 默认

  - RULE-SET,proxy,🚀 默认
  - RULE-SET,direct,➡️ 直连

  - RULE-SET,lancidr,🏠 局域网,no-resolve
  - RULE-SET,telegramcidr,🚀 默认,no-resolve
  - RULE-SET,cncidr,➡️ 直连

  - GEOIP,CN,➡️ 直连

  - MATCH,🐟️ 漏网之鱼
```
