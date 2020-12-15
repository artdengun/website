---
title: "Java Standar Classes"
date: 2020-11-19T19:21:45+07:00
linktitle: Java Standar Classes
title: Java Standar Classes
categories: [ "Java", "Standar Classes"]
tags: ["Linux", "Java","SpringBoot"]
weight: 10
---

# Apa Itu Apache Kafka 
<hr>
Apache kafka merupakan salah satu aplikasi Message Broker yang secara garis besar digunakan untuk 
mengirim dan mengambil/menerima data secara realtime,

apache kafka memerlukan Apache Zookeeper tapi pada saat instalasi Zookper sudah ikut didalamnya. 

apabila di production kita perlu menginstall terpisah zookeeper dan kafka masing masisng . 

# Publish Subscribe 
<hr>
apa perlu menggunakan message broker? sangat perlu, kenapa? 
misal kita punya Aplikasi A sebagai pengirimnya dan B sebagai penerimanya, ditengah jalan kita membutuhkan penerima baru 
si C nah, tentunya kita perlu mencoding ulang Aplikasi A agar supaya bisa mengirim data ke C, tentunya hal ini membutuhkan
waktu development baru, untuk menghindari hal ini kita bisa menggunakan **Message Broker** kita cukup kirim data ke Message Broker
plikasi yang membutuhkan data / mengirim data cukup Listen ke message broker , kita cukup kirim data sekali, aplikasi yang membutuhkan data hanya listen 
di message broker .  

# Producer dan Consumer
<hr>
- Producer adalah pihak/aplikasi yang mengirim{publish} data ke Message Broker
- Consumer adalah pihak/aplikasi yang mengambil{subscribe} data ke Message Broker
- Aplikasi bisa bertindak sebagai Producer sekaligus Consumer Secara Bersamaan


# Arsitektur Kafka 
<hr>
 Teknologi Kafka
 
   - **producer** adalah  aplikasi yang mengirim data 
   - **consumer**  adalah aplikasi yang menerima data 
   - **connectors** adalah integrasi dengan existing aplikasi, contoh DB,  misal kita mau setiap data yang berubah maka akan dikirim ke kafka 
   - **Stream** proccesor adalah untuk mengolah data berupa stream -> stream data yang mengalir terus tanpa kita tahu kapan berhenti datanya, sekali kita mensubscibe data kita tidak tahu kapan berhentinya
   - **Cluster** merupakan kelompok dari beberapa aplikasi/borker yang saling bekerjasama.


# TOPIC 
<hr>
topic / table di database
 
 - Data di kafka disimpan dalam topic 
 - Analogi yang dekat untuk Topic, jika di database adalah Table
 - Data di Topic tidak bisa diubah



# Beberapa Istilah Penting diapache kafka 
<hr>

 - **Producer** merupakan proses atau sistem yang dapat mempublikasikan data ke suatu topik. 
 - **Consumer** merupakan proses atau sistem yang dapat melakukan subscription ke satu atau lebih topik dan mengolah data-data dari topik tersebut.
 - **Topic** merupakan nama dari sebuah feed dimana pesan/data di-
 - **Broker** merupakan instance Apache Kafka yang berjalan di satu mesin.
 - **Cluster** merupakan kelompok dari broker-broker/aplikasi yang saling bekerjasama.
 - **Partition** merupakan pengelompokkan data topic yang dipecah menjadi bagian-bagian kecil. Misalnya, suatu topik menyimpan informasi user login, maka data-data pada topik dapat dibagi bedasarkan huruf awal dari username.
 - **Offset** merupakan array index yang digunakan oleh Apache Kafka sebagai unique identifier untuk setiap data pada satu partisi.

