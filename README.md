<p align="center">
  <img src="banner.svg" alt="MeduzaVPN — personal VPN on your own server" width="100%">
</p>

<p align="center">
  <a href="https://meduzavpn.com"><img alt="Website" src="https://img.shields.io/badge/meduzavpn.com-0A0E19?style=for-the-badge&labelColor=0A0E19&color=C37BD9"></a>
  <a href="https://github.com/txrx13/meduzavpn/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/txrx13/meduzavpn?style=for-the-badge&labelColor=0A0E19&color=8199D6"></a>
  <img alt="Platforms" src="https://img.shields.io/badge/Linux%20%C2%B7%20macOS%20%C2%B7%20Windows-0A0E19?style=for-the-badge&labelColor=0A0E19&color=5A7AB7">
</p>

<h3 align="center">Your VPN. Your server. Your rules.</h3>

<p align="center">
  MeduzaVPN gives you a VPN server that is <b>yours alone</b> — not a shared pool, not a
  crowded exit node. You pick the country, we deploy the server, and nobody else is on it.
</p>

<p align="center">
  <b>This repository publishes the official builds.</b> It holds no source code.
</p>

---

## Why a server of your own

A shared VPN puts thousands of people behind one address. That address gets rate-limited,
CAPTCHA-walled and blocked, because of what strangers did with it. A server of your own has
none of that: its reputation is whatever you make it.

It also changes what a block can do to you. When one protocol stops working on your network,
you switch to another on the same server, in one tap — the server already speaks all of them.

## Protocols

| | |
|---|---|
| **MeduzaVPN** | our own protocol — obfuscated, looks like nothing in particular on the wire |
| **VLESS / VLESS 2.0** | REALITY on 443 and XHTTP on 2053 — indistinguishable from an ordinary TLS site |
| **WireGuard** | the fastest, and the easiest for a network to recognise |
| **Hysteria 2** | QUIC — holds up best on a lossy mobile link |
| **OpenVPN · Xray · V2Ray · Outline · Shadowsocks · SOCKS5 · IKEv2/IPsec · SoftEther** | everything else, on the same server |

---

## Install on Linux

**Use the repository.** It signs everything, resolves dependencies, and upgrades with the
rest of your system.

### Debian, Ubuntu

```bash
curl -fsSL https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/meduzavpn-archive-keyring.asc \
  | sudo gpg --dearmor -o /usr/share/keyrings/meduzavpn.gpg
echo "deb [signed-by=/usr/share/keyrings/meduzavpn.gpg] https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/deb stable main" \
  | sudo tee /etc/apt/sources.list.d/meduzavpn.list
sudo apt update
sudo apt install meduzavpn-desktop   # the app; pulls in the service
sudo apt install meduzavpn           # a server: the command line and the daemon only
```

### Fedora, CentOS, RHEL

```bash
sudo rpm --import https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/meduzavpn-archive-keyring.asc
sudo tee /etc/yum.repos.d/meduzavpn.repo >/dev/null <<'REPO'
[meduzavpn]
name=MeduzaVPN
baseurl=https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/rpm
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/meduzavpn-archive-keyring.asc
REPO
sudo dnf install meduzavpn-desktop
```

### Anything else — Arch, openSUSE, NixOS, Alpine, a container

```bash
curl -fsSLO https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-158-linux-amd64.tar.gz
tar xzf meduzavpn-1.2.24-158-linux-amd64.tar.gz
cd meduzavpn-1.2.24-158-linux-amd64 && sudo ./install.sh
```

The tarball carries compiled binaries, a systemd unit, an installer **and an uninstaller** —
not source code.

> The service is never enabled for you. A VPN daemon that takes the default route a second
> after installation would be a rude surprise on a machine you reached over SSH. Start it when
> you are ready: `sudo systemctl enable --now meduzavpnd`

---

## The command line

The same `meduzavpn` binary on all three desktop systems. One invocation brings up any VPN on
your account, with no configuration file needed:

```bash
meduzavpn login --qr                    # scan the code with the phone app
meduzavpn list                          # your VPNs, the protocols, the settings in force
meduzavpn connect --protocol vless2 --wait
meduzavpn status
meduzavpn disconnect
```

Every setting resolves **flag → environment → config file → what the server's profile says**,
`--json` is available everywhere for scripts, and the exit codes tell "not signed in" apart
from "no daemon" from "the server refused".

On Linux the tunnel belongs to the `meduzavpnd` service. On macOS and Windows it belongs to
the application, and the command line drives it over a local socket — enable the command-line
interface in the app's settings first.

---

## Downloads

Everything here is also on [meduzavpn.com](https://meduzavpn.com).

### Linux

| File | For |
|---|---|
| [`meduzavpn-desktop_1.2.24-158_amd64.deb`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-desktop_1.2.24-158_amd64.deb) | the app — Ubuntu, Debian |
| [`meduzavpn-desktop-1.2.24-158.x86_64.rpm`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-desktop-1.2.24-158.x86_64.rpm) | the app — Fedora, CentOS, RHEL |
| [`meduzavpn_1.2.24-158_amd64.deb`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn_1.2.24-158_amd64.deb) | the service — Ubuntu, Debian |
| [`meduzavpn-1.2.24-158.x86_64.rpm`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-158.x86_64.rpm) | the service — Fedora, CentOS, RHEL |
| [`meduzavpn-1.2.24-158-linux-amd64.tar.gz`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-158-linux-amd64.tar.gz) | everything else |

Installing a `.deb` or `.rpm` by hand? The app package depends on the service package — take
both, or use the repository above and let it sort itself out.

### macOS and Windows

| File | For |
|---|---|
| [`meduzavpn-1.2.24-macos-universal.tar.gz`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-macos-universal.tar.gz) | command line — Apple silicon and Intel, signed and **notarized by Apple** |
| [`meduzavpn-1.2.24-windows.zip`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-windows.zip) | command line — x64 and ARM64 |

The full applications for macOS, Windows, iOS and Android are on
[meduzavpn.com](https://meduzavpn.com).

---

## Verifying what you downloaded

Every release ships `SHA256SUMS`:

```bash
curl -fsSLO https://github.com/txrx13/meduzavpn/releases/latest/download/SHA256SUMS
sha256sum -c SHA256SUMS --ignore-missing
```

The `.deb` and `.rpm` files in the repositories are covered by a signature chain rooted in our
key, and the RPMs are signed individually as well:

```
MeduzaVPN Package Signing <packages@meduzavpn.com>
B53E 4BF4 D6EF A6F0 E2B7  EF7B 4843 39BB 9BE9 9052
```

---

## About

MeduzaVPN is operated by IPFB LLC. This repository contains **compiled builds only** — no
source code is published here.

* Site and accounts — **[meduzavpn.com](https://meduzavpn.com)**
* Support — [meduzavpn.com/support](https://meduzavpn.com/support)
