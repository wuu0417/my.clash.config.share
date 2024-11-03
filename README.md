# 仓库信息
### 我自用的Clash 配置文件
A Clash config that I use it myself

### 代理客户端
Clash或Mihomo（原Clash.Meta）

我自己用的是Mihomo，因为原Clash核心已经删库且无人维护。

但鉴于Mihomo设计之初就与Clash原内核的语法兼容，因此本配置在原Clash内核上大概也能运行。

### 配置特色
重点在DNS分流上。

参考配置内容，我把所有DNS请求分四部分：
> + nameserver
> + fallback
> + default-nameserver
> + proxy-server-nameserver

nameserver：
解析国内DNS请求，配置使用阿里云DoH和腾讯云DoH。

fallback:
解析国外DNS请求，配置使用Google DoH、Cloudflare DoH和OpenDNS DoH。

default-nameserver：
解析DoH服务器域名的DNS服务器，也就是只负责解析如dns.alidns.com这样的DNS服务器域名。配置使用223.5.5.5、119.29.29.29和8.8.8.8。

proxy-server-nameserver:
专门解析节点服务器域名的DNS服务器，配置使用223.5.5.5和119.29.29.29。如使用自建节点或非专线/中转机场，请改为合适的国外DNS。

DNS规范具体参考[Mihomo官方介绍](https://wiki.metacubex.one/config/dns/)

DNS分流的目的是达到类似V2RayN“绕过大陆模式”的效果。

### 说明 
自己设置配置的初衷是不满机场的默认配置。机场配置常常会代入完善的常用软件规则（如Google），可以满足大部分用户使用。但如果想要翻墙访问一些小众网页（如：我一个朋友经常翻墙看小众的Sex网站），这些网站不在机场维护的分流规则内，就容易发起本地DNS请求进而导致DNS泄露，容易给本地ISP可乘之机。因此，我才~~帮助这位朋友~~设计了此规则。

但这只是我自己编写的Clash配置，碍于个人水平有限，难免会有遗漏或不足。

如果你发现有任何疏漏之处，还请Issues指正，我会按照您的指教做出改正。
