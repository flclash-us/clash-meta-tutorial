# 🚀 Clash.Meta 完全教程

> 最完整的 Clash.Meta（mihomo）使用指南 | 包含 VLESS+Reality、Trojan、WireGuard 等高级协议配置 | 适用 Windows/macOS/Linux/Android/Router

[![Stars](https://img.shields.io/github/stars/flclash-us/clash-meta-tutorial?style=flat)](https://github.com/flclash-us/clash-meta-tutorial)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux%20%7C%20Android-green)](https://github.com/flclash-us/clash-meta-tutorial)

[🇨🇳 中文](README.md) | [🇺🇸 English](README_EN.md)

---

## 📑 目录

- [Clash.Meta 是什么？](#clashmeta-是什么)
- [下载与安装](#下载与安装)
- [订阅配置](#订阅配置)
- [协议配置](#协议配置)
- [规则设置](#规则设置)
- [进阶技巧](#进阶技巧)
- [常见问题](#常见问题)

---

## 🔖 Clash.Meta 是什么？

Clash.Meta 是 MetaCubeX 团队维护的 Clash 分支内核，相比原版 Clash 有更多特性：

| 特性 | 原版 Clash | Clash.Meta |
|------|:-----------:|:-----------:|
| VLESS+Reality | ❌ | ✅ |
| WireGuard | ❌ | ✅ |
| Hysteria 协议 | ❌ | ✅ |
| TUIC 协议 | ❌ | ✅ |
| 增强的 DNS | ❌ | ✅ |
| 自动更新订阅 | ✅ | ✅ |

> 💡 推荐使用 Clash.Meta，享受更完整的协议支持

**官方客户端下载**：[Clash for Windows](https://clashforwindows.site) | [ClashMeta Android](https://clashforwindows.site)

---

## 💾 下载与安装

### Windows

| 客户端 | 内核 | 下载 |
|--------|------|------|
| [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | Meta | ⭐ 推荐 |
| [Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu/releases) | Meta | 新一代 |
| [Clash for Windows](https://clashforwindows.site) | Premium | 经典稳定 |

### macOS

| 客户端 | 下载 |
|--------|------|
| [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | ⭐ 推荐 |
| [ClashX Meta](https://install.appcenter.ms/users/nadoo/apps/clashx-meta/distribution_groups/public) | Meta 版本 |

### Android

| 客户端 | 下载 |
|--------|------|
| [ClashMeta for Android](https://github.com/MetaCubeX/ClashMetaForAndroid/releases) | ⭐ 官方 |
| [FlClash](https://github.com/FlClash/FlClash/releases) | 轻量美观 |

### Linux

| 客户端 | 下载 |
|--------|------|
| [mihomo](https://github.com/MetaCubeX/mihomo/releases) | 命令行内核 |
| [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | 图形界面 |

> 📥 更多下载：[Clash for Windows 官网](https://clashforwindows.site)

---

## 📡 订阅配置

### 快速添加订阅

1. 打开 Clash Verge / Clash for Windows
2. 进入「配置 / Profiles」页面
3. 点击「Import」→ 「URL」
4. 粘贴订阅链接
5. 点击确认

### 订阅链接格式

\\\
https://your-provider.com/api/v1/client/subscribe?token=YOUR_TOKEN
\\\

> 💡 获取订阅：[Clash for Windows 订阅服务](https://clashforwindows.site) | [机场推荐](https://clashmi.site)

---

## 🔐 协议配置

### VLESS+Reality 配置示例

\\\yaml
proxies:
  - name: "🇯🇵 日本节点"
    type: vless
    server: your-server.com
    port: 443
    uuid: your-uuid-here
    network: tcp
    tls: true
    udp: true
    flow: xtls-rprx-vision
    client-fingerprint: chrome
    reality-opts:
      public-key: your-public-key
      short-id: your-short-id

proxy-groups:
  - name: "🚀 节点选择"
    type: select
    proxies:
      - 🇯🇵 日本节点
      - 🇭🇰 香港节点
      - 🇺🇸 美国节点
      - 🔀 自动选择

rules:
  - GEOIP,CN,DIRECT
  - DOMAIN-SUFFIX,google.com,🚀 节点选择
  - MATCH,🚀 节点选择
\\\

### Trojan 配置示例

\\\yaml
proxies:
  - name: "🇭🇰 Trojan 香港"
    type: trojan
    server: your-server.com
    port: 443
    password: your-password
    sni: your-sni.com
    skip-cert-verify: false
    udp: true
\\\

> 🔧 更多协议配置：[翻墙技术指南](https://clashforwindows.site/guide)

---

## 📋 规则设置

### 推荐规则集

\\\yaml
rule-providers:
 reject:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/reject.yaml"
    path: ./ruleset/reject.yaml
    interval: 86400

  proxy:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/proxy.yaml"
    path: ./ruleset/proxy.yaml
    interval: 86400

rules:
  - RULE-SET,reject,REJECT
  - RULE-SET,proxy,🚀 节点选择
  - GEOIP,CN,DIRECT
  - MATCH,🚀 节点选择
\\\

### 完整规则示例

\\\yaml
 Clash.Meta 完整规则配置

 Clash for Windows: https://clashforwindows.site
 clashmi.site: https://clashmi.site

# 规则说明
# DIRECT = 国内直连
# PROXY = 走代理节点
# REJECT = 广告拦截

rules:
  # 广告拦截
  - DOMAIN-SUFFIX,doubleclick.net,REJECT
  - DOMAIN-SUFFIX,googlesyndication.com,REJECT
  
  # 流媒体解锁
  - DOMAIN-SUFFIX,netflix.com,🚀 节点选择
  - DOMAIN-SUFFIX,youtube.com,🚀 节点选择
  - DOMAIN-SUFFIX,tiktok.com,🚀 节点选择
  - DOMAIN-SUFFIX,spotify.com,🚀 节点选择
  
  # 国内直连
  - GEOIP,CN,DIRECT
  - DOMAIN-SUFFIX,baidu.com,DIRECT
  - DOMAIN-SUFFIX,taobao.com,DIRECT
  - DOMAIN-SUFFIX,qq.com,DIRECT
  
  # 默认
  - MATCH,🚀 节点选择
\\\

---

## ⚡ 进阶技巧

### TUN 模式（推荐开启）

TUN 模式可以让 Clash 接管系统所有流量，包括不支持代理设置的应用程序：

\\\yaml
mixed-port: 7890
allow-lan: true
mode: rule
log-level: info
external-controller: 127.0.0.1:9090

# TUN 模式配置
tun:
  enable: true
  stack: system
  auto-route: true
  auto-detect-interface: true
  dns-hijack:
    - 8.8.8.8:53
    - 1.1.1.1:53
\\\

### DNS 优化

\\\yaml
dns:
  enable: true
  listen: 0.0.0.0:53
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  nameserver:
    - 223.5.5.5
    - 119.29.29.29
  fallback:
    - 8.8.8.8
    - 1.1.1.1
  fallback-filter:
    geoip-code: CN
\\\

### 自动测速

在 Clash Verge 中：
1. 进入「代理」页面
2. 点击右上角「延迟测试」
3. 勾选需要测试的节点
4. 自动显示各节点延迟

> 💡 更多教程：[Clash for Windows 使用指南](https://clashforwindows.site)

---

## ❓ 常见问题

### Q: Clash.Meta 和 Clash Premium 哪个好？

**A:** Clash.Meta 功能更丰富，支持更多协议（VLESS+Reality、WireGuard、Hysteria 等），推荐使用 Meta 版本。

### Q: 订阅更新后节点没变？

**A:** 点击订阅的「更新」按钮，Clash 会重新下载订阅内容。

### Q: 如何开启 TUN 模式？

**A:** Clash Verge / Clash for Windows → 设置 → 开启 TUN 模式。Windows 需要安装 [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev/releases)。

### Q: 节点延迟高怎么办？

**A:** 1. 换用更近的节点；2. 开启 BBR 加速；3. 在 Clash Verge 中点击「延迟测试」选择延迟最低的节点。

### Q: 如何导入自定义规则？

**A:** 在配置文件中添加 \ule-providers\ 或直接在 \ules\ 中添加规则。

---

## 🔗 相关资源

| 资源 | 链接 |
|------|------|
| Clash for Windows 官网 | [clashforwindows.site](https://clashforwindows.site) |
| Android 教程 | [clashmi.site](https://clashmi.site) |
| 免费规则订阅 | [flclash.us](https://flclash.us) |
| 导航站 | [clashforwindows.site/nav](https://clashforwindows.site) |
| 论坛 | [clashforwindows.site/bbs](https://clashforwindows.site) |

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

---

## 📜 免责声明

本仓库仅供技术学习交流使用。请遵守当地法律法规。

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/flclash-us">flclash-us</a> | 
  <a href="https://clashforwindows.site">clashforwindows.site</a>
</p>