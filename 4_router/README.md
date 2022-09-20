# **Analisis Router**

## Topologi Jaringan

Topologi di bawah terdiri dari 2 pc client dan 2 router dengan subneting.
[![topologi.png](https://i.postimg.cc/sX3LFSL4/topologi.png)](https://postimg.cc/GBSKGBd4)

## Configuration IP (PC)

[![2.png](https://i.postimg.cc/vmTJD5h8/2.png)](https://postimg.cc/wtKfGynn)

192.168.1.2 Subnet Mask -> 255.255.255.0 Gateway -> 192.168.1.1 (IP Router) PC1 : IP Address -> 192.168.3.2 Subnet Mask -> 255.255.255.0 Gateway -> 192.168.3.1 (IP Router)

[![3.png](https://i.postimg.cc/FHBPW8bm/3.png)](https://postimg.cc/VJXB57HH)

## Configuration Static Route (Router)

[![4.png](https://i.postimg.cc/8cbGLN6T/4.png)](https://postimg.cc/xNqB2r5Z)

Untuk setting static routing di cisco packet tracer menggunakan perintah : #ip route [destination] [subnet] [next hop address] Keterangan :

ip route : perintah membuat tabel routing static
destination : network jaringan yang dituju
subnet : subnet mask jaringan yang dituju
next hop address : ip dari router yang akan dilewati
IP Route (Router 0) : 192.168.3.0/24 via 192.168.2.2 [for sending packages or ping from PC0-192.168.1.2/24 to PC1-192.168.3.2/24] IP Route (Router 1) : 192.168.1.0/24 via 192.168.2.1 [for sending packages or ping from PC1-192.168.3.2/24 to PC0-192.168.1.2/24]

## Test Ping From Network 192.168.1.0/24 To 192.168.3.0/24 Or Reverse

[![5.png](https://i.postimg.cc/KjWNqgLf/5.png)](https://postimg.cc/RJcKqhgJ)

Terlihat ketika ping pertama dan kedua RTO (request time out) karena untuk pertama kali pada layer data-link mac belum ada sehingga ping tersebut ditunda dan digantikan dengan package broadcast untuk dari PC 0 (192.168.1.2/24) ke Router 0 (192.168.1.1/24) -> untuk RTO pertama. Sementara RTO kedua digantikan dengan packgage broadcast dari Router 0 (192.168.2.1/24) ke Router 1 (192.168.2.2/24) untuk mendapatkan MAC / Phsyical Address. Terlihat pada arp -a (arpa cache) pada PC0 (192.168.1.2/24) memiliki daftar arp yaitu 192.168.1.1 (IP Router 0) dengan Physical / MAC Address

## Test Ping From Network 192.168.1.0/24 To 192.168.3.0/24 Atau Sebaliknya

[![6.png](https://i.postimg.cc/J7QtNLmy/6.png)](https://postimg.cc/SjJy4Hnq)
Ping-PC1-To-PC0.png Terlihat gambar di atas PC1-192.168.3.2/24 tidak memalukan request ping dan hanya replay ping sebelumnya dari PC0-192.168.1.2/24 dan sudah memiliki daftar arp cache yaitu IP 192.168.3.1 (Router 1) dengan Physical / MAC Address 0001.9724.4801 sehingga untuk melakukan ping pada PC1-192.168.3.2/24 ke PC1-192.168.1.2/24 tidak terjadi RTO lagi karena setiap pc sudah memliki destinasi ip yang bisa menngirim pada paket tersebut.
