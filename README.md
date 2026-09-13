<p align="center">
  <img src="banner.svg" alt="MeduzaVPN — personal VPN on your own server" width="100%">
</p>

<p align="center">
  <a href="https://meduzavpn.com"><img alt="meduzavpn.com" src="https://img.shields.io/badge/meduzavpn.com-C37BD9?style=for-the-badge&labelColor=0A0E19"></a>
  <a href="https://github.com/txrx13/meduzavpn/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/txrx13/meduzavpn?style=for-the-badge&label=release&labelColor=0A0E19&color=8199D6"></a>
  <a href="#downloads"><img alt="Downloads" src="https://img.shields.io/badge/downloads-7%20files-5A7AB7?style=for-the-badge&labelColor=0A0E19"></a>
  <img alt="No source" src="https://img.shields.io/badge/builds%20only-no%20source-8199D6?style=for-the-badge&labelColor=0A0E19">
</p>

<h3 align="center">Your VPN. Your server. Your rules.</h3>

<p align="center">
  A VPN server that is <b>yours alone</b> — not a shared pool, not a crowded exit node.<br>
  You pick the country, we deploy the server, and nobody else is on it.
</p>

<p align="center">
  <b>This repository publishes the official builds and nothing else.</b><br>
  <sub>No source code is here, by design.</sub>
</p>

---

## Why a server of your own

A shared VPN puts thousands of people behind one address. That address collects rate limits,
CAPTCHAs and outright blocks because of what strangers did with it. A server of your own
carries only your reputation.

It also changes what a block can do to you. When one protocol stops working on your network,
you switch to another **on the same server**, in one tap — the server already speaks all of
them.

---

## Protocols

Every one of these runs on your server at the same time. Switching between them does not move
you to a different machine.

| Protocol | Windows | macOS | Linux | Android | iOS | Router |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| **MeduzaVPN** — our own, obfuscated | ✅ | ✅ | ✅ | ✅ | ✅ | — |
| **MeduzaVPN ULTRA** — multi-carrier transport | — | ✅ | — | ✅ | ✅ | — |
| **WireGuard** — fastest, easiest to recognise | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OpenVPN** — works almost everywhere | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **VLESS** — REALITY, looks like ordinary TLS | ✅ | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| **Xray** | ✅ | ✅ | ✅ | ⚠️ | ⚠️ | ⚠️ |
| **V2Ray** | ✅ | ✅ | ✅ | ⚠️ | ⚠️ | ⚠️ |
| **Hysteria 2** — QUIC, best on a lossy link | ✅ | ✅ | ✅ | ⚠️ | ⚠️ | ⚠️ |
| **Shadowsocks** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Outline VPN** | ✅ | ✅ | ✅ | ✅ | ✅ | — |
| **SOCKS5 proxy** | ⚠️ | ✅ | ✅ | ⚠️ | ⚠️ | ⚠️ |
| **IKEv2/IPsec** — built into the OS | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **OpenConnect** | ✅ | ✅ | ✅ | ⚠️ | — | ✅ |
| **SoftEther** | ✅ | — | ⚠️ | — | — | ⚠️ |

✅ supported · ⚠️ needs a third-party client, an older OS or compatible router firmware · — not supported

---

## Install on Linux

### From our repository — recommended

The repository resolves dependencies for you (the app pulls in the service by itself) and
upgrades with the rest of your system. Everything in it is signed with our key, and the key is
installed **before** the repository is added — a repository trusted first and verified later is
not verified at all.

<details open>
<summary><b>Debian · Ubuntu</b></summary>

```bash
curl -fsSL https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/meduzavpn-archive-keyring.asc \
  | sudo gpg --dearmor -o /usr/share/keyrings/meduzavpn.gpg

echo "deb [signed-by=/usr/share/keyrings/meduzavpn.gpg] https://meduzavpn-builds.fra1.digitaloceanspaces.com/repo/deb stable main" \
  | sudo tee /etc/apt/sources.list.d/meduzavpn.list

sudo apt update
sudo apt install meduzavpn-desktop   # the app (GUI) — pulls in the service
sudo apt install meduzavpn           # a server: command line and service only
```
</details>

<details open>
<summary><b>Fedora · CentOS · RHEL</b></summary>

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

