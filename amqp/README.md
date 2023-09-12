## Apa itu AMQP?
AMQP singkatan dari 'Advanced Messaging Queuing Protocol' merupakan desain standar pertukaran pesan (messaging) yang mendukung efisiensi penentuan proses pertukaran pesan (messaging) pada aplikasi atau komunikasi data yang beragam. 

## AMQP Core Elements
1. Connections (network layer strwam transport : TCP, SCTP atau Pipes)
2. Sessions ( Binds two undirectional channels to form a bidirectional, sequential conversation).
3. Link (Named undirectional transfer route for message from resource to target node).


## Message-Transfer
Cara penyelesaian ada 2 jenis, yaitu :
1, At-most-once/Fire-And-Forget : yaitu pertukaran/pengiriman yang sama di lakukan hanya sekali saja atau paling banyak hanya sekali.
At-Least-Once : yaitu Proses pertukaran/pengiriman data yang sama dapat dilakukan secara berkali-kali atau paling sedikit sekali.

Status Pengiriman dapat di bagi menjadi beberapa bagian, yaitu :
1. Intermediary State (Status messaging sedang bverjalan atau on-progress).
2. Terminal State (Status ketika proses messaging dianggap selesai)
   1. Accepted (Pesan telah diterima oleh si consumer).
   2. Rejected (Si consumer menolak pesan yang dikirimkan kepada dia ole si producer).
   3. Released (Pesan tidak dipedulikan (abandoned) oleh si consumer sehingga bila perlu si producer harus mengirim ulang pesan tersebut).
   4. Modified (pesan sudah di released dan perlu di ubah/modify sesuai dengan indikasi yang tertera pada detail pesan).

Terminology AMQP sebagai berikut :

- Broker : merupakan sebuah applikasi yang menerapkan model AMQP yang menerima koneksi dari klien dan digunakan sebagai applikasi untuk message routing, Queue lain-lain.
- Message : pesan/content dari data yang di transfer/routing yang mengandung beberpa informasi seperti payload, attribute dan sebagainya.
- Producer : Sebuah applikasi yang meletakkan/mengirimkan pesan ke Queue melalui exchange.
- Consumer : Sebuah Applikasi yang memiliki role untuk menerima/mengambil pesan yang telah dikirimkan oleh si producer dan ada di Queue.


Bagian Komponen:
- Exchange : Bagian dari broker yang menerapkan AMQP model yang bertugas menerima pesan dan meletakkannya kedalam Queue
- Queue (Message Queue) : Sebuah Entity yang bertugas menampung pesan dan consumer mana yang akan menerima pesan tersebut
- Bindings : Bertugas mendistribusikan pesan dari Exchanges ke Queue.


Beberapa Bentuk peletakan data dari Exchange ke Queue adalah sebagai Berikut :
- Direct : Message akan di route alngsung ke Queue yang ada yang terdaftar pada Key message. Sehingga ketika key diterima maka pesan akan langsung dikirimkan ke Queue sesuai dengan Key tersebut.
- Topic : Message akan di route berdasarkan pattern dan key yang ada dan bersifat publish (publish subscribe), sehingga exchange akan meletakkan pesan kesetiap queue sesuai dengan key + pattern yang ada.
- Fanout : Peletakan data yang tidak bergantung pada key ataupun pattern. Pesan yang diterima akan langsung di publish kesemua Queue yang terdapat pada broker.


Jika kita ingin menerapakan model AMQP init pada proses messaging, maka kita harus menggunakan Broker APpp yang sudah menerapakan model ini. Berikut adalah beberapa Message Broker yang menerapkan AMQP adalah :
- ActiveMQ 
- RabbitMQ
- QPID (Apache foundation)
- OpenAMQ
- StormAMQ
- Solace Cloud
- Solace
- JORAM