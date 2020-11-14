---
title: "Belajar Apache Kafka"
date: 2020-11-14T20:50:19+07:00
linktitle: Belajar Apache Kafka
title: Belajar Apache Kafka
categories: [ "Apache","Kafka"]
tags: ["Linux", "Apache", "Kafka","Message Broker","software","Backend"]
weight: 10
---

# Apa Itu Apache Kafka
  Apache kafka adalah salah satu Message Broker yang berguna untuk mengirimkan
  Message dan Menerima Message
    
##  Tahap Installation
  - download apache kafka [Download Disini](https://downloads.apache.org/kafka/2.5.0/kafka_2.12-2.5.0.tgz)
  
  - Extract Apache kafka file 
  
  ```
    tar -xzf kafka_2.12-2.5.0.tgz 
  ``` 
  
  - Masuk ke folder config 
  
  ```
    cd /kafka/config
  ```
  
  - Masuk ke config
    
   ```
    code config 
   ```
 - Edit Zooker.properties
 
    ```
    
    dataDir=data/zookeeper   <- Edit seperti ini 
    
    ```
 
 - Edit server.properties
   
    ```
     log.dirs=data/kafka	  <- Edit Seperti ini

    ```
 
 - Menjalankan Zookeeper **default properti 'localhost:2181'**
 
 ```
 ./bin/zookeeper-server-start.sh config/zookeeper.properties
 ```
 
- Menjalankan Kafka Server **default properti 'localhost:9092'**

```
./bin/kafka-server-start.sh config/server.properties   

```
## Bekerja Dengan Directory
- membuat Topic
```
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
```

- melihat Topic

```
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

-	Send Message to Cosumers from producers

```

```
## Bekerja Dengan Kafka 

- contoh scricpt producer
```java
public class Producer {
public static void main(String[] args) {
		Properties properties = new Properties();
				// ini data opsional bisa disesuaikan denga konfigurasi yang disesuaikan skenario
				//
       		 properties.put(ProducerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");  
				// file konfigurasi mengambil data dari ProducerConfig menggunakan perintah BOOTSTRAP_SERVERS_CONFIG
				// kemudian BOOTSTRAP_SERVERS_CONFIG ambil data dari server , disini kita menggunakan localhost:9092
				// untuk ambil data kita bisa sesuaikan dengan server yang kita gunakan	
      		  properties.put(ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG, StringSerializer.class.getName()); 
				// ini bersifat opsional
				// konversi string yang kita masukan ke binary data yang dimengerti oleh kafka
      		  properties.put(ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG, StringSerializer.class.getName()); 
				// 
				//       

				// serializer adalah menkonversi string yang kita masukan ke binary data 
      		  KafkaProducer<String, String> producer = new KafkaProducer<>(properties);
				// 1 key <String(1)	 		-> ini dari KEY_SERIALIZER_CLASS_CONFIG
				// 2 value , <String(2)>	-> ini VALUE_SERIALIZER_CLASS_CONFIG
        
        	for(int i = 0; i< 20; i++){
       		     ProducerRecord<String, String> record = new ProducerRecord<>("CostumerService", " data ke 1 " + i);
           	     producer.send(record);
					// ini untuk mengirim data
       		 }
        producer.close();
		// close jika data sudah dikirim
    }
}
```

- contoh script consumer

```java
public class consumer {

 public static void main(String[] args) {
     Properties properties = new Properties();
		// ini data opsional bisa disesuaikan denga konfigurasi yang disesuaikan skenario ( harus sama dengan producer)
		//
	     properties.setProperty(ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
		// file konfigurasi mengambil ( penting  -> lokasi dari kafkanya)
	     properties.setProperty(ConsumerConfig.GROUP_ID_CONFIG, "test");
		// menyebutkan group dara consumer dari grup idnya
	     properties.setProperty(ConsumerConfig.ENABLE_AUTO_COMMIT_CONFIG, "true");
		// auto commit secara otomatis 
	     properties.setProperty(ConsumerConfig.AUTO_COMMIT_INTERVAL_MS_CONFIG, "1000");
		// auto commitnya berapa lama 
	     properties.setProperty(ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG, "org.apache.kafka.common.serialization.StringDeserializer");
	     properties.setProperty(ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG, "org.apache.kafka.common.serialization.StringDeserializer");
		//  key dan value harus sama dengan producer String dan string
		//  jangan berbeda kan sangat berbahaya
        KafkaConsumer<String, String> consumer = new KafkaConsumer<>(properties);
     consumer.subscribe(Arrays.asList("CostumerService"));
	 // cara mensubcribe, consum bisa mengsubscirbe beberapa topic yang berbeda
	 // saran gunakan satu consumer untuk satu topik dan tidak lebih dan tidak terjadi erroy
	 // erroy karna perbedaan key dan value yang berbeda antar cosumer dan producer
     while (true) {
         ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(1000)); // ( 1 detik)
        // poll itu artinya ambil, Duration of ofMillis -> kalo datanya tidak ada kita mau menunggu berapa lama 
		// kalo datanya tidak ada dia akan mereturn data kosong
		 for (ConsumerRecord<String, String> record : records){
        // while (true) -> kita menggunakan method infinity loop pengulangan tanpa batas. 

                System.out.println("Received Number " + record.value());
             
            }
        }
    }
}
```
