# 🧩 Nikki 配置模板

个人使用的 **Nikki / Loon 配置模板**，专为追求精简、高效、易维护的用户设计  
适用于 **OpenClash / Clash Meta / MetaCubeX / Nikki / Clash mi** 等 `mihomo` 内核代理客户端 以及 **Loon**

---

## 📦 项目描述

本项目提供了完整的代理配置框架，具备以下特点：

- ✨ 精简且常用的规则集，满足主流使用场景
- ❌ 详尽的广告拦截规则 - [anti-AD](https://github.com/privacy-protection-tools/anti-AD?tab=readme-ov-file) & [AdRules](https://github.com/Cats-Team/AdRules/tree/main?tab=readme-ov-file)

- 🔧 支持 GEO 数据库远程下载，更新更便捷
- 📦 配置文件结构清晰，注释详尽，方便自定义扩展
- 📁 rule-providers 以 `.mrs` 格式为主，更快、内存占用更低
- 🎨 支持图标美化

---

## 📌 快速开始

1. 下载载配置文件：`mihomo_BS_Template.yml` 

2. 修改 `订阅地址` `机场名称`
```
proxy-providers:
  机场名称:
    <<: *proxy-providers-general                          # 引用上文的yaml锚点
    url: '订阅链接'
    override:                                             # 可选，覆写设置
      additional-prefix: 'ik|'                            # 可选，给订阅添加前缀
    #path: ./providers/proxy/proxy-provider1.yaml         # 可选，指定下载路径
  # provider2:

# 代理组设置
use-all-proxy-providers: &use-all-proxy-providers         # 代理组通用配置
  use:
    - 机场名称
    # - provider2:
```
> 非linux系统请注释或删除 `redir-port: 7892` `tproxy-port: 7894` 如 **clash mi** 客户端 


3.  将 `mihomo_BS_Template.yml` 导入 Clash 客户端（如 **Clash Verge、Clash Meta for Android**）。
4.  按照注释提示，根据实际使用软件调整。
5.  (可选) `nikki.txt` 为 Nikki 程序配置文件，路径 `/etc/config/`。



### Loon 配置

#### Loon Ver.1.0 (2025-08-18)

📌 **说明**  
本配置文件为 **Loon 专用配置**，结合个人实际使用需求与 Nikki 配置文件编写。

🆕 **更新内容**

- 初版发布  
- 集成常用分流规则与代理组  
- 优化部分策略逻辑，适配日常使用场景  

🔗 **参考资源**

- [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script)  
- [luestr/ProxyResource](https://github.com/luestr/ProxyResource)  
- [fmz200/wool_scripts](https://github.com/fmz200/wool_scripts)  
- [limbopro/Adblock4limbo](https://github.com/limbopro/Adblock4limbo)  
- [Loon0x00/LoonManual](https://github.com/Loon0x00/LoonManual)  
- [luestr/ShuntRules](https://github.com/luestr/ShuntRules)  
- [Cats-Team/AdRules](https://github.com/Cats-Team/AdRules/tree/main?tab=readme-ov-file)
- [privacy-protection-tools/anti-AD](https://github.com/privacy-protection-tools/anti-AD?tab=readme-ov-file)

🕒 更新日志
-------

详见 [`CHANGELOG.md`](CHANGELOG.md)

## 🧠 参考项目

- [refined-fish/clash_rule_fish](https://github.com/refined-fish/clash_rule_fish)
- [liandu2024/clash](https://github.com/liandu2024/clash)
- [Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)
- [qichiyuhub/rule](https://github.com/qichiyuhub/rule)
- [Coldvvater/Mononoke](https://github.com/Coldvvater/Mononoke)
- [privacy-protection-tools/anti-AD](https://github.com/privacy-protection-tools/anti-AD)
---
-  以及上文 Loon 相关资源

