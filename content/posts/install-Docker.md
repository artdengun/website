---
author: "Deni Gunawan"
date: 2020-11-14
linktitle: Cara Install Docker
title: Cara Install Docker
categories: [ "install"]
tags: ["Linux", "install", "Kali Linux","Docker","software"]
weight: 10
---
# Cara Install Docker

- install  package pendukung 

```
sudo apt-get install  curl apt-transport-https ca-certificates 
	 software-properties-common 
```
- install docker.io

```
sudo apt install -y docker.io
``` 
- Enable docker di sistem 

```
sudo systemctl enable docker --now
```
- agar docker bisa di akses semua user bukan hanya oleh superuser

```
sudo usermod -aG docker $USER
```

*Selesai*
