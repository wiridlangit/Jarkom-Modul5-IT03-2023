# Kelompok: IT03
### Anggota: 
Nama | NRP | Github 
--- | --- | --- |
Adiba Zalfa Camilla | 5027211060 | https://github.com/dibazalfa
Wiridlangit Suluh Jiwangga | 5027211064 | https://github.com/wiridlangit

# IP Prefix
`10.65`

# Spreadsheet
https://docs.google.com/spreadsheets/d/1i99nOF023sdb0iFERJQ4ZItxRdEgZ2EGgY3sLRmkUtw/edit#gid=639936282

## Daftar Isi 
- [Topologi](#topologi)
- [Rute Subnet](#rute-subnet)
- [Tree VLSM](#tree-vlsm)
- [Pembagian IP](#pembagian-ip-vlsm)

# Topologi
### GNS3 | VLSM |
![Screenshot 2023-12-20 163127](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/8c2882a5-a009-4cd0-a091-8e135f5559b7)

# Rute Subnet
![Screenshot 2023-12-20 163746](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/064f0853-f671-4d72-84d5-bead0ebd9898)

# Tree VLSM
Berikut adalah Tree yang digunakan sebagai visualisasi VLSM.

<img width="4023" alt="Opportunity Solution Tree - Free Template (Community)" src="https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/41bd9326-2a14-4dc1-9a79-01a031888f63">

# Pembagian IP VLSM
Berikut adalah pembagian IP pada VLSM.

![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/35ae9568-74e5-412f-8868-eb31bed35754)

# Konfigurasi
### Router
- Aura
```
auto eth0
iface eth0 inet static
    address 192.168.122.2
    netmask 255.255.255.252
    gateway 192.168.122.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf

# config for eth1
auto eth1
iface eth1 inet static
    address 10.65.14.133
    netmask 255.255.255.252

# config for eth2
auto eth2
iface eth2 inet static
    address 10.65.14.129
    netmask 255.255.255.252
```

- Heiter
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.130
    netmask 255.255.255.252
    gateway 10.65.14.129

# config for eth1
auto eth1
iface eth1 inet static
    address 10.65.0.1
    netmask 255.255.248.0

# config for eth2
auto eth2
iface eth2 inet static
    address 10.65.8.1
    netmask 255.255.252.0
```

- Frieren
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.134
    netmask 255.255.255.252
    gateway 10.65.14.133
    
# config for eth1
auto eth1
iface eth1 inet static
    address 10.65.14.137
    netmask 255.255.255.252

# config for eth2
auto eth2
iface eth2 inet static
    address 10.65.14.141
    netmask 255.255.255.252
```

- Himmel
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.142
    netmask 255.255.255.252
    gateway 10.65.14.141

# config for eth1
auto eth1
iface eth1 inet static
    address 10.65.12.1
    netmask 255.255.254.0

# config for eth2
auto eth2
iface eth2 inet static
    address 10.65.14.1
    netmask 255.255.255.128
```

- Fern
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.3
    netmask 255.255.255.128
    gateway 10.65.14.1

# config for eth1
auto eth1
iface eth1 inet static
    address 10.65.14.145
    netmask 255.255.255.252

# config for eth2
auto eth2
iface eth2 inet static
    address 10.65.14.149
    netmask 255.255.255.252
```

### DNS Server
- Richter
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.146
    netmask 255.255.255.252
    gateway 10.65.14.145
```

### DHCP Server
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.150
    netmask 255.255.255.252
    gateway 10.65.14.149
```

### Web Server
- Sein
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.8.2
    netmask 255.255.252.0
    gateway 10.65.8.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Stark
```
# config for eth0
auto eth0
iface eth0 inet static
    address 10.65.14.138
    netmask 255.255.255.252
    gateway 10.65.14.137
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

### Client
- GrobeForest, LaubHills, SchwerMountain
```
# config for eth0
auto eth0
iface eth0 inet dhcp
    gateway 10.65.8.1
```

- TurkRegion
```
# config for eth0
auto eth0
iface eth0 inet dhcp
    gateway 10.65.0.1
```

- LaubHills
```
# config for eth0
auto eth0
iface eth0 inet dhcp
    gateway 10.65.12.1
```

- SchwerMountain
```
# config for eth0
auto eth0
iface eth0 inet dhcp
    gateway 10.65.14.1
```
