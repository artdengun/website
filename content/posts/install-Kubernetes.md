---
author: "Deni Gunawan"
date: 2020-11-14
linktitle: Cara Install Kubernetes
title: Cara Install Kubernetes
categories: [ "install"]
tags: ["Linux", "install", "Kali Linux","Kubernetes","software"]
weight: 10
---
# Cara Install Kubernetes 
- Update System 

```
sudo apt-get update
```

- Install Package apt-tranport-https

```
sudo apt-get install -y apt-transport-https
```

- Install Package virtualbox-ext-pack

```
sudo apt-get install -y virtualbox virtualbox-ext-pack
```
-  Install key 

```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```
- Buat file kubernetes list 

```
sudo touch /etc/apt/sources.list.d/kubernetes.list 
```
- download file 

```
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
```
- update system

```
sudo apt-get update

```
- download kubectl 

```
sudo apt-get install -y kubectl

```
- install minikube 

```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.28.2/minikube-linux-amd64
```
- pindahkan lokasi minikube

```
chmod +x minikube && sudo mv minikube /usr/local/bin/
```
- memulai minikube

```
minikube start
```
- lihat versi kubectl

```
kubectl api-versions
```

*Selesai*
