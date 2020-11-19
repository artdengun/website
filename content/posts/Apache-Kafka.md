---
title: "Apache Kafka"
date: 2020-11-19T19:21:45+07:00
linktitle: Apache Kafka
title: Apache Kafka
categories: [ "Java", "Apache Kafka"]
tags: ["Linux", "Java","Message Broker", "SpringBoot"]
weight: 10
---

# Apa Itu Apache Kafka 
Apache kafka adalah sistem untuk mengirim dan mengambil/menerima data secara realtime 
![gambar](./static/img/apachekafka.png)
# Beberapa Istilah Penting diapache kafka 

 - **Producer** merupakan proses atau sistem yang dapat mempublikasikan data ke suatu topik. 
 - **Consumer** merupakan proses atau sistem yang dapat melakukan subscription ke satu atau lebih topik dan mengolah data-data dari topik tersebut.
 - **Topic** merupakan nama dari sebuah feed dimana pesan/data di-
 - **Broker** merupakan instance Apache Kafka yang berjalan di satu mesin.
 - **Cluster** merupakan kelompok dari broker-broker yang saling bekerjasama.
 - **Partition** merupakan pengelompokkan data topic yang dipecah menjadi bagian-bagian kecil. Misalnya, suatu topik menyimpan informasi user login, maka data-data pada topik dapat dibagi bedasarkan huruf awal dari username.
 - **Offset** merupakan array index yang digunakan oleh Apache Kafka sebagai unique identifier untuk setiap data pada satu partisi.

