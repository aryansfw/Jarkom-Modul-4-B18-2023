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


# VLSM
### Topologi
Untuk metode VLSM menggunakan GNS. Berikut topologi pada GNS.

![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/2d992ef3-e6a3-49ec-900c-bccce197e386)

### Pohon
Dari subnet-subnet tersebut, kita bisa membuat pohon VLSM yang digunakan untuk menentukan pembagian IP pada node-node dalam topologi seperti berikut.

![TREE - VLSM (2)](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/2b0ac5f9-7cdf-4c63-97e7-37ec553f7578)

### Tabel Pembagian IP
Dari IP yang sudah ditentukan akan didapatkan pembagian IP sebagai barikut.

![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/e25668dd-d7a9-43ab-a9b5-2bb618379d43)



### Konfigurasi dan Routing
Lakukan konfigurasi terlebih dahulu setelah mendapatan NID, Netmask dan Broadcast. Lalu Routing dengan menjadikan `AURA` *master*. Dimana `AURA` mengetahui informasi menuju seluruh router, client dan server yang ada. Untuk rute kembalinya pada GNS tidak perlu diatur karena sudah ada default dari GNSnya. Berikut Konfigurasi dan Routing pada setiap node.

**SERVER**
```sh
#SERVER SEIN
#A12
auto eth0
iface eth0 inet static
	address 192.187.16.3
	netmask 255.255.252.0
	gateway 192.187.16.1
```

```sh
#SERVER RICHTER
#A13
auto eth0
iface eth0 inet static
	address 192.187.0.146
	netmask 255.255.255.248
	gateway 192.187.16.145
```

```sh
#SERVER REVOLTE
#A13
auto eth0
iface eth0 inet static
	address 192.187.0.147
	netmask 255.255.255.248
	gateway 192.187.16.145
```

```sh
#SERVER STARK
#A4
auto eth0
iface eth0 inet static
	address 192.187.0.18
	netmask 255.255.255.252
	gateway 192.187.0.17

```
**CLIENT**
```sh
#CLIENT ROYAL
#A2
auto eth0
iface eth0 inet static
	address 192.187.8.2
	netmask 255.255.255.0
	gateway 192.187.8.1
```

```sh
#CLIENT WR
#A2
auto eth0
iface eth0 inet static
	address 192.187.8.3
	netmask 255.255.255.0
	gateway 192.187.8.1
```

```sh
#CLIENT TR
#A6
auto eth0
iface eth0 inet static
	address 192.187.12.2
	netmask 255.255.252.0
	gateway 192.187.12.1
```

```sh
#CLIENT GF
#A7
auto eth0
iface eth0 inet static
	address 192.187.9.2
	netmask 255.255.255.0
	gateway 192.187.9.1
```

```sh
#CLIENT GC
#A9
auto eth0
iface eth0 inet static
	address 192.187.10.2
	netmask 255.255.254.0
	gateway 192.187.10.1
```

```sh
#CLIENT BR
#A11
auto eth0
iface eth0 inet static
	address 192.187.0.195
	netmask 255.255.255.192
	gateway 192.187.0.194
```

```sh
#CLIENT RIEGEL
#A12
auto eth0
iface eth0 inet static
	address 192.187.16.2
	netmask 255.255.252.0
	gateway 192.187.16.1
```

```sh
#CLIENT LK
#A15
auto eth0
iface eth0 inet static
	address 192.187.0.162
	netmask 255.255.255.224
	gateway 192.187.0.161
```

```sh
#CLIENT LH
#A18
auto eth0
iface eth0 inet static
	address 192.187.24.2
	netmask 255.255.248.0
	gateway 192.187.24.1
```

```sh
#CLIENT AR
#A18
auto eth0
iface eth0 inet static
	address 192.187.24.3
	netmask 255.255.248.0
	gateway 192.187.24.1
```

```sh
#CLIENT RR
#A19
auto eth0
iface eth0 inet static
	address 192.187.20.2
	netmask 255.255.252.0
	gateway 192.187.20.1
```

```sh
#CLIENT SM
#A21
auto eth1
iface eth1 inet static
	address 192.187.0.154
	netmask 255.255.255.248
	gateway 192.187.0.153
```