sudo dnf install meduzavpn-desktop   # the app (GUI)
sudo dnf install meduzavpn           # command line and service only
```
</details>

<details>
<summary><b>Anything else</b> — Arch, openSUSE, NixOS, Alpine, a container</summary>

```bash
curl -fsSLO https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-158-linux-amd64.tar.gz
tar xzf meduzavpn-1.2.24-158-linux-amd64.tar.gz
cd meduzavpn-1.2.24-158-linux-amd64
sudo ./install.sh        # and ./uninstall.sh when you want it gone
```

The tarball carries compiled binaries, a systemd unit, an installer and an uninstaller — **not
source code**.
</details>

> [!NOTE]
> The service is never enabled for you. A VPN daemon that takes the default route a second
> after installation would be a rude surprise on a machine you reached over SSH.
> Start it when you are ready: `sudo systemctl enable --now meduzavpnd`

---

## <a id="downloads"></a>Downloads

Everything below is also on **[meduzavpn.com](https://meduzavpn.com)**.

### Linux — the app (GUI)

| File | For |
|---|---|
| [`meduzavpn-desktop_1.2.24-158_amd64.deb`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-desktop_1.2.24-158_amd64.deb) | Ubuntu, Debian |
| [`meduzavpn-desktop-1.2.24-158.x86_64.rpm`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-desktop-1.2.24-158.x86_64.rpm) | Fedora, CentOS, RHEL |

### Linux — command line and service (CLI)

| File | For |
|---|---|
| [`meduzavpn_1.2.24-158_amd64.deb`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn_1.2.24-158_amd64.deb) | Ubuntu, Debian |
| [`meduzavpn-1.2.24-158.x86_64.rpm`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-158.x86_64.rpm) | Fedora, CentOS, RHEL |
| [`meduzavpn-1.2.24-158-linux-amd64.tar.gz`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-158-linux-amd64.tar.gz) | everything else |

### Command line for macOS and Windows

| File | For |
|---|---|
| [`meduzavpn-1.2.24-macos-universal.tar.gz`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-macos-universal.tar.gz) | Apple silicon and Intel — signed and **notarized by Apple** |
| [`meduzavpn-1.2.24-windows.zip`](https://github.com/txrx13/meduzavpn/releases/latest/download/meduzavpn-1.2.24-windows.zip) | x64 and ARM64 |

> [!IMPORTANT]
> Taking a `.deb` or `.rpm` by hand? **The app package depends on the service package** —
> install both, or use the repository above and let it sort itself out.

The full desktop and mobile applications for macOS, Windows, iOS and Android are on
[meduzavpn.com](https://meduzavpn.com).

---

## The command line

The same `meduzavpn` binary on all three desktop systems. One invocation brings up any VPN on
your account, with no configuration file needed:

```bash
meduzavpn login --qr                          # scan the code with the phone app
meduzavpn list                                # your VPNs, the protocols, the settings in force
meduzavpn connect --protocol vless2 --wait
meduzavpn status
meduzavpn disconnect
```

Every setting resolves **flag → environment → config file → what the server's profile says**,
`--json` works everywhere for scripts, and the exit codes tell *not signed in* apart from *no
daemon* from *the server refused*.

On Linux the tunnel belongs to the `meduzavpnd` service. On macOS and Windows it belongs to the
application, and the command line drives it over a local socket — turn the command-line
interface on in the app's settings first.

---

## Verifying what you downloaded

Every release ships `SHA256SUMS`:

```bash
curl -fsSLO https://github.com/txrx13/meduzavpn/releases/latest/download/SHA256SUMS
sha256sum -c SHA256SUMS --ignore-missing
```

Packages in the repositories are covered by a signature chain rooted in our key, and each RPM
is signed individually as well:

```
MeduzaVPN Package Signing <packages@meduzavpn.com>
B53E 4BF4 D6EF A6F0 E2B7  EF7B 4843 39BB 9BE9 9052
```

---

<p align="center">
  <sub>
    MeduzaVPN is operated by IPFB LLC · <a href="https://meduzavpn.com">meduzavpn.com</a> ·
    <a href="https://meduzavpn.com/support">Support</a><br>
    This repository contains compiled builds only — no source code is published here.
  </sub>
</p>
