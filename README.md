# BSakura mihomo-config

个人使用的 mihomo / Loon 配置模板。

当前主线是家庭网关架构：RouterOS 作为主路由，按 CNIP / 策略路由把需要代理的 IPv4 流量送到 mihomo 旁路网关，IPv6 默认由 RouterOS 直连，不进入代理链路。

最后更新：2026-08-17

## 文件

| 文件 | 用途 |
| --- | --- |
| `mihomo_BS_Template.yml` | mihomo 网关模板，适合 Linux / LXC / 裸核运行 |
| `mihomo_F50Pro_Template.yml` | 中兴 F50 Pro / UFI-TOOLS 脱敏模板，使用 TUN + auto-route |
| `Loon/Loon_BS.conf` | Loon iPhone / Mac 通用模板 |
| `nikki.txt` | Nikki/OpenWrt 相关参考配置 |

## 隐私说明

仓库内配置是公开模板，已移除或替换以下内容：

- 机场订阅链接
- WireGuard 私钥、公钥、endpoint
- VLESS / Trojan / SS 等手写节点
- Loon MITM CA 与口令
- 家庭 Wi-Fi SSID 与本地主机名
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
- `fake-ip-range: 198.18.0.0/16`，与 RouterOS 的 Fake-IP 回程路由和本地地址列表保持一致。
- 外部面板固定为 Zashboard，并配置 `external-ui-url`，避免更新 UI 时回退到其他默认面板。
- `Final` 策略组包含 `Proxy`、`AllServer`、`DIRECT`，方便兜底策略快速切换。
- `AI` 可优先使用自建 `VLESS + REALITY + Vision` 节点，并通过 `AI-专线` 在故障时回退机场策略。
- PT tracker、内网、国内常用服务优先直连。
- 与 Loon 同步 `ug.link`、Blackmagic Design、Wabotech 及 `119.29.35.44/32` 直连规则。
- `LoadBalance` 默认不使用，避免日常连接体验不稳定。

## F50 Pro 模板

- 保留 UFI-TOOLS/CMFA 所需的 `cmfa-plugin` 和 TUN 配置。
- 面板使用 `192.168.0.1:7788`，必须先替换 `<CHANGE_ME>` 密钥。
- 两个订阅 URL 都是占位符，不包含私人订阅。
- 包含脱敏的 `Seoul-AI` 节点和 `AI-专线` 回退组，使用前必须替换节点占位参数。
- 由于 F50 Pro 模板没有 Loon 的 WireGuard `home` 节点，不包含两条“回家”网段规则。

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
- `AI-专线`（自建 REALITY 节点优先、机场策略回退）
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

### 自建 AI 节点

模板提供 `Seoul-AI` 占位节点和 `AI-专线` 故障转移组。使用时必须替换服务器地址、端口、UUID、REALITY 公钥、Short ID 和 SNI；公开仓库不应提交这些真实值。AI 规则仍统一指向 `AI`，不会改变 PT、流媒体、国内直连或 IPv6 路径。

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
