<p align="center">
  <img src="banner.svg" alt="MeduzaVPN — personal VPN on your own server" width="100%">
</p>

<p align="center">
  <a href="https://meduzavpn.com"><img alt="meduzavpn.com" src="https://img.shields.io/badge/meduzavpn.com-C37BD9?style=for-the-badge&labelColor=0A0E19"></a>
  <a href="https://github.com/txrx13/meduzavpn/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/txrx13/meduzavpn?style=for-the-badge&label=release&labelColor=0A0E19&color=8199D6"></a>
  <a href="#downloads"><img alt="Downloads" src="https://img.shields.io/badge/downloads-apps%20%26%20CLI-5A7AB7?style=for-the-badge&labelColor=0A0E19"></a>
  <img alt="No source" src="https://img.shields.io/badge/builds%20only-no%20source-8199D6?style=for-the-badge&labelColor=0A0E19">
</p>

<h3 align="center">One account. Your devices. A choice of VPN protocols.</h3>

<p align="center">
  Official MeduzaVPN applications and command-line tools.<br>
  Choose a VPN location and protocol, manage your services, and connect from your devices.
</p>

<p align="center">
  <b>This repository distributes compiled releases and documentation.</b><br>
  <sub>The application source code is maintained separately and is not published here.</sub>
</p>

---

## What is new

**Build 170 is available** in iOS TestFlight, Android internal testing/APK, Linux GUI/CLI direct downloads, and Windows CLI. macOS distribution, the Windows graphical installer, and the apt/dnf repository update are still pending. The repositories currently serve build 158; use the direct Linux packages for 170. See the [170 release notes](https://github.com/txrx13/meduzavpn/releases/tag/v1.2.24-170) for the exact files and validation.

- **MeduzaVPN ULTRA:** updated iOS flow admission and DNS handling under load, bounded memory accounting, preservation of active one-way UDP sessions, and non-blocking ICMP connection setup.
- **Network recovery:** iOS and Android reconnect ULTRA when the active physical network changes or returns after going offline.
- **Protocol selection:** ULTRA appears above the alphabetical list; VLESS and VLESS 2.0 are in the general list. Display order does not change an existing protocol selection.
- **Connection settings:** IPv4/IPv6 controls where supported, configuration-file and QR sharing, and a visible countdown until an IP address can be changed again.
- **Desktop and command line:** graphical applications, Linux service packages, and CLI downloads for Linux, macOS and Windows.

Availability depends on the platform, installed build, server configuration and account access. Test builds and public store releases can have different version numbers; check the release notes for the exact artifacts and channels.

### ULTRA validation

The iOS changes were checked with repeated downloads, DNS requests under flow pressure, TCP/UDP tests and platform lifecycle tests. A controlled 200 Mbps fixture completed ten rounds at approximately 188–189 Mbps without HTTPS errors. This is a laboratory result, not a guarantee of a particular speed on a phone or mobile network. The reported iPhone slowdown still needs device verification. Release notes retain known test limitations.

## Protocols

MeduzaVPN clients offer protocols supported by the selected platform and service, including **MeduzaVPN**, **MeduzaVPN ULTRA**, **WireGuard**, **OpenVPN**, **VLESS**, **VLESS 2.0 (XHTTP + REALITY)**, **Hysteria 2**, **Xray/V2Ray**, **Shadowsocks**, **Outline**, **SOCKS5**, and **SoftEther**. System IKEv2/IPsec support depends on the operating system.

ULTRA's graphical client integration is available on **iOS, Android and macOS** when enabled in the release. Windows and Linux GUI builds do not gain ULTRA merely by sharing the application version. The Linux CLI/service has a separate ULTRA implementation and requires the corresponding release configuration and device enrollment. A CLI on macOS or Windows controls the installed application rather than supplying a separate VPN engine.

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
curl -fsSLO https://meduzavpn-builds.fra1.digitaloceanspaces.com/latest/meduzavpn-linux-amd64.tar.gz
mkdir meduzavpn-install
tar xzf meduzavpn-linux-amd64.tar.gz -C meduzavpn-install --strip-components=1
cd meduzavpn-install
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

### Applications and testing

| Platform / channel | Download |
|---|---|
| iOS public store | [App Store](https://apps.apple.com/us/app/meduzavpn/id6755959724) |
| iOS and macOS beta | TestFlight; access is managed through the existing tester groups |
| Android public store | [Google Play](https://play.google.com/store/apps/details?id=app.meduzavpn) |
| Android beta | [Google Play testing](https://play.google.com/apps/testing/app.meduzavpn) — sign in with an invited tester account |
| macOS direct installer | [Signed, notarized DMG](https://meduzavpn.com/download/macos) |
| Android direct installer | [Release-signed APK](https://meduzavpn.com/download/android) |
| Windows graphical app | [Windows installer](https://meduzavpn.com/download/windows) |
| Linux graphical app | [DEB](https://meduzavpn.com/download/linux-desktop-deb) · [RPM](https://meduzavpn.com/download/linux-desktop-rpm) |

### Command line and Linux service

| Platform | Download |
|---|---|
| Linux CLI + daemon | [DEB](https://meduzavpn.com/download/linux-deb) · [RPM](https://meduzavpn.com/download/linux-rpm) · [tar.gz](https://meduzavpn.com/download/linux-tar) |
| macOS CLI | [Universal archive](https://meduzavpn.com/download/cli-macos) |
| Windows CLI | [Windows archive](https://meduzavpn.com/download/cli-windows) |

Versioned files and their SHA-256 checksums are listed in [GitHub Releases](https://github.com/txrx13/meduzavpn/releases). The website links above remain stable between releases. See each release's asset list for the architectures actually provided.

> [!IMPORTANT]
> Installing Linux files manually? The graphical `meduzavpn-desktop` package depends on the `meduzavpn` service package. Install both, or use the signed repository above to resolve dependencies.

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
