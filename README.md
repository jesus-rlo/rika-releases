# rika releases

**rika** is a desktop app for Android TV and Google TV. It finds TVs on your network, backs them up, turns off preloaded bloat (reversibly), and installs custom launchers such as Luma TV, Projectivy or FLauncher. Every change it makes can be undone.

This repository holds only rika's **installer files and release notes**. Installed copies of rika check it for updates. There is no source code here.

**[Download the latest release »](https://github.com/jesus-rlo/rika-releases/releases/latest)**

## Install

Each release has three files:

| File | For |
|---|---|
| `rika_X.Y.Z_all.deb` | Ubuntu, Debian, Linux Mint, Pop!_OS (recommended) |
| `rika-X.Y.Z.tar.gz` | Any Linux, installed for your user without root |
| `SHA256SUMS` | Checksums of the two files above |

**Ubuntu and Debian:** download the `.deb` from the [latest release](https://github.com/jesus-rlo/rika-releases/releases/latest), then:

```bash
sudo apt install ./rika_X.Y.Z_all.deb
```

apt also installs `adb` and the window libraries rika uses. Open **rika** from your apps. To remove it: `sudo apt remove rika`.

**Any Linux, without root:**

```bash
tar xf rika-X.Y.Z.tar.gz && cd rika-X.Y.Z && ./install.sh
```

This adds rika to your apps menu. You need Python 3.9 or newer and `adb` (`sudo apt install adb`, or `android-tools` on Fedora and Arch). Remove it with `./install.sh --uninstall`.

rika opens in its own window when Chrome, Chromium, Brave, Edge or Vivaldi is installed, otherwise in a native GTK window or your browser. To look around without a TV, right-click rika in your apps and choose **Try with simulated TVs**.

## Check a download

Put `SHA256SUMS` next to the files you downloaded and run:

```bash
sha256sum -c SHA256SUMS --ignore-missing
```

Each file you have should print `OK`.

## Updates

rika v1.3.0 and newer check this repository about once a day. When a new release appears, **Update available** shows in rika's sidebar. Installing it downloads the right file from here over HTTPS, checks it against `SHA256SUMS`, installs it (apt asks for your password for the `.deb`), and restarts rika. No GitHub account or token is needed.

Versions before v1.3.0 looked for updates elsewhere: install v1.3.0 or newer from here once, and later updates arrive by themselves.

## Before you start: prepare the TV

1. On the TV: Settings › Device Preferences › About, select **Build** seven times.
2. Settings › Device Preferences › **Developer options**: turn on **USB debugging** (Sony and most Android TVs) or **Network debugging**.
3. In rika: **Find TVs** › **Scan network** › **Connect**. The TV asks "Allow USB debugging?". Tick *Always allow from this computer* and choose *Allow*.

On Google TV, the build number is under Settings › System › About › Android TV OS build.

## Security

rika runs a small web server for its own window, reachable only from your computer and protected by a per-session token. It validates everything it sends to a TV, and installs updates only from this repository's releases, over HTTPS, when the checksum matches.

If you find a security problem, please contact [@jesus-rlo](https://github.com/jesus-rlo) privately rather than opening a public issue.
