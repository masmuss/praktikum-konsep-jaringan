# **Cisco packet tracer**

Pertama kita akan membuat rangkaian jaringan seperti dibawah ini dengan rincian:

1. 1 buah Hub
2. PC1 dengan alamat ip `192.168.1.1`
3. PC2 dengan alamat ip `192.168.1.2`
4. PC3 dengan alamat ip `192.168.1.3`

[![image.png](https://i.postimg.cc/zGdBrLVX/image.png)](https://postimg.cc/LJ1Rk8tr)

Sebelum memulai percobaan, kita harus mengatur beberapa hal seperti:

1. Set ke **simulation**

   [![image.png](https://i.postimg.cc/NMnT1123/image.png)](https://postimg.cc/zbnVNHj7)

2. Klik pada tombol "Show All/None", lalu "Edit Filters"
   [![image.png](https://i.postimg.cc/sxyBPwD0/image.png)](https://postimg.cc/sQ6DsPWp)

   Centang pada `ARP` dan `ICMP`, lalu close.

## Skenario Pertama `(PC1 => PC2)`

Pada skenario pertama, PC1 belum menyimpan ARP cache. Untuk mengecek cache dari ARP, bisa menggunakan perintah `arp -a` di cmd

[![image.png](https://i.postimg.cc/zDcZg3tT/image.png)](https://postimg.cc/5jLRc9Mt)

[![image.png](https://i.postimg.cc/qvc5j7Lb/image.png)](https://postimg.cc/tsTkgp8W)

Karena dari ARP sendiri masih belum memiliki ARP cache kita perlu melakukan adanya broadcast yang akan mencari semua device yang terhubung berdasarkan MAC addres

-  Proses Ping memulai permintaan ping berikutnya.
-  Proses Ping membuat pesan ICMP Echo Request dan mengirimkannya ke proses yang lebih rendah.
-  Alamat IP sumber tidak ditentukan. Perangkat menyetelnya ke alamat IP port.
-  Alamat IP tujuan berada di subnet yang sama. Perangkat mengatur hop berikutnya ke tujuan.
-  Proses ARP membuat permintaan untuk alamat IP target.
-  Perangkat merangkum PDU ke dalam bingkai Ethernet.

[![image.png](https://i.postimg.cc/nLCwZ1x5/image.png)](https://postimg.cc/B8fCBHXc)

Selanjutnya frame paket akan di dapatkan ke MAC Addres yang di tuju dan MAC adress yang bukan dari tujuan akan di drop. dan paket yang telah di terima oleh penerima MAC Address tujuan maka akan melakukan reply dengan broadcast hal yang sama di lakukan dengan PC1 yang akan menerima paket tersebut dan ARP akan memetakan logical ke pysical selanjutnya kita cek apakah ARP cache pada PC1 sudah tersimpan atau belum

[![image.png](https://i.postimg.cc/MHN171Nc/image.png)](https://postimg.cc/n9KsZ9HZ)

## Skenario Kedua `(PC1 => PC2)` Apakah akan terjadi broadcast lagi?

Dengan adanya cache ARP itu maka arp akan memetakan MAC dan tentunya tidak di perlukan lagi broadcast, kita bisa melihatnya menggunakan perintah `arp -a`

[![image.png](https://i.postimg.cc/MHN171Nc/image.png)](https://postimg.cc/n9KsZ9HZ)

Di situ bisa kita lihat bahwa pada PC1 sudah memiliki MAC Address dari PC2

[![image.png](https://i.postimg.cc/bYg1PCHw/image.png)](https://postimg.cc/G9B4Jj5W)

Bisa dilihat bahwa pada layer tiga dest IP ICMP sudah bisa langsung di dapatkan. Tentu saja jawaban nya komputer tidak perlu lagi melakukan broadcast karene sudab di ada di cache ARP

## Skenario Ketiga `(PC2 => PC1)`

Kita harus melihat pada saat broadcast pertama pada saat PC1 melakukan broadcast dan PC lain yang menerima frame broadcast akan memberi response, tentu saja secara otomatis pada PC2 juga perlu melakukan broadcast sehingga pada tahap tersebut ARP juga mencatat hasil broadcast dari hasil response ke PC1

untuk melihatnya coba kita ketik perintah `arp -a` pada PC2

[![image.png](https://i.postimg.cc/PqFrKDmh/image.png)](https://postimg.cc/nsBJhCRw)

Bisa diketahui bahwa PC2 memiliki ARP dari PC1 sehingga tidak diperlukan broadcast.
