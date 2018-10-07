# Essential

Absolutely essential software for any computer.

<!-- MarkdownTOC autolink=true bracket=round depth=3 -->

- [Package Managers](#package-managers)
	- [Homebrew (macOS)](#homebrew-macos)
	- [Brew Cask (macOS)](#brew-cask-macos)
	- [Mac App Store CLI (macOS)](#mac-app-store-cli-macos)
	- [Chocolatey (Windows)](#chocolatey-windows)
	- [scoop (Windows)](#scoop-windows)
	- [apt-get & yum (Linux)](#apt-get-yum-linux)
- [Internet](#internet)
	- [Google Chrome](#google-chrome)
	- [Mozilla FireFox](#mozilla-firefox)
	- [Lynx](#lynx)
	- [YakYak](#yakyak)
	- [Transmission](#transmission)
	- [OpenVPN Client](#openvpn-client)
	- [Chrome Remote Desktop](#chrome-remote-desktop)
- [Media](#media)
	- [VLC](#vlc)
	- [Audacity](#audacity)
- [Other](#other)
	- [1Password](#1password)
	- [iStat Menus (macOS)](#istat-menus-macos)
	- [Android File Transfer (macOS)](#android-file-transfer-macos)
	- [BetterSnapTool (macOS)](#bettersnaptool-macos)
	- [7-Zip (Windows)](#7-zip-windows)
	- [Java](#java)
	- [macOSuckless](#macosuckless)

<!-- /MarkdownTOC -->

## Package Managers

Installation of package managers for macOS, Windows 10, and Ubuntu

### Homebrew (macOS)

The missing package manager for macOS.

Links:
 - http://brew.sh/

*macOS 10.12+*
```bash
#!/usr/bin/env bash
! [ `command -v brew` ] && /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" || echo "brew already installed"
```

### Brew Cask (macOS)

Homebrew Cask extends Homebrew and brings its elegance, simplicity, and speed to macOS applications and large binaries alike.

Links:
 - https://caskroom.github.io/

*macOS 10.12+*
```bash
#!/usr/bin/env bash
brew tap caskroom/cask
```

### Mac App Store CLI (macOS)

A simple command line interface for the Mac App Store. Designed for scripting and automation.

Links:
 - https://github.com/mas-cli/mas

*macOS 10.12+*
```bash
#!/usr/bin/env bash
brew install mas
```

### Chocolatey (Windows)

The package manager for Windows.

Links:
 - https://chocolatey.org/

*Windows 10+*
```powershell
#!powershell
if (return [bool](Get-Command -Name chocolatey -ErrorAction SilentlyContinue)) { iex ((New-Object System.Net.WebClient).DownloadString("https://chocolatey.org/install.ps1")) }
```

### scoop (Windows)

Scoop installs the tools you know and love.

Links:
- http://scoop.sh/

```powershell
#!powershell
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

### apt-get & yum (Linux)

Make sure apt-get/yum is up to date.

*Ubuntu 16+*
```bash
#!/usr/bin/env bash
apt-get update
apt-get upgrade
```

## Internet

Applications for navigating the interwebs and being safe online.

### Google Chrome

Google Chrome is a freeware web browser developed by Google.

Links:
- https://www.google.com/chrome/browser/desktop/index.html

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install google-chrome
```

*Windows 10+*
```shell
#!powershell
choco install GoogleChrome
```

*Ubuntu 16+*
```bash
#!/usr/bin/env bash
apt-get update
apt-get upgrade
```

### Mozilla FireFox

Mozilla Firefox is a free and open-source web browser developed by the Mozilla Foundation and its subsidiary the Mozilla Corporation.

Links:
- https://www.mozilla.org/en-US/firefox/new/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install firefox
```

*Windows 10+*
```shell
#!powershell
choco install firefox
```

### Lynx

Lynx is a highly configurable text-based web browser for use on cursor-addressable character cell terminals.

Links:
- http://lynx.browser.org/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew install lynx
```

### YakYak


### Transmission

Transmission is a cross-platform BitTorrent client that is easy, lean, native, and powerful.

Links:
- https://transmissionbt.com/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install transmission
```

*Windows 10+*
```shell
#!powershell
choco install transmission
```

*Ubuntu 16+*
```shell
#!/usr/bin/env bash
apt-get install transmission-qt
```

### OpenVPN Client

Install Tunnelblick for macOS and OpenVPN-GUI for Windows.

Links:
- https://tunnelblick.net
- https://openvpn.net

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install tunnelblick
# TODO: Copy setup from Dropbox
```

### Chrome Remote Desktop

Links:
- https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en

```shell
#!/usr/bin/env bash
brew cask install chrome-remote-desktop-host
echo "Enable Chrome Remote Desktop host and install the Chrome browser extension to complete setup" && sleep 2
open "x-apple.systempreferences:com.google.chromeremotedesktop.preferences"
open "https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en" -a "Google Chrome"
```


## Media

Software for viewing and managing media.

### VLC

VLC is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVDs, Audio CDs, VCDs, and various streaming protocols.

Links:
- http://www.videolan.org/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install vlc
```

*Windows 10+*
```shell
#!powershell
choco install vlc
```

### Audacity

Audacity is a free, easy-to-use, multi-track audio editor and recorder for Windows, Mac OS X, GNU/Linux and other operating systems.

Links:
- http://www.audacityteam.org/

*macOS 10.12+*
```shell
url=https://www.dropbox.com/s/jzc5nhortvsvp25/audacity-macos-2.1.3.dmg?dl=1
filename=`basename $url | sed 's/\?dl\=1//g'`
[ ! -f ~/Downloads/$filename ] && curl -L -o ~/Downloads/$filename $url
checksum_expected=68e82a944a9aa29068e2a2faa4cbd85f909d48f3916e6a57983d14f605d88b5d
checksum_actual=`openssl sha -sha256 ~/Downloads/$filename | awk '{print $2}'`
if [[ "$checksum_expected" == "$checksum_actual" ]]; then
	mountname=`hdiutil attach ~/Downloads/$filename | grep Apple_HFS | cut -f 3-`
	cp -rf "$mountname/Audacity.app" /Applications/
else
	echo "Checksum did not match; expected $checksum_expected but got $checksum_actual" && exit 1
fi
```

## Other

### 1Password

1Password remembers them all for you. Save your passwords and log in to sites with a single click.

Links:
- https://1password.com/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install 1password
```

*Windows 10+*
```shell
#!powershell
cd $home\Downloads
Invoke-WebRequest -OutFile 1PasswordSetup.msi https://rink.hockeyapp.net/api/2/apps/0cb99692bcdb47abb89fad56dfd56d0c?format=zip
.\1PasswordSetup.msi
```

### iStat Menus (macOS)

An advanced Mac system monitor for your menubar.

Links:
- https://bjango.com/mac/istatmenus/

TODO: add config file setup.

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install istat-menus
```

### Android File Transfer (macOS)

Browse and transfer files between your Mac computer and your Android device.

Links:
- https://www.android.com/filetransfer/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install android-file-transfer
```

### BetterSnapTool (macOS)

TODO: copy setup files

*macOS 10.12+*
```shell
#!/usr/bin/env bash
mas install 417375580
```

### WinDock

Links:
- http://www.ivanyu.ca/windock/

*Windows 10+*
```powershell

```

### 7-Zip (Windows)

*Windows 10+*
```powershell
#!powershell
choco install 7zip
```

### Java

Java Development Kit and/or runtime environment; necessary for applications like Photoshop and Minecraft.

*Note: Installing Java via the JDK package will install it without the shitty browser adware (it's also the only way to install a JRE via the command line on macOS); this is why the JDK package is used instead of the consumer JRE package.*

Links:
- https://stackoverflow.com/a/29160633
- https://www.java.com/en/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install java
```

*Ubuntu 16+*
```shell
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
sudo apt-get install oracle-java8-set-default
```

*Windows 10+*
```powershell
#!powershell
choco install jdk8
```

### macOSuckless

Make macOS Suck Less.

Links:
- https://github.com/MartinHarding/macOSuckless

*macOS 10.12+*
```include
#!sead
https://github.com/MartinHarding/macOSuckless/glob/README.raw
```
