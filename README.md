# BSakura mihomo-config

个人使用的 mihomo / Loon 配置模板。

当前主线是家庭网关架构：RouterOS 作为主路由，按 CNIP / 策略路由把需要代理的 IPv4 流量送到 mihomo 旁路网关，IPv6 默认由 RouterOS 直连，不进入代理链路。

最后更新：2026-06-23

## 文件

| 文件 | 用途 |
| --- | --- |
| `mihomo_BS_Template.yml` | mihomo 网关模板，适合 Linux / LXC / 裸核运行 |
| `Loon/Loon_BS.conf` | Loon iPhone 默认模板 |
| `Loon/Loon_BS_iPhone.conf` | Loon iPhone 模板 |
| `Loon/Loon_BS_mac.conf` | Loon Mac 模板 |
| `nikki.txt` | Nikki/OpenWrt 相关参考配置 |

## 隐私说明

仓库内配置是公开模板，已移除或替换以下内容：

- 机场订阅链接
- WireGuard 私钥、公钥、endpoint
- VLESS / Trojan / SS 等手写节点
- mihomo 面板 `secret`
- 其他 token / key / 私密节点信息

使用前请搜索 `REDACTED`、`CHANGE_ME`、`example.com`、`<...>` 并替换成自己的信息。

## mihomo 网关思路

默认端口：

| 端口 | 作用 |
| --- | --- |
| `7890` | HTTP 代理 |
| `7891` | SOCKS5 代理 |
| `7892` | redir TCP 透明代理 |
| `7893` | mixed HTTP/SOCKS |
| `7894` | tproxy UDP 透明代理 |
| `9090` | external-controller / Zashboard |

关键设计：

- `ipv6: false`，因为机场节点不支持 IPv6，IPv6 由主路由直连。
- `fake-ip-range: 198.18.0.0/15`，配合 RouterOS 的 Fake-IP 回程路由。
- `Final` 策略组包含 `Proxy`、`AllServer`、`DIRECT`，方便兜底策略快速切换。
- PT tracker、内网、国内常用服务优先直连。
- `LoadBalance` 默认不使用，避免日常连接体验不稳定。

## RouterOS 配合项

典型配合方式：

- RouterOS 负责 DHCP、DNS 指向、CNIP 初筛和策略路由。
- mihomo 旁路网关负责透明代理、规则分流、Fake-IP。
- AdGuardHome 可作为局域网 DNS 入口，RouterOS 保留上游和路由控制。

需要按自己的环境调整：

- mihomo 网关 IP
- `to_side_router` 路由表或等价策略路由
- Fake-IP 网段回程路由
- QUIC bypass 策略
- DNS 劫持/重定向策略

## Loon 模板

Loon 配置保留了日常使用策略组：

- `Final`
- `Proxy`
- `AI`
- `Speedtest`
- `GitHub`
- `YouTube`
- `NETFLIX`
- `Telegram`
- `Apple`
- `Google`
- `Microsoft`
- 地区节点组和自动测速组

`[Proxy]` 和 `[Remote Proxy]` 内仅保留示例。导入前需要替换自己的订阅和手写节点。

## 使用步骤

1. 下载对应模板。
2. 替换订阅链接、面板密钥和节点占位符。
3. 根据客户端环境调整端口和透明代理选项。
4. 用 mihomo / Loon 自带检查功能确认配置可加载。
5. 再接入 RouterOS 策略路由或客户端分流。

## 参考

- [MetaCubeX mihomo 文档](https://wiki.metacubex.one/config/)
- [refined-fish/clash_rule_fish](https://github.com/refined-fish/clash_rule_fish)
- [liandu2024/clash](https://github.com/liandu2024/clash)
- [Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)
- [qichiyuhub/rule](https://github.com/qichiyuhub/rule)
- [Coldvvater/Mononoke](https://github.com/Coldvvater/Mononoke)
- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)
- [luestr/ProxyResource](https://github.com/luestr/ProxyResource)

## 更新日志

详见 [`CHANGELOG.md`](CHANGELOG.md)。
