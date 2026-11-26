# GitBeam

[繁体中文](README.md) [简体中文](README.zh.md) [English](README.en.md)

一个在安卓设备上通过**本地 DNS 清洗**让 GitHub 可访问的轻量小工具。

## 原理

应用注册一个本地 VPN 接口，只接管 DNS（查询发往 `10.111.222.2`）：GitHub 相关域名走 DoH 获取真实地址，用真实 TLS 握手测速排序后返回；其他域名照常转发给原 DNS。网页流量不经过代理。

加速范围：`github.com` 全子域、`githubusercontent.com`、`githubassets.com`、`github.io`、`ghcr.io`、`git.io` 等，以及手动添加的自定义域名。默认拦截 AAAA，强制走 IPv4。

## 安装

来到 **[发布页面](https://github.com/Toushou-114514/GitBeam/release/latest)** 下载文件`GitBeam.apk`

安装`GitBeam.apk`

大功告成


## 功能

- DoH：DNSPod / 阿里 / Cloudflare / Google，固定 IP + 真实 SNI 与证书校验，全部失败时回退内置地址表
- IP 优选（TLS 握手测速）、AAAA 开关、缓存 5 / 10 / 30 / 60 分钟
- 首页连通性测试：对比系统 DNS 与 DoH，并对 GitHub 做真实 HTTPS 握手
- 自定义域名、诊断日志、开机自启、主题（跟随系统 / 浅色 / 深色）、简体中文 / 繁體中文 / English

## 使用注意

- 系统「私人 DNS」要关闭或设为「自动」，设成主机名会绕过本应用。
- 首次开启需授权 VPN；Android 13+ 还会请求通知权限。
- 只改 DNS 应答，实际下载速度仍取决于你到 GitHub 的链路。
- `keystore.jks`（口令 `gitbeam`）是 debug 签名，升级安装需保留它。

## 关于

作者：[Toushou](https://github.com/Toushou-114514)
![ts](https://avatars.githubusercontent.com/u/219519717?v=4&size=64)

