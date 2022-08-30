# **1. Dasar teori**

Jaringan komputer (jaringan) adalah jaringan telekomunikasi yang memungkinkan antar komputer untuk saling berkomunikasi dengan bertukar data. Tujuan dari jaringan komputer adalah agar dapat mencapai tujuannya, setiap bagian dari jaringan komputer dapat meminta dan memberikan layanan (service).

Dalam transaksi data atau terhubungan ke dalam internet terdapat layer seperti OSI Layer dan TCP/IP. Model OSI membagi trafik jaringan menjadi beberapa lapisan. Setiap lapisan berdiri sendiri, tidak tergantung pada lapisan yang lain, dan masing-masing membangun berbasis pada jasa layer dibawahnya dan memberikan jasa pada lapisan di atasnya. Berikut adalah catatan singkat ke tujuh lapisan model jaringan OSI:

1. Fisik (mengacu pada media fisik dimana komunikasi terjadi dapat berupa kabel LAN CAT5, sekumpulan kabel fiber optik, gelombang radio, pada dasarnya medium yang dapat digunakan untuk mengirimkan sinyal).
2. Data Link (Pada saat dua atau lebih node berbagi media fisik yang sama, contoh, beberapa komputer tersambung ke sebuah hub, atau sebuah ruangan yang penuh dengan peralatan wireless yang semua menggunakan kanal yang sama, maka mereka akan menggunakan lapisan data link untuk berkomunikasi satu sama lain. Contoh protokol data link yang sering digunakan adalah Ethernet, Token Ring, ATM, dan protokol jaringan wireless (802.11a/b/g)).
3. Jaringan (Lapisan ini adalah lapisan dimana proses routing terjadi. Paket akan meninggalkan sambungan jaringan lokal dan di kirim ulang ke jaringan lain).
4. Transport (Memberikan metoda untuk mencapai jasa tertentu di sebuah node di jaringan. Contoh protokol yang bekerja pada lapisan ini adalah TCP dan UDP).
5. Sesi (Mengatur sesi komunikasi secara logika (virtual) antara aplikasi. NetBIOS dan RPC adalah dua (2) contoh dari protokol di lapisan nomor lima).
6. Presentasi (Berurusan dengan presentasi data, sebelum data mencapai lapisan aplikasi. Pekerjaan di lapisan ini dapat berupa MIME enkoding, kompresi data, pengecekan format, pengurutan byte dsb).
7. Aplikasi (Pada lapisan ini interaksi dengan manusia dilakukan. HTTP, FTP, dan SMTP adalah contoh protokol di lapisan aplikasi).

## 1.1 Media jaringan komputer

Dalam sebuah media jaringan, beberapa jenis yang umum digunakan, antara lain kabel tembaga _(copper)_, kabel optik _(fiber optic)_, serta kabel nirkabel dan LAN. Namun yang paling umum digunakan adalah kabel LAN untuk menghubungkan jaringan lokal untuk saling terhubung. Ada dua jenis kabel LAN yaitu STP _(Shield Twisted Pair)_ dan UTP _(Unshield Twisted Pair)_.

### STP _(Shield Twisted Pair)_

STP banyak digunakan untuk kondisi khusus. Kabel STP umumnya digunakan di perangkat elektronik seperti televisi, radio, komputer, hingga telepon. Dengan demikian, hanya alasan khusus yang membutuhkan media ini sebagai media transmisi. Pemasangan kabel STP lebih rumit daripada UTP dan relatif lebih mahal.

### UTP _(Unshield Twisted Pair)_

UTP adalah empat pasang kabel yang digunakan pada jaringan yang berbeda. Masing-masing dari 8 kawat tembaga dalam kabel UTP dilapisi dengan bahan isolasi dan masing-masing kawat dipilin (twisted) bersama-sama. Disebut unshielded karena ketahanannya yang lebih rendah terhadap interferensi elektromagnetik.

## 1.2 Standar kabel UTP

Pemberian kategori 1/2/3/4/5/5e/6 merupakan kategori spesifikasi untuk masing-masing kabel tembaga dan juga untuk jack. Berikut penjelasan singkat kegunaan setiap kateogri kabel UTP:

-  Cat 1 (Untuk koneksi suara / sambungan telepon).
-  Cat 2 (Untuk protocol localtalk (Apple) dengan kecepatan data hingga 4 Mbps).
-  Cat 3 (Untuk protocol ethernet dengan kecepatan data hingga 10 Mbps).
-  Cat 4 (Untuk protocol 16 Mbps token ring (IBM) dengan kecepatan data hingga 20 Mbps).
-  Cat 5 (Untuk protocol fast ethernet dengan kecepatan data hingga 100 Mbps).
-  Cat 5e (Untuk protocol fast ethernet dengan kecepatan data hingga 250 Mbps).
-  Cat 6 (Untuk protocol fast ethernet dengan kecepatan data hingga 10 Gbit/s).

## 1.3 Koneksi dengan kabel UTP

