# GitBeam

[繁体中文](README.md) [简体中文](README.zh.md) [English](README.en.md)

一款在安卓裝置上透過**本機 DNS 清洗**讓 GitHub 可連線的輕量小工具。

## 原理

應用程式註冊本機 VPN 介面，只接管 DNS（查詢送往 `10.111.222.2`）：GitHub 相關網域透過 DoH 取得真實位址，再以真實 TLS 握手測速排序後回傳；其他網域照樣轉送給原本的 DNS。網頁流量不經由代理。

加速範圍：`github.com` 所有子網域、`githubusercontent.com`、`githubassets.com`、`github.io`、`ghcr.io`、`git.io` 等，以及自行新增的自訂網域。預設封鎖 AAAA，強制使用 IPv4。

## 安裝

前往 **[發布頁面](https://github.com/Toushou-114514/GitBeam/releases/latest)** 下載 `GitBeam.apk`

安裝 `GitBeam.apk`

大功告成

## 功能

- DoH：DNSPod / 阿里 / Cloudflare / Google，固定 IP + 真實 SNI 與憑證驗證，全部失敗時回退內建位址表
- IP 優選（TLS 握手測速）、AAAA 開關、快取 5 / 10 / 30 / 60 分鐘
- 首頁連線測試：比對系統 DNS 與 DoH，並對 GitHub 做真實 HTTPS 握手
- 自訂網域、診斷日誌、開機自動啟動、主題（跟隨系統 / 淺色 / 深色）、简体中文 / 繁體中文 / English

## 使用注意

- 系統「私人 DNS」請關閉或設為「自動」，設成主名稱會繞過本應用程式。
- 首次開啟需授權 VPN；Android 13+ 也會要求通知權限。
- 只改 DNS 回應，實際下載速度仍取決於你到 GitHub 的線路。
- `keystore.jks`（密碼 `gitbeam`）為 debug 簽章，升級安裝時請保留。

## 關於

作者：[Toushou](https://github.com/Toushou-114514)
![ts](https://avatars.githubusercontent.com/u/219519717?v=4&size=64)
