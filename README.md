# Jarkom-Modul-4-B18-2023

## Kelompok B18

|          Nama          |    NRP     |
| :--------------------: | :--------: |
|  Aryan Shafa Wardana   | 5025211031 |
| Shazia Ingeyla Naveeda | 5025211203 |

# Pendahuluan

Pada praktikum ini, kami membuat topologi sesuai dengan soal yang diberikan pada aplikasi GNS3 VM dan Cisco Packet Tracer. Kemudian kami mengaplikasikan pembagian subnet dan pembagian IP dengan metode classless, yaitu menggunakan teknik VLSM di GNS3 dan teknik CIDR di Cisco Packet Tracer. Lalu kami menghubungkan antar node di topologi menggunakan routing. Prefix yang kami gunakan adalah 192.187.x.x.


## Topologi

Berikut adalah gambar topologi yang digunakan.

![Topologi](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/8176cbfa-9fb9-451f-9a7b-6a10ca3d6cb1)

## Rute

Berikut adalah pembagian subnet dan rutenya untuk topologi yang kami gunakan

![Rute](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/9dab5ba5-e5f0-4f7c-a739-77d85653e819)

# CIDR

### Topologi

Untuk teknik CIDR, kami menggunakan Cisco Packet Tracer untuk mensimulasikan topologi. Berikut adalah topologi yang dibuat.

![Topologi](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/8176cbfa-9fb9-451f-9a7b-6a10ca3d6cb1)

### Tabel Penggabungan IP CIDR

Setelah membuat topologi, kita harus menggabungkan subnet-subnet sehingga menjadi 1 subnet besar yang mencakupi semua subnet. Penggabungan dilakukan pada tabel seperti berikut.

![Tabel CIDR](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/d950c065-65d0-46b6-8b69-a1a1fb185754)

### Pohon CIDR

Dari subnet-subnet tersebut, kita bisa membuat pohon CIDR yang digunakan untuk menentukan pembagian IP pada node-node dalam topologi seperti berikut.

![Pohon CIDR](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/024f0145-c070-4787-95d0-0742614c2a38)

### Tabel Pembagian IP CIDR

Pembagian NID, netmask, dan broadcast dapat ditabelkan seperti pada tabel berikut.

![Tabel IP CIDR](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/069f9f86-766f-4fad-86d3-ae8743179980)

### Konfigurasi Interface dan IP pada Router, Server, dan Client

Setelah kita membagikan IP pada subnet, kita harus konfigurasi interface masing-masing router, server, dan client. Untuk mengubah konfigurasi interface dan IP, kita bisa melakukan berikut.
- Untuk router, kita bisa mengakses Router -> Config -> Interface
- Untuk server dan client, kita bisa mengakses Server atau Client -> Desktop -> IP Configuration

 Sebagai contoh, kita bisa melakukan konfigurasi interface pada Aura yang melalui subnet A1. Kita bisa memasukkan IP 192.187.0.1 dengan netmask 255.255.255.252 pada interface FastEthernet0/1 sesuai dengan tabel CIDR seperti berikut.

![Konfigurasi Interface Aura](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/577f563e-d1aa-4292-b927-7f42b259ea0e)

Router Denken yang juga terhubung pada subnet A1 bisa dikonfigurasi memiliki IP 192.187.0.2 dan netmask 255.255.255.252 pada interface FastEthernet0/0 seperti berikut.

![Konfigurasi Interface Denken](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/f111a28a-488f-4b06-811e-f13384925648)


Setelah dikonfigurasi, kita bisa menghidupkan port dengan centang Port Status menjadi On. Contoh 

Contoh konfigurasi IP pada server dan client seperti berikut. Untuk client RoyalCapital, kita bisa melakukan konfigurasi seperti gambar di bawah

![RoyalCapital](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/61ec0b1b-c183-4499-8e49-82823b9379a8)

Konfigurasi interface dan IP ini dilakukan untuk semua router, client, dan server.

### Konfigurasi Routing pada Router, Server, dan Client

Setelah interface sudah dikonfigurasi, kita bisa memulai routing. Sebagai contoh, kita menggunakan router Eisen. Eisen perlu melakukan routing ke subnet A6, A7, A9, A8, A11, dan A12. Route Eisen dapat disimpulkan seperti berikut.
- Untuk bisa route kembali ke parentnya, maka harus kembali ke router Aura melalui subnet A3
- Untuk menuju subnet A6 dan A7, Eisen perlu melewati router Lugner yang memiliki IP 192.189.136.2. 
- Untuk menuju subnet A9, A8, A11, dan A12, Eisen perlu melewati router Linie yang memiliki IP 192.189.224.2

Untuk menambahkan routing maka bisa memilih Device -> Config -> Routing -> Static, lalu memasukkan Network ID, Netmask, dan Gateway atau IP router yang dilalui. Sebagai contoh, untuk bisa route kembali ke Aura maka kita bisa menambahkan seperti berikut.

![Aura](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/20900519-824d-402d-83ea-7dea11d5c959)

Lalu, untuk menuju subnet A6 maka kita bisa menambahkan route seperti berikut.

![A6](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/47a82090-3fe2-4149-a8e5-36a99bfe2749)

Routing ini dilakukan pada semua router dengan cara yang sama.

### Testing

Untuk test apabila routing sudah berhasil maka kita bisa mencoba ping antar device. 
Untuk testing di Cisco Packet Tracer, kita bisa menggunakan tool Add Simple PDU (atau klik P) lalu pilih 2 device yang ingin ditest. Kami mencoba ping antar device berikut.
- GranzChannel - Eisen
- Aura - Laubhills
- SchwerMountains - Stark
- RoyalCapital - RiegelCanyon
- AppetitRegion - GrobeForest 

Hasil testing seperti berikut. Jika successful semua maka paket berhasil terkirim.

![Testing](https://github.com/aryansfw/Jarkom-Modul-4-B18-2023/assets/115603634/38409af6-7ee4-43c2-9f86-bed5ee4dc3ee)
