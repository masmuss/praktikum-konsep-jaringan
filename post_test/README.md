# LAPORAN PRAKTIKUM 
Musafir Khoirul (3121600003)
Awan Abdillah (3121600016)

## TOPOLOGI
[![image.png](https://i.postimg.cc/h40JrZ80/image.png)](https://postimg.cc/z3VXDjcL)
Topologi di atas terdiri dari 10 Router. R1 sebagai router utama yang akan terhubung ke AS Number yang lain. Area R2 menggunakan routing protocol RIP, area R3 menggunakan OSPF, area R4 menggunakan Static Routing, sementara untuk menghubungkan area R2, R3, dan R4 menggunakan routing protocol BGP yang terhubung ke router pusat yakni R1.

| Devices |   IP Address    | CIDR |     Network     | Interface |
| :-----: | :-------------: | :--: | :-------------: | :-------: |
|   R1    |   14.14.14.1    |  24  |   14.14.14.0    |  ether2   |
|         |   13.13.13.1    |  24  |   13.13.13.0    |  ether3   |
|         |   12.12.12.1    |  24  |   12.12.12.0    |  ether4   |
|   R2    |   12.12.12.2    |  24  |   12.12.12.0    |  ether1   |
|         |   27.27.27.2    |  24  |   27.27.27.0    |  ether2   |
|         |   28.28.28.2    |  24  |   28.28.28.0    |  ether3   |
|   R3    |   13.13.13.3    |  24  |   13.13.13.0    |  ether1   |
|         |   36.36.36.3    |  24  |   36.36.36.0    |  ether2   |
|         |   35.35.35.3    |  24  |   35.35.35.0    |  ether3   |
|   R4    |   14.14.14.4    |  24  |   14.14.14.0    |  ether1   |
|         |   41.41.41.4    |  24  |   41.41.41.0    |  ether2   |
|         |   49.49.49.4    |  24  |   49.49.49.0    |  ether3   |
|   R5    |   35.35.35.5    |  24  |   35.35.35.0    |  ether1   |
|         |   50.50.50.50   |  -   |   50.50.50.50   |    lo0    |
|   R6    |   36.36.36.6    |  24  |   36.36.36.0    |  ether1   |
|         |   60.60.60.60   |  -   |   60.60.60.60   |    lo0    |
|   R7    |   27.27.27.7    |  24  |   27.27.27.0    |  ether1   |
|         |   70.70.70.70   |  -   |   70.70.70.70   |    lo0    |
|   R8    |   28.28.28.8    |  24  |   28.28.28.0    |  ether1   |
|         |   80.80.80.80   |  -   |   80.80.80.80   |    lo0    |
|   R9    |   49.49.49.9    |  24  |   49.49.49.0    |  ether1   |
|         |   90.90.90.90   |  -   |   90.90.90.90   |    lo0    |
|   R10   |   41.41.41.10   |  24  |   41.41.41.0    |  ether1   |
|         | 100.100.100.100 |  -   | 100.100.100.100 |    lo0    |

## Ruang Lingkup Kerja
Ruang lingkup kerja kami disini adalah mengkonfigurasi Router R8 dengan konfigurasi sebagai berikut:
1. Memberi Alamat IP pada interface yang akan digunakan
   ```powershell
   /interface bridge
   add name=lo0
   /ip address
   add address=28.28.28.8/24 interface=ether1 network=28.28.28.0
   add address=80.80.80.80 interface=lo0 network=80.80.80.80
   ```

2. Konfigurasi Routing RIP agar dapat bertukar informasi Routing antar router
   ```powershell
   /routing rip network
   add network=28.28.28.0/24
   add network=80.80.80.80/32
   ```

## Table Routing
[![image.png](https://i.postimg.cc/15QDJNNp/image.png)](https://postimg.cc/rzfdpsjm)
## Test Koneksi
[![image.png](https://i.postimg.cc/NjP9qyLC/image.png)](https://postimg.cc/Xrd79Yf9)
[![image.png](https://i.postimg.cc/15mf80qY/image.png)](https://postimg.cc/Wty2KkSM)
[![image.png](https://i.postimg.cc/dVdPvp0M/image.png)](https://postimg.cc/FY9nVPcG)

1. Berhasil melakukan ping ke IP Address pada router lokal R7(27.27.27.1) dan R2(12.12.12.1)
2. Berhasil melakukan ping ke IP Address pada router R4(14.14.14.1)