Pemasangan urutan kabel UTP umunya mengikuti aturan standar internasional yaitu aturan IEA/TIA 568A dan TIA/EIA 568B aturan kabelnya adalah sebagai berikut.

Aturan IEA/TIA 568A
Urutan ke 1 : Putih Hijau
Urutan ke 2 : Hijau
Urutan ke 3 : Putih Orange
Urutan ke 4 : Biru
Urutan ke 5 : Putih Biru
Urutan ke 6 : Orange
Urutan ke 7 : Putih Coklat
Urutan ke 8 : Coklat

Aturan TIA/EIA 568B
Urutan 1 : Putih Orange
Urutan 2 : Orange
Urutan 3 : Putih Hijau
Urutan 4 : Biru
Urutan 5 : Putih Biru
Urutan 6 : Hijau
Urutan 7 : Putih Coklat
Urutan 8 : Coklat

### a. Straight

Jenis kabel ini menggunakan standar yang sama antara ujung satu dengan ujung yang satunya lagi. Jika pada ujung pertama susunan yang kita pakai adalah EIA/TIA 568A, maka pada ujung yang kedua kita menggunakan susunan yang sama pula yaitu EIA/TIA 568A. Begitu juga bila salah satu ujungnya menggunakan susunan EIA/TIA 568B, maka ujung satunya menggunakan susunan yang sama.
Jadi sederhananya, pin 1 pada salah satu ujung akan terhubung dengan pin 1 pada ujung yang lainnya, lalu pin 2 akan terhubung dengan pin 2, dan seterusnya.

