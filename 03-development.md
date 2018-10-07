# Development

Tools for developing apps, websites, games, and other software.

- [Languages and Platforms](#languages-and-platforms)
	- [Ruby (RVM)](#ruby-rvm)
	- [Python (PyEnv)](#python-pyenv)
	- [Node (NVM)](#node-nvm)
	- [Go (GVM)](#go-gvm)
	- [Docker](#docker)
	- [VirtualBox](#virtualbox)
- [Editors and IDEs](#editors-and-ides)
	- [SublimeText 3](#sublimetext-3)
	- [Xcode](#xcode)
	- [Android Studio](#android-studio)
	- [Arduino](#arduino)
	- [Processing](#processing)
	- [Unity](#unity)
	- [IDEs for Unity](#ides-for-unity)
- [Tools and Utilities](#tools-and-utilities)
	- [Git](#git)
	- [Tower](#tower)
	- [wget](#wget)
	- [cURL](#curl)
	- [Wuzz](#wuzz)
	- [Insomnia](#insomnia)
	- [SequelPro (macOS)](#sequelpro-macos)
- [Terminals](#terminals)
	- [iTerm2 (macOS)](#iterm2-macos)
	- [PoSH-SSH (Windows)](#posh-ssh-windows)
- [Other](#other)
	- [Dash (macOS)](#dash-macos)

## Languages and Platforms

### Ruby (RVM)

```
brew install rbenv
mkdir -p ~/.rbenv
rbenv init - > ~/.rbenv/rbenv.sh
source ~/.rbenv/rbenv.sh # Add to shell profile to load on start
rbenv install 2.4.2
```

### Python (PyEnv)

```
brew install pyenv
mkdir -p .pyenv
source
source .pyenv/pyenv.sh # Add this line to your shell profile to load on start
# Fix for build errors
pyenv_install() {
  CFLAGS="-I$(brew --prefix openssl)/include" \
  LDFLAGS="-L$(brew --prefix openssl)/lib" \
  pyenv install "$1"
}
pyenv_install 2.7.12
pyenv_install 3.5.2
pyenv_install 3.6.2
pip install pylint
```

### Node (NVM)

```
brew install nvm
mkdir ~/.nvm
echo "export NVM_DIR=~/.nvm; source \"\$(brew --prefix nvm)/nvm.sh\"" > ~/.nvm/nvm.sh
source ~/.nvm/nvm.sh # Add this line to your shell profile to load on start
nvm install 8.5.0
nvm install 6.10.2
nvm use 6.10.2
```

### Go (GVM)

Go is an open source programming language that makes it easy to build simple, reliable, and efficient software.

Links:
- https://golang.org/

TODO: Rewrite for GVM

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew install go
if ! [[ `echo $PATH | sed 's/\:/ /g' | grep -o '[^ ]*\/go\/[^ ]*'` ]]; then
mkdir -p ~/.go
cat <<< "export GOPATH=$HOME/.go
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
" > ~/.go/go.sh
fi
source ~/.go/go.sh # Add this line to your shell profile to load on start
```

### Docker

Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications, whether on laptops, data center VMs, or the cloud.

Links:
- https://www.docker.com

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew install docker
brew install docker-compose
gem install docker-sync
brew install unison
```

*Windows 10+*
```powershell
#!powershell

# Install Docker Engine (there is a bug with LTS version, so we're use Edge version)
choco install docker-for-windows -my --pre --ignore-checksums

# Install Docker CLI
choco install docker docker-compose docker-machine -my

# Setup Docker Tab-Autocomplete
Set-ExecutionPolicy RemoteSigned
Install-Module posh-docker
Install-Module -Scope CurrentUser posh-docker
Import-Module posh-docker
if (-Not (Test-Path $PROFILE)) {
    New-Item $PROFILE –Type File –Force
}
Add-Content $PROFILE "`nImport-Module posh-docker"
```

*Ubuntu 16+*
```shell
#!/usr/bin/env bash
# See: https://docs.docker.com/engine/installation/linux/ubuntu/
sudo apt-get remove docker docker-engine
sudo apt-get update

sudo apt-get install \
linux-image-extra-$(uname -r) \
linux-image-extra-virtual

sudo apt-get install \
   apt-transport-https \
   ca-certificates \
   curl \
   software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) \
  stable"

sudo apt-get update
sudo apt-get install docker-ce
sudo usermod -aG docker $USER

# https://docs.docker.com/compose/install/
dockerComposeVersion=1.13.0
sudo curl -L https://github.com/docker/compose/releases/download/$dockerComposeVersion/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### VirtualBox

VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.

Links:
- https://www.virtualbox.org/wiki/VirtualBox

```shell
#!/usr/bin/env bash
brew cask install virtualbox
```

## Editors and IDEs

### SublimeText 3

Sublime Text is a sophisticated text editor for code, markup and prose.

Links:
- https://www.sublimetext.com/3

macOS
```shell
#!/usr/bin/env bash
brew cask install sublime-text
```

Windows
```powershell
#!powershell
choco install sublimetext3 -y
```

### Xcode

Xcode is an integrated development environment for macOS containing a suite of software development tools developed by Apple for developing software for macOS, iOS, watchOS and tvOS.

Links:
- https://developer.apple.com/xcode/

macOS
```shell
#!/usr/bin/env bash
mas install 497799835
# Accept license automatically
sudo xcodebuild -license accept
```

### Android Studio

Integrated Android developer tools for development and debugging.

Links:
- https://developer.android.com/studio/
- https://paolorotolo.github.io/android-studio/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install android-studio
```

*Ubuntu 16+*
```shell
#!/usr/bin/env bash
sudo apt-add-repository ppa:paolorotolo/android-studio
sudo apt-get update
sudo apt-get install android-studio
```

*Windows 10+*
```powershell
choco install AndroidStudio -y
```

### Arduino

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install arduino
```

*Windows 10+*
```powershell
choco install arduino -y
```

### Processing

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install processing
```

*Windows 10+*
```powershell
choco install Processing -y
```

### Unity

Unity is a cross-platform game engine developed by Unity Technologies[5] and used to develop video games for PC, consoles, mobile devices and websites.

Links:
- https://unity3d.com/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install unity
```

*Windows 10+*
```powershell
choco install unity -y
```

### IDEs for Unity

Install VS Code and Mono for Unity (Mono is required for VS Code to work properly)

```shell
#!/usr/bin/env bash
brew cask install visual-code-studio dotnet dotnet-sdk mono
code --install-extension ms-vscode.csharp
code --install-extension Tobiah.unity-tools
code --install-extension Unity.unity-debug
```

## Tools and Utilities

### Git

TODO: setup config files, authenticate, GPG signing

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew install git
curl -o ~/.gitignore_global https://raw.githubusercontent.com/github/gitignore/master/Global/macOS.gitignore
echo -e "# SublimeText\n*.sublime-workspace" >> ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

*Windows 10+*
```
#!powershell
choco install git -y
Invoke-WebRequest -OutFile $home\.gitignore_global https://raw.githubusercontent.com/github/gitignore/master/Global/Windows.gitignore
git config --global core.excludesfile $home\.gitignore_global
```

### Tower

TODO: setup config files, register

- Tower

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install tower
```

*Windows 10+*
```
#!powershell
choco install tower -y
```

### Bat

A cat clone with syntax highlighting and Git integration.

Links:
- https://github.com/sharkdp/bat

macOS
```shell
#!/usr/bin/env bash
brew install bat
```

### wget

GNU Wget is a free software package for retrieving files using HTTP, HTTPS and FTP, the most widely-used Internet protocols. It is a non-interactive commandline tool, so it may easily be called from scripts, cron jobs, terminals without X-Windows support, etc.

Links:
- https://www.gnu.org/software/wget/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew install wget
```

### cURL

Command line tool and library for transferring data with URLs.

Links:
- https://curl.haxx.se/

*cURL is installed on macOS and most Linux distributions by default.*

### Wuzz

Links:
- https://github.com/asciimoo/wuzz

*macOS 10.12+*
```shell
#!/usr/bin/env bash
go get github.com/asciimoo/wuzz
```

*Windows 10+*
```
#!powershell
Invoke-WebRequest -OutFile "C:\Program Files\wuzz.exe" "https://github.com/asciimoo/wuzz/releases/download/v0.3.0/wuzz_windows_386.exe"
```

*Ubuntu 16+*
```shell
#!/usr/bin/env bash
go get github.com/asciimoo/wuzz
```

### Insomnia

Debug APIs like a human, not a robot.

Links:
- https://insomnia.rest/

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install insomnia
```

### SequelPro (macOS)

Sequel Pro is a fast, easy-to-use Mac database management application for working with MySQL databases.

Links:
- https://www.sequelpro.com/

TODO: config file setup

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install sequel-pro
```

## Shell

Shells and customizations

### Case-insensitivity

Makes shell case insensitive

macOS, Linux
```shell
#!/usr/bin/env bash
if ! [ -f ~/.inputrc ] || [ "`cat ~/.inputrc | grep completion-ignore-case`" ]; then
    echo 'set completion-ignore-case On' >> ~/.inputrc
fi
```

### Hushlogin

Removes last login from new shells.

```shell
#!/usr/bin/env bash
touch ~/.hushlogin
```

### Profile

A suite of Bash shell scripts and customizations.

Links:
- https://github.com/martinharding/shell-profile

```shell
#!/usr/bin/env bash
git clone https://github.com/martinharding/shell-profile.git
./shell-profile/setup.sh
```

### OhMyZSH

TODO

## Terminals

### iTerm2 (macOS)

iTerm2 is a replacement for Terminal and the successor to iTerm.

Links:
- http://iterm2.com/

TODO: setup config files / sync

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install iterm2
```

### PoSH-SSH (Windows)

A PowerShell SSH module.

*Windows 10+*
```powershell
!#powershell
Find-Module Posh-SSH -y
Install-Module Posh-SSH -y
```

## Other

### Dash (macOS)

Dash is an API Documentation Browser and Code Snippet Manager.

Links:
- https://kapeli.com/dash

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install dash
```
