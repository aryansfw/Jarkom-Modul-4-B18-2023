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