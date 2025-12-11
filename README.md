## 自用

diy-direct:
https://raw.githubusercontent.com/haha12358/DIY-rules/refs/heads/main/diy-direct.yaml

diy-proxy:
https://raw.githubusercontent.com/haha12358/DIY-rules/refs/heads/main/diy-proxy.yaml

广告:
https://raw.githubusercontent.com/217heidai/adblockfilters/main/rules/adblockmihomo.yaml

## 查询用

直连域名列表:
https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/direct.txt

代理域名列表:
https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/proxy.txt

## 使用方法

```yaml
rule-providers:
  reject:
    type: http
    behavior: domain
    url: "https://raw.githubusercontent.com/217heidai/adblockfilters/main/rules/adblockmihomo.yaml"
    path: ./ruleset/reject.yaml

  diy-direct:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/haha12358/DIY-rules/refs/heads/main/diy-direct.yaml"
    path: ./ruleset/diy-direct.yaml

  diy-proxy:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/haha12358/DIY-rules/refs/heads/main/diy-proxy.yaml"
    path: ./ruleset/diy-proxy.yaml

  # 可选
  proxy:
    type: http
    behavior: domain
    url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/proxy.txt"
    path: ./ruleset/proxy.yaml
    interval: 86400

  # 可选
  direct:
    type: http
    behavior: domain
    url: "https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/direct.txt"
    path: ./ruleset/direct.yaml
    interval: 86400
```

```yaml
rules:
  - 'RULE-SET,reject,REJECT'
  - 'RULE-SET,diy-direct,DIRECT'
  - 'RULE-SET,diy-proxy,♻️ 手动切换'  # "♻️ 手动切换"需修改
  # ...(原来的规则)
```
