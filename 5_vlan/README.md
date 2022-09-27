# **Virtual Local Area Network (V-LAN)**

Virtual Local Area Network atau VLAN adalah sekumpulan perangkat yang ada di satu atau lebih jaringan LAN dan dikonfigurasikan oleh perangkat lunak sehingga dapat berkomunikasi antara satu dengan lainnya seolah-olah berada di saluran yang sama.

VLAN sendiri sebenarnya merupakan sebuah jaringan yang berada di dalam Local Area Network (LAN) sehingga dalam satu jaringan LAN bisa terdiri atas lebih dari satu jaringan VLAN.

Secara umum, konfigurasi jaringan Virtual Local Area Network (VLAN) dilakukan oleh perangkat lunak atau software. Sehingga ketika perangkat dipindah tidak perlu melakukan konfigurasi ulang.

Metodenya sendiri biasanya menggunakan switch bukan router seperti pada konfigurasi LAN biasa.

## Fungsi dari V-LAN

1. ### Keamanan

   LAN atau Local Area Network merupakan sebuah jaringan private yang tidak bisa diakses oleh sembarang user.

   Dari segi keamanan, LAN tentu sangat maksimal karena setiap akses harus mendapat permission atau izin dari administrator jaringan.

   Adapun VLAN (Virtual Local Area Network) sendiri konsepnya hampir sama seperti LAN konvensional, hanya saja jaringan yang digunakan kini sudah bersifat nirkabel sehingga bisa diakses dari mana saja.

   VLAN dapat bermanfaat untuk membatasi akses ke berbagai data sensitif tersebut sehingga mengurangi potensi penyalahgunaan akses dari orang tidak bertanggung jawab.

2. ### Efisiensi biaya

   Dengan VLAN (Virtual Local Area Network) kita tidak perlu menyiapkan perangkat LAN seperti router maupun kabel, sebagai gantinya kita menggunakan switch yang relatif mudah dalam pengoperasiannya.

   Hal ini tentu sangat efektif dan efisien karena perusahaan bisa menghemat biaya pembelian kabel LAN dan router ketika ada komputer baru yang ingin dihubungkan.

3. ### Tidak Perlu Mengatur Ulang Jaringan Komputer

   Agar bisa tetap terkoneksi ke jaringan LAN, maka setiap komputer yang dipindahkan harus diatur ulang. Hal ini tentu membutuhkan banyak waktu karena harus dilakukan mulai dari awal. Dan ketika kita menggunakan V-LAN, kita tidak perlu melakukannya karena komputer terhubung secara virtual.

4. ### Memudahkan Administrasi
   Manfaat VLAN berikutnya adalah penyederhanaan proses administrasi. Dengan adanya jaringan VLAN sebuah komputer server tidak perlu datang langsung ke area komputer server untuk masuk ke jaringan.

## Cara kerja V-LAN

1. Virtual Local Area Network dalam jaringan diidentifikasi dengan nomor
2. Rentang yang valid adalah 1-4094. Pada saklar Virtual Local Area Network, anda menetapkan port dengan nomor Virtual Local Area Network yang tepat
3. Saklar kemudian memungkinkan data yang perlu dikirim antara berbagai port yang memiliki Virtual Local Area Network yang sama
4. Karena hampir semua jaringan lebih besar dari satu saklar, harus ada cara untuk mengirim lalu lintas antara dua saklar
5. Salah satu cara sederhana dan mudah untuk melakukannya adalah dengan menetapkan port pada setiap switch jaringan. Dengan Virtual Local Area Network dan menjalankan kabel antara keduanya.

## Praktikum

Pertama disini saya mempunyai beberapa perangkat yaitu

1. 1 buah switch
2. 8 buah PC

Kemudian dirangkai seperti rangkaian berikut
[![image.png](https://i.postimg.cc/QdZWpBQ2/image.png)](https://postimg.cc/HV3xmkPz)

Pada rangkaian diatas, saya membuat 2 grup dengan asumsi group 1 (PC0 - PC3) berada pada ruang 1 (VLAN 100) dan group 2 (PC4 - PC7) berada pada ruang 2 (VLAN 200)

### **Konfigurasi PC**

Untuk alokasi IP dari masing masing PC adalah sebagai berikut:
| **PC** |    **IP**     | **Port pada switch** |
| :----: | :-----------: | :------------------: |
|  PC0   | `192.168.1.1` |   FastEthernet0/1    |
|  PC1   | `192.168.1.2` |   FastEthernet0/2    |
|  PC2   | `192.168.1.3` |   FastEthernet0/3    |
|  PC3   | `192.168.1.4` |   FastEthernet0/4    |
|  PC4   | `192.168.1.5` |   FastEthernet0/11   |
|  PC5   | `192.168.1.6` |   FastEthernet0/12   |
|  PC6   | `192.168.1.7` |   FastEthernet0/13   |
|  PC7   | `192.168.1.8` |   FastEthernet0/14   |

Untuk membuktikan bahwa semua komputer terhubung dengan baik, kita bisa tes `ping` antar PC, semisal kita akan ping PC dengan IP `192.168.1.8` dari PC dengan IP `192.168.1.1`. Disini masih bisa terhubung dikarenakan belum ada pembatas yang membatasi akses antar ruang.

### **Konfigurasi switch**

Setelah semua PC sudah tersambung dengan switch, maka sekarang kita akan masuk ke konfigurasi dari switch

Pertama kita akan setup untuk VLAN 100 (ruang 1), masuk ke CLI pada switch dan masukkan perintah pada gambar berikut

[![image.png](https://i.postimg.cc/gkm1TsH4/image.png)](https://postimg.cc/ThNkyrSW)

Lakukan hal yang sama dengan VLAN 200.

Setelah itu kita lanjutkan dengan membatasi port yang digunakan, kita asumsikan `fa0/1 - fa0/10` akan digunakan pada ruang 1 dan `fa0/11 - fa0/20` digunakan pada ruang 2.

Gunakan perintah dibawah ini untuk melakukan pembatasan port
[![image.png](https://i.postimg.cc/XYcq0QRJ/image.png)](https://postimg.cc/jD2tHQd0)

Setelah konfigurasi switch selesai, kita bisa `exit`.
Untuk memastikan bahwa konfigurasi sudah berhasil dilakukan, gunakan perintah `show vlan brief` untuk melihat port mana saja yang sudah terhubung

[![image.png](https://i.postimg.cc/xdpmb99h/image.png)](https://postimg.cc/rdWsBX0N)

Kemudian kita bisa mengetes `ping` PC pada ruang 2 dari PC di ruang 1
[![image.png](https://i.postimg.cc/J4THF1kn/image.png)](https://postimg.cc/F7LKdXG5)

Bisa dilihat jika proses gagal karena akses ruang sudah dibatasi oleh V-LAN


