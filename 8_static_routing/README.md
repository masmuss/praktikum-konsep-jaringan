# **Static Routing**

### Table of Contents

- [**Static Routing**](#static-routing)
    - [Table of Contents](#table-of-contents)
  - [Routing dan static routing](#routing-dan-static-routing)
  - [Persiapan Topologi](#persiapan-topologi)
  - [Percobaan 1 - Konfigurasi masing-masing perangkat](#percobaan-1---konfigurasi-masing-masing-perangkat)
    - [PC0 dan PC1](#pc0-dan-pc1)
      - [PC0](#pc0)
      - [PC1](#pc1)
    - [Router](#router)
      - [Router 1](#router-1)
      - [Router 2](#router-2)
  - [Percobaan 2 - Trace Packet](#percobaan-2---trace-packet)
  - [Percobaan 3 - Konfigurasi IP dan routing Router3](#percobaan-3---konfigurasi-ip-dan-routing-router3)
  - [Percobaan 4 - Penambahan routing melalui router 3](#percobaan-4---penambahan-routing-melalui-router-3)

## Routing dan static routing

Routing adalah proses menentukan jalur yang akan dilalui oleh paket. Perangkat yang melakukan routing adalah router.

Static Routing adalah routing yang dilakukan secara manual. Setiap jaringan yang akan dirouting harus dikonfigurasi satu persatu oleh administrator jaringan. Kelebihan dari static routing adalah lebih aman serta tidak memutuhkan sumber daya yang besar.

## Persiapan Topologi

Pertama adalah mari kita buat topologi seberti gambar dibawah

[![image.png](https://i.postimg.cc/GtwQd2fV/image.png)](https://postimg.cc/qhwnGk4x)

Dalam topologi diatas, sebelah kanan memiliki network address `192.168.5.0/24` dan sebelah kiri `192.168.4.0/24`. Untuk mengubungkan jaringan di kanan dan kiri, disini menggunakan 3 router yang disusun seperti topologi ring.

Menggunakan topologi di atas, akan dilakukan 1 percobaan sebagai berikut:

1. Konfigurasi default untuk menghubungkan jaringan 4.0 dan 5.0 menggunakan Router1 dan Router2 serta konfigurasi IP untuk Router0
2. Melakukan trace jalur yang dilewati paket apakah sudah benar melalui Router1 dan Router2.
3. Konfigurasi Router3 untuk melakukan routing ke jaringan 4.0 dan 5.0 serta melakukan trace apakah jalurnya berubah.
4. Konfigurasi Router1 dan Router2 untuk melewatkan paket dari jaringan 4.0 ke 5.0 melalui Router3 dengan menggunakan parameter distance.

## Percobaan 1 - Konfigurasi masing-masing perangkat

### PC0 dan PC1

Untuk PC disini kita menggunakan static routing, berikut konfigurasi dari masing-masing PC

#### PC0

[![image.png](https://i.postimg.cc/Y2P44Zq2/image.png)](https://postimg.cc/7bgPdB2j)

#### PC1

[![image.png](https://i.postimg.cc/wvZmdG1B/image.png)](https://postimg.cc/34jRX9CM)

### Router

#### Router 1

```powershell
!
interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet1/0
 ip address 192.168.3.2 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet4/0
 no ip address
 shutdown
!
interface FastEthernet5/0
 no ip address
 shutdown
!
interface FastEthernet6/0
 ip address 192.168.5.1 255.255.255.0
 duplex auto
 speed auto
!
ip classless
ip route 192.168.4.0 255.255.255.0 192.168.3.1
```

Tes tabel routing

[![image.png](https://i.postimg.cc/8PMN40Db/image.png)](https://postimg.cc/tYqKCDs1)

#### Router 2

```powershell
!
interface FastEthernet0/0
 ip address 192.168.3.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet1/0
 ip address 192.168.2.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet6/0
 ip address 192.168.4.1 255.255.255.0
 duplex auto
 speed auto
!
ip classless
ip route 192.168.5.0 255.255.255.0 192.168.3.2
```

Tes tabel routing

[![image.png](https://i.postimg.cc/BbCNQ3Hg/image.png)](https://postimg.cc/LgnjNryY)

## Percobaan 2 - Trace Packet

Selelah kita menghubungkan kedua jaringan, kita akan mengecek apakah kedua jaringan sudah terhubung

PC0 --> PC1

[![image.png](https://i.postimg.cc/t4gybCWB/image.png)](https://postimg.cc/LnGGBSyP)

PC1 --> PC0

[![image.png](https://i.postimg.cc/L5XKpxZn/image.png)](https://postimg.cc/r0vYGCjk)

## Percobaan 3 - Konfigurasi IP dan routing Router3

Selanjutnya adalah konfigurasi router0 agar memiliki koneksi ke jaringan 4.0 dan 5.0 . Konfigurasinya adalah sebagai berikut

```powershell
!
interface FastEthernet0/0
 ip address 192.168.1.2 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet1/0
 ip address 192.168.2.2 255.255.255.0
 duplex auto
 speed auto
!
ip classless
ip route 192.168.4.0 255.255.255.0 192.168.2.1
ip route 192.168.5.0 255.255.255.0 192.168.1.1
```

Kemudian kita cek tabel routingnya

[![image.png](https://i.postimg.cc/c1MByssg/image.png)](https://postimg.cc/grjZ3bLm)

Kita cek sekali lagi route dari PC0 ke PC1

[![image.png](https://i.postimg.cc/QNkw4GwS/image.png)](https://postimg.cc/8scZc31r)

## Percobaan 4 - Penambahan routing melalui router 3

Kali ini kita akan mencoba untuk merubah routing dengan menggunakan router 3 ketika menghubungkan PC0 ke PC1

1. Hapus konfigurasi routing di masing masing router

   Router 1

   ```powershell
    no ip route 192.168.4.0 255.255.255.0 192.168.3.1
   ```

   Pouter 2

   ```powershell
    no ip route 192.168.5.0 255.255.255.0 192.168.3.2
   ```

2. Tambahkan routing baru di router

   Untuk konfigurasi baru yang kita gunakan disini ada penambahan parameter di belakang gateway yang dilewati oleh paket. Untuk Router 1, kita dapat menggunakan perintah sebagai berikut

   ```powershell
    ip route 192.168.4.0 255.255.255.0 192.168.3.1 9
    ip route 192.168.4.0 255.255.255.0 192.168.1.2 10
   ```

   Pada perintah tersebut mengindikasikan bahwa routing melalui gateway 192.168.3.1 lebih prioritas karena nilai distancenya lebih sedikit.

   Cek tabel routing

   [![image.png](https://i.postimg.cc/Zn8G60yz/image.png)](https://postimg.cc/QKMY38bf)

   Pada tabel routing tersebut dapat kita lihat bahwa gateway menuju jaringan 4.0 masih tetap melalui `192.168.3.1` namun memiliki distance yang berbeda yaitu [9/0] atau 9.

   Untuk Router 2 perintahnya adalah sebagai berikut

   ```powershell
    ip route 192.168.5.0 255.255.255.0 192.168.3.2 10
    ip route 192.168.5.0 255.255.255.0 192.168.2.2 9
   ```

   Cek tabel routing

   [![image.png](https://i.postimg.cc/C558qn2z/image.png)](https://postimg.cc/BPWtWb40)

   Pada tabel routing dari router 2 juga mengalami perubahan namun perubahan tidak hanya ada pada distance saja, melainkan gatewaynya juga berubah melalui `192.168.2.2`.

   Tes trace PC0 --> PC1

   [![image.png](https://i.postimg.cc/vHjKDWKx/image.png)](https://postimg.cc/JGNx2BMR)

   Dari capture tersebut, dapat kita lihat bahwa gateway yang dilewati oleh paket dari PC0 menuju PC1 bertambah yaitu 192.168.2.2 dan 192.168.3.2. Lalu apakah gateway yang dilewati ketika paket dikirimkan dari PC1 menuju PC0 juga sesuai?

   PC1 --> PC0

   [![image.png](https://i.postimg.cc/Hs72ZFSj/image.png)](https://postimg.cc/8jNMsXgV)

   Ternyata jalur yang dilewati paket ketika paket tersebut berasal dari PC1 menuju PC0 juga sudah sesuai dengan distance pada konfigurasi.

[def]: #table-of-contents