[![Straight-Through-Cable.gif](https://i.postimg.cc/G2T4yDXT/Straight-Through-Cable.gif)](https://postimg.cc/HcHWGrDT)

Kabel straight trought ini biasanya digunakan untuk peragkat yang tidak sejenis, semisal:

-  PC dengan Switch
-  PC dengan HUB
-  Switch dengan Router

### b. Crossover

Penyusunan kaebel Cross Over (Silang) berbeda dengan kabel Straight Trought (Lurus). Jika pada ujung satu menggunakan standar EIA/TIA 568A, maka pada ujung kedua harus menggunakan standar EIA/TIA 568B. Bisa kita lihat bersama pada gambar dibawah ini, kabel yang menyilang merupakan kabel yang berfungsi untuk mengirim dan menerima data, sedangkan dua pasang kabel yang lain susunannya tetap.

[![Cross-Over-Cable.png](https://i.postimg.cc/Jhwv8V9w/Cross-Over-Cable.png)](https://postimg.cc/jDXZ69xv)

Kabel Cross Over digunakan untuk menghubungkan perangkat yang sejenis, semisal:

-  PC dengan PC
-  Switch Dengan Switch
-  Hub dengan Hub
-  Router dengan Router

# **2. Pembuatan Kabel UTP**

Dalam pembuatan kabel UTP yang merupakan kabel paling sering digunakan untuk menghubungkan sebuah komputer dengan komputer lainnya melalui sebuah perangkat jaringan. Tidak hanya itu, kabel ini juga sering digunakan untuk menghubungkan dari komputer ke perangkat jaringan yang lain seperti router dan switch. Kali ini saya akan membagi tips cara membuat Kabel UTP Straight & Cross untuk bisa membuat jaringan pada komputer agar terhubung secara online ke internet maupun lokal.

## 2.1. Alat Yang Dipersiapkan Dan Kegunakannya

Alat-alat yang perlu dipersiapakan untuk pembuatan kabel UTP:

1. Tank Crimping adalah alat untuk memotong kabel UTP dan untuk menjepit ujung konektor,dan ini sangat penting sekali bagi kita yang ingin belajar cara mengcrimping kabel,alat ini bentuknya hampir sama dengan Tank biasa yang sering kita lihat atau temui.

   [![IMG20220823165951.jpg](https://i.postimg.cc/LsXvLSFP/IMG20220823165951.jpg)](https://postimg.cc/yDMFCwd6)

2. Kabel UTP kita gunakan untuk saling menghubungkan jaringan internet dan di dalam kabel UTP ini terdapat 8 helai kabel kecil yang berwarna-warni.

   [![IMG20220823165958.jpg](https://i.postimg.cc/K8QJ1zwF/IMG20220823165958.jpg)](https://postimg.cc/QF9pPXjn)

3. Konektor adalah alat yang kita pasang pada ujung kabel UTP tujuanya agar kabel dapat kita pasang pada port LAN. Konektor RJ-45 harus dipasangkan pada ujung kabel UTP apabila tidak maka Kabel UTP tidak akan berguna.

   [![IMG20220823164408.jpg](https://i.postimg.cc/6qRMqhJ1/IMG20220823164408.jpg)](https://postimg.cc/xNfvFMdK)

4. Lan Tester adalah alat untuk menguji hasil crimpingan kabel kita, kalau krimpingan kita salah maka lampu di Cable Tester ini tidak akan menyala dan kalau hasil crimpingan kita sudah benar maka lampu di Cable Tester akan menyala dengan otomatis,jadi alat ini sangat berguna bagi kita untuk mengetahui hasil crimpingan kita.

   [![IMG20220823165929.jpg](https://i.postimg.cc/BvqBs0ny/IMG20220823165929.jpg)](https://postimg.cc/WdHk6xr6)

## 2.2. Langkah Pembuatan Kabel Tipe Straight

Langkah-lankah pembuatan kabel UTP tipe straight

1. Kupas bagian ujung kabel UTP, kira-kira 2 cm.
2. Buka pilinan kabel, luruskan dan urutankan kabel sesuai standar gambar.
3. Setelah urutannya sesuai standar, potong dan ratakan ujung kabel,
4. Masukan kabel yang sudah lurus dan sejajar tersebut ke dalam konektor RJ-45, dan pastikan semua kabel posisinya sudah benar sesuai dengan Straight-through.
5. Lakukan crimping menggunakan crimping tools, tekan crimping tool dan pastikan semuapin (kuningan) pada konektor RJ-45 sudah “menggigit” tiap-tiap kabel. biasanya akan terdengar suara “klik”. Setelah selesai pada ujung yang satu, lakukan lagi pada ujung yang lain.

   [![IMG20220823162126.jpg](https://i.postimg.cc/G247wCMR/IMG20220823162126.jpg)](https://postimg.cc/JDWcZ9VY)

## 2.2. Langkah Pembuatan Kabel Tipe Cross

Langkah-lankah pembuatan kabel UTP tipe CrossOver

1. Kupas bagian ujung kabel UTP, kira-kira 2 cm.
2. Buka pilinan kabel, luruskan dan urutankan kabel sesuai standar gambar.
3. Setelah urutannya sesuai standar, potong dan ratakan ujung kabel,
4. Masukan kabel yang sudah lurus dan sejajar tersebut ke dalam konektor RJ-45, dan pastikan semua kabel posisinya sudah benar sesuai dengan Crossover
5. Lakukan crimping menggunakan crimping tools, tekan crimping tool dan pastikan semuapin (kuningan) pada konektor RJ-45 sudah “menggigit” tiap-tiap kabel. biasanya akan terdengar suara “klik”. Setelah selesai pada ujung yang satu, lakukan lagi pada ujung yang lain.

   [![IMG20220823164413.jpg](https://i.postimg.cc/Nf6NwbxK/IMG20220823164413.jpg)](https://postimg.cc/YhSN66Z7)

## 3.0. Pengetesan Kabel UTP

Langkah untuk mengecek kabel yang sudah kita buat tadi yaitu dengan menggunakan LAN tester, caranya masukan masing-masing ujung kabel (konektor RJ-45) ke masing2 port yang tersedia pada LAN tester, nyalakan dan pastikan semua lampu LED menyala sesuai dengan urutan kabel yang kita buat.

## 3.1. Alat Pengetesan

Alat pengetesan pada kabel utp biasanya menggunakan Lan Tester. Lan Tester adalah alat untuk mengecek koneksi sambungan kabel LAN RJ 45 dan RJ 11. Dilengkapi dengan lampu indikator, tombol pengatur kecepatan pengecekan, serta baterai dan kantong kecil. Dari namananya saja sudah jelas bahwa LAN tester adalah alat untuk mengecek sambungan rangkaian kabel LAN RJ 45 dan RJ 11.

[![IMG20220823165933.jpg](https://i.postimg.cc/FKDgHBfK/IMG20220823165933.jpg)](https://postimg.cc/Ty5WkQJ8)

## 3.2. Cara Pengetesan Alat

-  Cara Pengetesan kabel croos
   Fungsi kabel Straight adalah digunakan untuk menghubungkan 2 device yang berbeda dan merupakan kabel yang memiliki cara pemasangan yang sama antara ujung satu dengan ujung yang lainnya. Jika kalian mengecek kabel stright, maka lampu no 1 - 8 harus hidup semua secara berurutan.

   -  1 -> 1
   -  2 -> 2
   -  3 -> 3
   -  4 -> 4
   -  5 -> 5
   -  6 -> 6
   -  7 -> 7
   -  8 -> 8

-  Cara Pengetesal kabel straight
   fungsi kabel Cross adalah digunakan untuk menghubungkan 2 device yang sama, Susunan kabelnya yang berbeda antara ujung satu dengan ujung yang lainnya. Walaupun jenis kombinasi kabelnya berbeda tapi cross menggunakan kabel yang sama yaitu kabel UTP. Dan jika kalian ingin mengecek kabel cross, urutan lampu nya berbeda dengan urutan lampu kabel stright.
   -  1 -> 3
   -  2 -> 6
   -  3 -> 1
   -  4 -> 4
   -  5 -> 5
   -  6 -> 2
   -  7 -> 7
   -  8 -> 8
