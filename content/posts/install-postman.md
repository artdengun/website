---
author: "Deni Gunawan"
date: 2020-11-14
linktitle: Cara Install Postman
title: Cara Install Postman
categories: [ "install"]
tags: ["Linux", "install", "Kali Linux","snap" , "postman","software"]
weight: 10
---
# Cara Install Postman via SNAP

- buka terminal dan ketikan 

```
sudo snap install postman
```

- unpackage dropbox yang sudah di download 

```
tar -xzf Postman-linux-x64-5.3.2.tar.gz
```
- hapus postman di /opt/Postman

```
sudo rm -rf /opt/Postman
```
- pindahkan Postman ke opt

```
sudo mv Postman /opt/Postman
```
- copy postman

```
sudo ln -s /opt/Postman/Postman /usr/bin/postman
```
- masuk ke folder application

```
 cd ~/.local/share/applications/ 
```
- buat file untuk postman desktop 

```
  touch postman.desktop
```
- isi dari file postman desktop

```
[Desktop Entry]
		Type=Application
		Version=1.0
		Name=Postman
		Comment=Supercharge your API workflow
		Icon=/opt/Postman/app/resources/app/assets/icon.png
		Exec="/opt/Postman/Postman"
```

*Selesai*
