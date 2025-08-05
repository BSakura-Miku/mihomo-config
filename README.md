# 🧩 Clash 高性能配置模板

个人使用的 Clash 配置模板，专为追求精简、高效、易维护的用户设计。  
适用于 Clash / Clash Meta / MetaCubeX / Nikki 等常见代理客户端。

---

## 📦 项目描述

本项目提供了完整的 Clash 配置框架，具备以下特点：

- ✨ 精简且高性能的规则集，满足主流使用场景
- 🔧 支持 GEO 数据库远程下载，更新更便捷
- 🎨 配置文件结构清晰，注释详尽，方便自定义扩展
- 📁 遵循 GitHub 最佳实践，方便协作与版本控制
- 🧱 提供裸核用户的使用建议
- 📦 包含常用远程规则集地址及图标美化支持

---

## 📌 快速开始

1. 下载载配置文件：

2. 修改 `订阅地址` `机场名称`
```
proxy-providers:
  机场名称:
    <<: *proxy-providers-general                          # 引用上文的yaml锚点
    url: "订阅地址"
    override:                                             # 可选，覆写设置
      additional-prefix: "ik|"                            # 可选，给订阅添加前缀
    #path: ./providers/proxy/proxy-provider1.yaml         # 可选，指定下载路径
  # ikuuu2:

# 代理组设置
use-all-proxy-providers: &use-all-proxy-providers         # 代理组通用配置
  use:
    - 机场名称
    # ikuuu2
```

2. 将 `mihomo_BS_Template.yml` 导入到你使用的 Clash 客户端（如 Clash Verge、Clash Meta for Android 等）。

3. 根据注释提示，根据你使用的软件调整

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

---

