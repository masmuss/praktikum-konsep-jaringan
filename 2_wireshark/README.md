# **Wireshark**

Wireshark sendiri merupakan salah satu dari tool Network Analyzer yang biasa digunakan oleh Network Administrator pemecahan masalah jaringan, analisis, perangkat lunak dan pengembangan protokol komunikasi, dan pendidikan.

Wireshark menggunakan warna untuk membantu mengidentifikasi jenis lalu lintas secara sekilas. Secara default, hijau adalah lalu lintas TCP, biru tua adalah lalu lintas DNS, biru muda adalah lalu lintas UDP, dan hitam mengidentifikasi paket TCP dengan masalah — misalnya, mereka bisa saja dikirim tidak sesuai dengan request yang dikirim.

[![image.png](https://i.postimg.cc/NfLvM5Cq/image.png)](https://postimg.cc/nC8PSct0)

## Tabel warna di Wireshark

|    Color     |                                Packets type                                 |
| :----------: | :-------------------------------------------------------------------------: |
| Light purple |                                     TCP                                     |
|  Light blue  |                                     UDP                                     |
|    Black     |                             Packets with errors                             |
| Light green  |                                HTTP traffic                                 |
| Light yellow | Windows-specific traffic, including Server Message Blocks (SMB) and NetBIOS |
| Dark yellow  |                                   Routing                                   |
|  Dark gray   |                        TCP SYN, FIN and ACK traffic                         |
|     Red      |                           Invalid Display Filter                            |

1. Black Color
   [![image.png](https://i.postimg.cc/DfppZ5b5/image.png)](https://postimg.cc/mhMypYjF)
2. Light blue and Light purple
   [![image.png](https://i.postimg.cc/fTkFj1h6/image.png)](https://postimg.cc/HVDBTZn2)
   [![image.png](https://i.postimg.cc/RZpZpk3K/image.png)](https://postimg.cc/qNnrzZxv)
3. Dark gray and red
   [![image.png](https://i.postimg.cc/C1NCWMbm/image.png)](https://postimg.cc/PpC8Dj3w)
4. Light yellow
   [![image.png](https://i.postimg.cc/T3dcJDmh/image.png)](https://postimg.cc/ZCQ3T0wh)

## Packet Analyzer

### Config local

[![image.png](https://i.postimg.cc/kgRgZjWH/image.png)](https://postimg.cc/cvZWtB97)

Dengan menggunakan ping pada default gateway yang diberikan oleh router (wifi) sudah bisa melakukan analisa suatu packet dengan bantuan Wireshark.

[![image.png](https://i.postimg.cc/BtWVvQwH/image.png)](https://postimg.cc/2LwwcmYS)

[![image.png](https://i.postimg.cc/gjKgGq8F/image.png)](https://postimg.cc/gLnVDhgN)

Gambar di atas menunjukkan bahwa IP Address pada adaptor wifi yakni 192.168.18.14 dan default gatewaynya 192.168.18.1 dengan data tersebut kita bisa mengetahui packet yang terlintas pada Wireshark.

[![image.png](https://i.postimg.cc/nzGWLJfP/image.png)](https://postimg.cc/njM2dNz4)
[![image.png](https://i.postimg.cc/fbZjR0WM/image.png)](https://postimg.cc/rDnthstH)

Dalam box Internet Protocol terdapat:

-  Version: 4 Menunjukkan versi yang digunakan adalah versi 4
-  Header length: 20 bytes Menunjukkan panjangnya header yang ada di lapisan network adalah sebesar 20 bytes
-  Source: `192.168.18.1` Destination: `192.168.18.14` Menunjukkan IP dari source yaitu `192.168.18.1` dan IP dari destination yaitu `192.168.18.14`
-  Kesimpulan: Lapisan network, panjangnya header yang diberikan sebesar 32 bytes dengan IP source `192.168.18.1` dan IP destination yaitu `192.168.18.14`

## ICMP

Internet Control Message Protocol (ICMP) adalah salah satu protokol inti dari keluarga protokol internet. ICMP utamanya digunakan oleh sistem operasi komputer jaringan untuk mengirim pesan kesalahan yang menyatakan, sebagai contoh, bahwa komputer tujuan tidak bisa dijangkau. ICMP berbeda tujuan dengan TCP dan UDP dalam hal ICMP tidak digunakan secara langsung oleh aplikasi jaringan milik pengguna. salah satu pengecualian adalah aplikasi ping yang mengirim pesan ICMP Echo Request (dan menerima Echo Reply) untuk menentukan apakah komputer tujuan dapat dijangkau dan berapa lama paket yang dikirimkan dibalas oleh komputer tujuan. [Wikipedia.org](https://id.wikipedia.org/wiki/Internet_Control_Message_Protocol)

[![image.png](https://i.postimg.cc/fbZjR0WM/image.png)](https://postimg.cc/rDnthstH)

Dari keterangan diatas, ICMP saat echo ping request tersebut, icmp bertype 0, code 0, dengan algoritma checksum 0x5559, banyak identifier (identifikasi) 256 bytes dan Sequence number 25088 byte. Serta hasil diatas menunjukkan saat proses request ping, paket dari source IP address dari komputer kita akan merequest ({echo (ping) request) ke destination IP address router wifi biznet.

[![image.png](https://i.postimg.cc/tRdFTNvw/image.png)](https://postimg.cc/K4z1pB2D)

Dalam box frame terdapat:

1. Arrival Time: Sep 6, 2022 09:48:14.462763000 SE Asia Standard Time
   Menunjukkan waktu saat pengiriman data
2. [Time delta from previous captured frame: 0.003049000 seconds]
   [time delta from previous displayed frame: 0.003049000 seconds]
   [Time since reference or first frame: 2.146335000 seconds]
   Menunjukkan waktu sebelum capture dari frame
3. Frame Number: 9
   Menunjukkan nomor dari frame tersebut yaitu 4344
4. Frame Length: 74 bytes (592 bits)
   Menunjukkan panjangnya frame adalah sebasar 74 bytes
5. [Protocols in frame: eth:ethertype:ip:icmp:data]
   Menunjukkan protokol-protokol apa saja yang ada di frame 4344 yaitu ada Ethernet, Internet Protocol (IP), Internet Control Message Protocol (ICMP) & Data
6. Kesimpulan: Lapisan ini menunjukkan apa saja yang ada dalam satu frame yaitu JOBSHEET TEUM seperti protokol-protokol yang ada di lapisan ini Ethernet, Internet Protocol (IP), Transmission Control Protocol (TCP), Hypertext Transfer Protocol (HTTP), dan data-text-lines.
