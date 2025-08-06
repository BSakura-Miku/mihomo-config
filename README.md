<!--
 * @Author: bsakura
 * @Date: 2025-08-05 12:15:01
 * @LastEditors: BSakura
 * @LastEditTime: 2025-08-06 05:32:44
 * @FilePath: /undefined/Users/bsakura/Documents/github/mihomo-config/README.md
 * @Description: 
 * 
 * Copyright (c) 2025 by bsakura, All Rights Reserved. 
-->
# 🧩 Nikki 配置模板

个人使用的 Nikki 配置模板，专为追求精简、高效、易维护的用户设计。  
适用于 Clash / Clash Meta / MetaCubeX / Nikki 等常见代理客户端。

---

## 📦 项目描述

本项目提供了完整的 nikki 配置框架，具备以下特点：

- ✨ 精简且常用的规则集，满足主流使用场景
- 🔧 支持 GEO 数据库远程下载，更新更便捷
- 📦 配置文件结构清晰，注释详尽，方便自定义扩展
- 📁 rule-providers 基本使用 .mrs 格式，更快、内存占用更低
- 🧱 使用anti-AD广告过滤列表 
- 🎨 图标美化支持

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

2. 将 `mihomo_BS_Template.yml` 导入到你使用的 Clash 客户端（如 Clash Verge、Clash Meta for Android 等）。

3. 根据注释提示，根据你使用的软件调整

4. (可选) `nikki.txt` 为nikki程序配置 路径`/etc/config/`

---

![策略组展示](<FireShot Capture 006 - zashboard - 代理 - [10.10.2.2].png>)

## 🕒 更新日志

详见 [`CHANGELOG.md`](CHANGELOG.md)

---

## 🧠 参考项目

- [refined-fish/clash_rule_fish](https://github.com/refined-fish/clash_rule_fish)
- [liandu2024/clash](https://github.com/liandu2024/clash)
- [Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)
- [qichiyuhub/rule](https://github.com/qichiyuhub/rule)
- [Coldvvater/Mononoke](https://github.com/Coldvvater/Mononoke)
- [privacy-protection-tools/anti-AD](https://github.com/privacy-protection-tools/anti-AD)
---