**ROUTER**
```sh
#ROUTER DENKEN
#A1
auto eth0
iface eth0 inet static
	address 192.187.0.2
	netmask 255.255.255.252
	gateway 192.187.0.1

#A2
auto eth1
iface eth1 inet static
	address 192.187.8.1
	netmask 255.255.255.0
```

```sh
#ROUTER LUGNER
#A5
auto eth0
iface eth0 inet static
	address 192.187.0.22
	netmask 255.255.255.252
	gateway 192.187.0.21

#A6
auto eth1
iface eth1 inet static
	address 192.187.12.1
	netmask 255.255.252.0

#A7
auto eth2
iface eth2 inet static
	address 192.187.9.1
	netmask 255.255.255.0
```
```sh
#ROUTER HEITER
#A11
auto eth0
iface eth0 inet static
	address 192.187.0.194
	netmask 255.255.255.192
	gateway 192.187.0.193

#A12
auto eth1
iface eth1 inet static
	address 192.187.16.1
	netmask 255.255.252.0
```

```sh
#ROUTER FERN
#A17
auto eth0
iface eth0 inet static
	address 192.187.0.138
	netmask 255.255.255.252
	gateway 192.187.0.137

#A18
auto eth1
iface eth1 inet static
	address 192.187.24.1
	netmask 255.255.248.0
```

```sh
#ROUTER HIMMEL
#A20
auto eth0
iface eth0 inet static
	address 192.187.0.142
	netmask 255.255.255.252
	gateway 192.187.0.141

#A21
auto eth1
iface eth1 inet static
	address 192.187.0.153
	netmask 255.255.255.248
```
```sh
#ROUTER AURA
auto eth0
iface eth0 inet dhcp

#A1
auto eth1
iface eth1 inet static
	address 192.187.0.1
	netmask 255.255.255.252

#A3
auto eth2
iface eth2 inet static
	address 192.187.0.5
	netmask 255.255.255.252

#A14
auto eth3
iface eth3 inet static
	address 192.187.0.129
	netmask 255.255.255.252

----------------------------------------------------------------------

# .BASHRC AURA
route add -net 192.187.8.0 netmask 255.255.255.0 gw 192.187.0.2
route add -net 192.187.0.16 netmask 255.255.255.252 gw 192.187.0.6
route add -net 192.187.0.20 netmask 255.255.255.252 gw 192.187.0.6
route add -net 192.187.12.0 netmask 255.255.252.0 gw 192.187.0.6
route add -net 192.187.9.0 netmask 255.255.255.0 gw 192.187.0.6
route add -net 192.187.0.24 netmask 255.255.255.252 gw 192.187.0.6
route add -net 192.187.10.0 netmask 255.255.254.0 gw 192.187.0.6
route add -net 192.187.0.28 netmask 255.255.255.252 gw 192.187.0.6
route add -net 192.187.0.192 netmask 255.255.255.192 gw 192.187.0.6
route add -net 192.187.16.0 netmask 255.255.252.0 gw 192.187.0.6
route add -net 192.187.0.144 netmask 255.255.255.248 gw 192.187.0.6
route add -net 192.187.0.160 netmask 255.255.255.224 gw 192.187.0.130
route add -net 192.187.0.132 netmask 255.255.255.252 gw 192.187.0.130
route add -net 192.187.0.136 netmask 255.255.255.252 gw 192.187.0.130
route add -net 192.187.24.0 netmask 255.255.248.0 gw 192.187.0.130
route add -net 192.187.20.0 netmask 255.255.252.0 gw 192.187.0.130
route add -net 192.187.0.140 netmask 255.255.255.252 gw 192.187.0.130
route add -net 192.187.0.152 netmask 255.255.255.248 gw 192.187.0.130
```
```sh
#ROUTER EISEN
#A3 
auto eth0
iface eth0 inet static
	address 192.187.0.6
	netmask 255.255.255.252
	gateway 192.187.0.5

#A4
auto eth1
iface eth1 inet static
	address 192.187.0.17
	netmask 255.255.255.252

#A5
auto eth2
iface eth2 inet static
	address 192.187.0.21
	netmask 255.255.255.252

#A8
auto eth3
iface eth3 inet static
	address 192.187.0.25
	netmask 255.255.255.252

#A13
auto eth4
iface eth4 inet static
	address 192.187.0.145
	netmask 255.255.255.248

----------------------------------------------------------------------

# .BSHRC EISEN
route add -net 192.187.12.0 netmask 255.255.252.0 gw 192.187.0.22
route add -net 192.187.9.0 netmask 255.255.255.0 gw 192.187.0.22
route add -net 192.187.10.0 netmask 255.255.254.0 gw 192.187.0.26
route add -net 192.187.0.28 netmask 255.255.255.252 gw 192.187.0.26
route add -net 192.187.0.192 netmask 255.255.255.192 gw 192.187.0.26
route add -net 192.187.16.0 netmask 255.255.252.0 gw 192.187.0.26
```

