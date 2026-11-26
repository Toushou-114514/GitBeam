# GitBeam

[繁体中文](README.md) [简体中文](README.zh.md) [English](README.en.md)

A lightweight Android tool that makes GitHub reachable through **local DNS cleaning**.

## How it works

GitBeam registers a local VPN interface and takes over DNS only (queries go to `10.111.222.2`): GitHub domains are resolved over DoH, ranked by a real TLS handshake, and returned; everything else is forwarded to the original DNS. Web traffic is not proxied.

Accelerated domains: all `github.com` subdomains, `githubusercontent.com`, `githubassets.com`, `github.io`, `ghcr.io`, `git.io`, etc., plus custom domains you add. AAAA answers are blocked by default to force IPv4.

## Install

Go to the **[release page](https://github.com/Toushou-114514/GitBeam/releases/latest)** and download `GitBeam.apk`.

Install `GitBeam.apk`.

Done.

## Features

- DoH: DNSPod / AliDNS / Cloudflare / Google, pinned IPs with real SNI and certificate validation; built-in address table as a last resort
- IP optimisation by TLS handshake timing, AAAA toggle, 5 / 10 / 30 / 60-minute cache
- Home-screen connectivity test: compares system DNS with DoH and performs a real HTTPS handshake to GitHub
- Custom domains, diagnostic log, start on boot, themes (system / light / dark), 简体中文 / 繁體中文 / English

## Notes

- Turn **Private DNS** off or set it to Automatic; a hostname setting bypasses this app.
- Accept the VPN permission prompt on first launch; Android 13+ also asks for notification permission.
- DNS only: actual transfer speed still depends on your link to GitHub.
- `keystore.jks` (password `gitbeam`) is the debug signing key — keep it to upgrade later.

## About

Author: [Toushou](https://github.com/Toushou-114514)
![ts](https://avatars.githubusercontent.com/u/219519717?v=4&size=64)
