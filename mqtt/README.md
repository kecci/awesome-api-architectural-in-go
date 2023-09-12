## Apa itu MQTT?

MQTT adalah protokol pesan berbasis standar, atau seperangkat aturan, yang digunakan untuk komunikasi mesin-ke-mesin. Sensor pintar, perangkat yang dapat dikenakan, dan perangkat Internet untuk Segala (IoT) lainnya biasanya harus mengirim dan menerima data melalui jaringan dengan sumber daya dan bandwidth terbatas. Perangkat IoT ini menggunakan MQTT untuk transmisi data, karena mudah diterapkan dan dapat mengomunikasikan data IoT secara efisien. MQTT mendukung pengiriman pesan antara perangkat ke cloud dan cloud ke perangkat.

## Apa itu komponen MQTT?

MQTT menerapkan model publikasi/berlangganan dengan menentukan klien dan broker seperti di bawah ini.

### Klien MQTT

Klien MQTT adalah setiap perangkat dari server ke mikrokontroler yang menjalankan pustaka MQTT. Jika klien mengirim pesan, ia bertindak sebagai penerbit, dan jika klien menerima pesan, ia bertindak sebagai penerima. Pada dasarnya, perangkat apa pun yang berkomunikasi menggunakan MQTT melalui jaringan dapat disebut perangkat klien MQTT.

### Broker MQTT

Broker MQTT adalah sistem backend yang mengoordinasikan pesan antara klien yang berbeda. Tanggung jawab broker meliputi menerima dan memfilter pesan, mengidentifikasi klien yang berlangganan setiap pesan, serta mengirimi pesan kepada klien. Broker juga bertanggung jawab untuk tugas-tugas lain seperti:
- Mengotorisasi dan mengautentikasi klien MQTT
- Mengirim pesan ke sistem lain untuk analisis lebih lanjut
- Menangani pesan tak terjawab dan sesi klien

### Koneksi MQTT

Klien dan broker mulai berkomunikasi dengan menggunakan koneksi MQTT. Klien memulai koneksi dengan mengirimkan pesan CONNECT ke broker MQTT. Broker mengonfirmasi bahwa koneksi telah dibuat dengan merespons menggunakan pesan CONNACK. Baik klien MQTT maupun broker memerlukan tumpukan TCP/IP untuk berkomunikasi. Klien tidak pernah terhubung satu sama lain, hanya dengan broker.

## Bagaimana cara kerja MQTT?

Gambaran umum mengenai cara kerja MQTT diberikan di bawah ini. 

    Klien MQTT membuat koneksi dengan broker MQTT.
    Setelah terhubung, klien dapat memublikasikan pesan, berlangganan pesan tertentu, atau melakukan keduanya.
    Saat broker MQTT menerima pesan, broker meneruskan pesan tersebut ke pelanggan yang tertarik.

Mari kita uraikan detailnya untuk pemahaman lebih lanjut.

### Topik MQTT

Istilah 'topik' mengacu pada kata kunci yang digunakan broker MQTT untuk memfilter pesan bagi klien MQTT. Topik diatur secara hierarki, mirip dengan direktori file atau folder. Misalnya, mempertimbangkan sistem rumah pintar yang beroperasi di rumah bertingkat, dan rumah tersebut memiliki perangkat pintar yang berbeda di setiap lantainya. Dalam hal ini, broker MQTT dapat mengatur topik sebagai:
```
rumahkami/lantaidasar/ruangtamu/lampu

rumahkami/lantaipertama/dapur/suhu
```

### Publikasi di MQTT

Klien MQTT memublikasikan pesan yang berisi topik dan data dalam format bita. Klien menentukan format data seperti data teks, data biner, XML, atau file JSON. Misalnya, lampu di sistem rumah pintar dapat memublikasikan pesan menyalauntuk topik ruangtamu/lampu.

### Berlangganan di MQTT

Klien MQTT mengirimkan pesan BERLANGGANAN ke broker MQTT, untuk menerima pesan mengenai topik yang menarik. Pesan ini berisi pengenal unik dan daftar langganan. Misalnya, aplikasi rumah pintar di ponsel Anda ingin menampilkan jumlah lampu yang menyala di rumah. Aplikasi ini akan berlangganan ke topik lampu dan meningkatkan penghitung untuk semua pesan menyala. 

## Reference
- https://aws.amazon.com/id/what-is/mqtt/