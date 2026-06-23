<!--
 * @Author: bsakura
 * @Date: 2025-08-05 12:15:04
 * @LastEditors: BSakura
 * @LastEditTime: 2025-08-31 10:16:02
 * @FilePath: /undefined/Users/bsakura/Documents/github/mihomo-config/CHANGELOG.md
 * @Description:
 *
 * Copyright (c) 2025 by bsakura, All Rights Reserved.
-->

# 📜 更新日志

## mihomo gateway / Loon Ver.1.6 (2026-06-23)
- 同步当前 RouterOS + CT202 mihomo 旁路网关配置结构。
- 更新 `mihomo_BS_Template.yml` 顶部说明、端口、Fake-IP、Final/AllServer 等当前策略。
- 新增 Loon Mac / iPhone 发布版模板。
- 移除公开模板中的订阅链接、WireGuard 节点、手写代理节点与面板 secret。
- README 改写为当前家庭网关和客户端模板说明。

## Nikki Ver.3.9.5 (2025-09-07)
- 增加: PT 站点直连

## Nikki Ver.3.9.5 (2025-08-31)
- 增加: BT tracker常用域名 修复: 部分规则写法错误
- 放行`iadsdk.apple.com`域名 避免 AppStore 加载错误
## Nikki Ver.3.9.2 (2025-08-22)
- 修改: 流媒体放入国际服务之前

## Loon Ver.1.3 (2024-08-22)
- 新增 `doh-server = https://223.5.5.5/dns-query,https://223.6.6.6/dns-query`

## Nikki Ver.3.9.1 (2025-08-18)
- 添加 adrules.list 规则 [Cats-Team/AdRules](https://github.com/Cats-Team/AdRules/tree/main?tab=readme-ov-file)
- 优化规则顺序
- 添加 Global 集
- fake-ip-filter 新增 ` - 'RULE_SET,anti-ad_domain,adrules_domain,anProgramAD_domain'      `

## Loon Ver.1.2 (2025-08-18)
- 添加 adrules.list 规则  [AdRules List](https://adrules.top)
- 添加 WeChat.list 规则  [blackmatrix7/ios_rule_script](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Loon/WeChat/WeChat.list)
- 添加 Global 集

## Nikki Ver.1.1 (2025-08-18)
- 修改dns-reject-mode = Request

## Loon Ver.1.0 (2025-08-18)
📌 **说明**
本配置文件为 **Loon 专用配置**，结合个人实际使用需求与 Nikki 配置文件编写。

🆕 **更新内容**
- 初版发布
- 集成常用分流规则与代理组
- 优化部分策略逻辑，适配日常使用场景

🔗 **参考资源**
-  [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script)
-  [luestr/ProxyResource](https://github.com/luestr/ProxyResource)
-  [fmz200/wool_scripts](https://github.com/fmz200/wool_scripts)
-  [limbopro/Adblock4limbo](https://github.com/limbopro/Adblock4limbo)
-  [Loon0x00/LoonManual](https://github.com/Loon0x00/LoonManual)
-  [luestr/ShuntRules](https://github.com/luestr/ShuntRules)

## Nikki Ver.3.9 (2025-08-17)
- 新增韩国策略组 国内修改为China 部分策略优化
## Ver.3.8 (2025-08-16)
- 修改部分rules 如OneDrive， 更新tun设置

## Ver. 3.5 (2025-08-06 07:35)
- ✅ 修改fake ip排除列表、增加部分注释、优化可读性、优化规则匹配、网易云解锁节点筛选

## Ver. 3.1 (2025-08-06 04:55)
- ✅ 修改 speedtest 相关测速规则

## Ver. 3.0 (2025-08-05 06:03)
- ✅ 修改 GEO 数据库下载地址
- ✅ 增加代理组 icon
- ✅ 优化可读性
- ✅ 修改远程规则集保存路径

## Ver. 2.1 (2025-08-03 06:04)
- ✅ 优化规则匹配

## Ver. 2.0 (2025-08-03 05:14)
- ✅ 优化广告拦截策略

## Ver. 1.0 (2025-08-02 13:24)
- ✅ 初始版本发布