```sh
#ROUTER LINIE
#A8
auto eth0
iface eth0 inet static
	address 192.187.0.26
	netmask 255.255.255.252
	gateway 192.187.0.25

#A9
auto eth1
iface eth1 inet static
	address 192.187.10.1
	netmask 255.255.254.0

#A10
auto eth2
iface eth2 inet static
	address 192.187.0.29
	netmask 255.255.255.252

----------------------------------------------------------------------

# .BASHRC LINIE
route add -net 192.187.0.192 netmask 255.255.255.252 gw 192.187.0.30
route add -net 192.187.16.0 netmask 255.255.252.0 gw 192.187.0.30
```

```sh
#ROUTER LAWINE
#A10
auto eth0
iface eth0 inet static
	address 192.187.0.30
	netmask 255.255.255.252
	gateway 192.187.0.29

#A11
auto eth1
iface eth1 inet static
	address 192.187.0.193
	netmask 255.255.255.192

----------------------------------------------------------------------

# .BASHRC LAWINE
route add -net 192.187.16.0 netmask 255.255.252.0 gw 192.187.0.194
```

```sh
#ROUTER FRIEREN
#A14
auto eth0
iface eth0 inet static
	address 192.187.0.130
	netmask 255.255.255.252
	gateway 192.187.0.129

#A15
auto eth1
iface eth1 inet static
	address 192.187.0.161
	netmask 255.255.255.224

#A16
auto eth2
iface eth2 inet static
	address 192.187.0.133
	netmask 255.255.255.252

----------------------------------------------------------------------

# .BASHRC FRIEREN
route add -net 192.187.0.136 netmask 255.255.255.252 gw 192.187.0.134
route add -net 192.187.24.0 netmask 255.255.248.0 gw 192.187.0.134
route add -net 192.187.20.0 netmask 255.255.252.0 gw 192.187.0.134
route add -net 192.187.0.140 netmask 255.255.255.252 gw 192.187.0.134
route add -net 192.187.0.152 netmask 255.255.255.248 gw 192.187.0.134
```

```sh
#ROUTER FLAMME
#A16
auto eth0
iface eth0 inet static
	address 192.187.0.134
	netmask 255.255.255.252
	gateway 192.187.0.133

#A17
auto eth1
iface eth1 inet static
	address 192.187.0.137
	netmask 255.255.255.252

#A19
auto eth2
iface eth2 inet static
	address 192.187.20.1
	netmask 255.255.252.0

#A20
auto eth3
iface eth3 inet static
	address 192.187.0.141
	netmask 255.255.255.252

----------------------------------------------------------------------

# .BASHRC FLAMME
route add -net 192.187.24.0 netmask 255.255.248.0 gw 192.187.0.138
route add -net 192.187.0.152 netmask 255.255.255.248 gw 192.187.0.142
```

### Testing
- GranzChannel - Eisen
```sh
ping 192.187.0.6
```

![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/5a560788-2ff6-4ad0-ba62-db46c34f327f)


- Aura - LaubHills
```sh
ping 192.187.24.2
```
![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/df4a614a-5bd8-4e68-81d0-ceca35b4e23a)


- SchweMountains - Stark
```sh
ping 192.187.0.18
```

![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/60eb47be-eee3-4421-b441-2b82cd360b5b)


- RoyalCapital - RiegelCanyon
```sh
ping 192.187.16.2
```
![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/99869b33-a3c1-440d-8b14-88d1950a75d0)


- AppetitRegion - GrobeForest
```sh
ping  192.187.9.2
```
![image](https://github.com/aryansfw/Jarkom-Modul-2-B18-2023/assets/114483889/267b9269-0ce5-4794-b6a1-a012a97c6011)
