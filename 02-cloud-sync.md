# Cloud Sync

Sync files with cloud storage services

<!-- MarkdownTOC autolink=true bracket=round depth=3 -->

- [Dropbox](#dropbox)
	- [Install Dropbox](#install-dropbox)

<!-- /MarkdownTOC -->

## Dropbox

### Install Dropbox

Bring your photos, docs, and videos anywhere and keep your files safe.

*macOS 10.12+*
```shell
#!/usr/bin/env bash
brew cask install dropbox
open /Applications/Dropbox.app
echo "Note: you may want to wait for Dropbox to sync completely before continuing."
read -p "Please set up Dropbox and press [enter] to continue."
```

*Windows 10+*
```powershell
#!powershell
choco install dropbox
Dropbox.exe
echo "Note: you may want to wait for Dropbox to sync completely before continuing."
Read-Host -Prompt "Please set up Dropbox and press [enter] to continue."
```

*Ubuntu 16+*
```shell
#!/usr/bin/env bash
cd ~ && wget -O - "http://www.dropbox.com/download?plat=lnx.x86_64" | tar xz
~/.dropbox-dist/dropboxd
echo "Note: you may want to wait for Dropbox to sync completely before continuing."
read -p "Please set up Dropbox and press [enter] to continue."
```
