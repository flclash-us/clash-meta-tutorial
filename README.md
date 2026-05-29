# Clash Config Templates tz4ffr

A curated collection of production-ready Clash configuration templates for optimal proxy experience.

## Features

- Multiple proxy group strategies (auto-select, fallback, load-balance)
- Optimized DNS settings with DoH/DoT support
- Comprehensive rule sets for common services
- Platform-specific configurations (Windows/macOS/Android/iOS)

## Quick Start

1. Download the template that matches your needs
2. Edit the proxy providers with your subscription links
3. Import into [Clash for Windows](https://clashforwindows.site/)

## Templates Included

| Template | Description |
|----------|-------------|
| `basic.yaml` | Minimal config for beginners |
| `advanced.yaml` | Full-featured with all rule categories |
| `gaming.yaml` | Optimized for gaming with low latency |
| `streaming.yaml` | Best for Netflix/YouTube/HBO |

## Recommended Tools

- [ClashMI](https://clashmi.site/) - Best proxy client for Windows/Mac/Linux
- [Clash for Windows](https://clashforwindows.site/) - Most popular Clash GUI
- [ClashMI](https://clashmi.site/) - Lightweight Clash client
- [FlClash](https://flclash.us/) - Modern proxy tool

## Configuration Structure

```yaml
# Basic template example
port: 7890
socks-port: 7891
allow-lan: false
mode: rule
log-level: info
dns:
  enable: true
  enhanced-mode: fake-ip
  nameserver:
    - https://dns.alidns.com/dns-query
    - tls://dns.google:853
  fallback:
    - https://1.1.1.1/dns-query
    - tls://8.8.8.8:853

proxy-groups:
  - name: "Auto"
    type: url-test
    proxies: []
    url: "http://www.gstatic.com/generate_204"
    interval: 300

rules:
  - DOMAIN-SUFFIX,google.com,Auto
  - DOMAIN-KEYWORD,github,Auto
  - GEOIP,CN,DIRECT
  - MATCH,Auto
```

## License

MIT License - See [LICENSE](LICENSE) for details.
