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
- [Konfigurasi](#konfigurasi)
- [IP Subnet Client](#ip-subnet-client)
- [SOAL](#soal)

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
- GrobeForest
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

## Routing
- Aura
```
# A2
route add -net 10.65.0.0 netmask 255.255.248.0 gw 10.65.14.130
# A1 
route add -net 10.65.8.0 netmask 255.255.252.0 gw 10.65.14.130

# A5 
route add -net 10.65.14.136 netmask 255.255.255.252 gw 10.65.14.134
# A7 
route add -net 10.65.12.0 netmask 255.255.254.0 gw 10.65.14.134
# A8 
route add -net 10.65.14.0 netmask 255.255.255.128 gw 10.65.14.134
# A9 
route add -net 10.65.14.144 netmask 255.255.255.252 gw 10.65.14.134
# A10
route add -net 10.65.14.148 netmask 255.255.255.252 gw 10.65.14.134
```

- Heiter
```
# A3
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.65.14.129
```

- Frieren
```
# A7
route add -net 10.65.12.0 netmask 255.255.254.0 gw 10.65.14.142
# A8
route add -net 10.65.14.0 netmask 255.255.255.128 gw 10.65.14.142
# A9
route add -net 10.65.14.144 netmask 255.255.255.252 gw 10.65.14.142
# A10
route add -net 10.65.14.148 netmask 255.255.255.252 gw 10.65.14.142
# A2
route add -net 10.65.0.0 netmask 255.255.248.0 gw 10.65.14.133
# A1
route add -net 10.65.8.0 netmask 255.255.248.0 gw 10.65.14.133

route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.65.14.133
```

- Himmel
```
# A9
route add -net 10.65.14.144 netmask 255.255.255.252 gw 10.65.14.3
# A10
route add -net 10.65.14.148 netmask 255.255.255.252 gw 10.65.14.3
# A6
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.65.14.141
```

- Fern
```
# A8
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.65.14.1
```

## DNS
Gunakan script dibawah pada `Richter`.

```
echo "nameserver 192.168.122.1" >/etc/resolv.conf

apt update
apt install bind9 dnsutils -y

# Backup existing file
cp /etc/bind/named.conf.options /etc/bind/named.conf.options/bak

# Configuration data
echo 'options {
    listen-on-v6 { none; };
    directory "/var/cache/bind";

    # Forwarders
    forwarders {
        192.168.122.1;
    };

    # If there is no answer from the forwarders, dont attempt to resolve recursively
    forward only;

    dnssec-validation no;

    auth-nxdomain no;    # conform to RFC1035
    allow-query { any; };
};' >/etc/bind/named.conf.options

service bind9 restart
service bind9 status
```

# IP Subnet Client
### DHCP-Server
`/etc/default/isc-dhcp-server` isi file tersebut dengan menggunakan script seperti dibawah.
```
# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)
# Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
#DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf
# Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
#DHCPDv4_PID=/var/run/dhcpd.pid
#DHCPDv6_PID=/var/run/dhcpd6.pid
# Additional options to start dhcpd with.
#       Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=\"\"
# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. \"eth0 eth1\".
INTERFACESv4=\"eth0\"
INTERFACESv6=\"\"" >/etc/default/isc-dhcp-server
```

`/etc/dhcp/dhcpd.conf` isi file tersebut dengan menggunakan script seperti dibawah.
```
# A1
subnet 10.65.8.0 netmask 255.255.252.0 {
    range 10.65.8.3 10.65.11.254;
    option routers 10.65.8.1;
    option broadcast-address 10.65.11.255;
    option domain-name-servers 10.65.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

# A2
subnet 10.65.0.0 netmask 255.255.248.0 {
    range 10.65.0.1 10.65.7.254;
    option routers 10.65.0.1;
    option broadcast-address 10.65.7.255;
    option domain-name-servers 10.65.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

# A3
subnet 10.65.14.128 netmask 255.255.255.252 {
}

# A4
subnet 10.65.14.132 netmask 255.255.255.252 {
}

# A5
subnet 10.65.14.136 netmask 255.255.255.252 {
}

# A6
subnet 10.65.14.140 netmask 255.255.255.252 {
}

# A7 
subnet 10.65.12.0 netmask 255.255.254.0 {
    range 10.65.12.2 10.65.13.254;
    option routers 10.65.12.1;
    option broadcast-address 10.65.13.255;
    option domain-name-servers 10.65.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

# A8
subnet 10.65.14.0 netmask 255.255.255.128 {
    range 10.65.14.2 10.65.14.126;
    option routers 10.65.14.1;
    option broadcast-address 10.65.14.127;
    option domain-name-servers 10.65.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

# A9
subnet 10.65.14.144 netmask 255.255.255.252 {
}

# A10
subnet 10.65.14.148 netmask 255.255.255.252 {
}
" >/etc/dhcp/dhcpd.conf

rm /var/run/dhcpd.pid

service isc-dhcp-server restart
service rsyslog start

service isc-dhcp-server status
```

### DHCP Relay
Gunakan script dibawah pada seluruh node router.
```
apt update
apt-get install isc-dhcp-relay rsyslog -y

echo "
SERVERS=\"10.65.14.150\"
INTERFACES=\"eth0 eth1 eth2\"
OPTIONS=\"\"" >/etc/default/isc-dhcp-relay

service rsyslog start
service isc-dhcp-relay restart
service isc-dhcp-relay status
```

# SOAL
## Soal 1
Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE

Lakukan konfigurasi iptables pada

### Aura
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.128/30 --to-source 192.168.122.2
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.132/30 --to-source 192.168.122.2
```

### Frieren
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.140/30 --to-source 10.65.14.134
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.136/30 --to-source 10.65.14.134
```

### Heiter
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.0.0/21 --to-source 10.65.14.130
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.8.0/22 --to-source 10.65.14.130
```

### Himmel
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.0/25 --to-source 10.65.14.142
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.12.0/23 --to-source 10.65.14.142
```

### Fern
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.144/30 --to-source 10.65.14.3
iptables -t nat -A POSTROUTING -o eth0 -j SNAT -s 10.65.14.148/30 --to-source 10.65.14.3
```

### Testing Soal 1
Untuk testing apakah sudah bisa akses keluar, dilakukan ping google.com pada setiap node

Uji coba ping pada SchwerMountains

![image6](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/35c1604f-95db-4f9c-a878-a79657dcd46f)

Uji coba ping pada Fern

![image12](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/b8bb0a45-f2d1-4dd9-bedb-3e97fa17e420)


## Soal 2
Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

Jalankan command berikut pada **LaubHills**
```
iptables -F
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP
iptables -A INPUT -p udp -j DROP
```
### Testing Soal 2
Pada **SchwerMountain**, jalankan command `nmap -p 80 10.65.12.2`. Dapat dilihat bahwa STATE nya adalah filtered untuk port 80

![image7](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/b8810858-bc7f-4325-b49b-09d213bf2c93)


Lalu, coba jalankan command `nmap -p 8080 10.65.12.2`. Dapat dilihat bahwa STATE nya adalah closed pada port 8080, di mana artinya koneksi terhubung tetapi tidak ada layanan yang aktif 

![image14](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/534513b7-0f91-414c-949e-d530ac86c61e)

## Soal 3
Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

Jalankan command berikut pada **REVOLTE** dan **RICHTER** (sebagai DHCP dan DNS Server)

```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```
### Testing Soal 3
Lakukan ping ke Revolte dari keempat client

Ping 1 Device

![image3](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/c591fd64-110b-4e98-8c13-8f31f5bd8fea)

Ping 2 Device

![image10](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/756d6d09-f13b-4664-ad74-6fcd21f6425a)

Ping 3 Device

![image16](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/f34482d9-b0a7-47c5-b5b3-4901b6c10c6b)

Ping 4 Device 

![image8](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/e3019b65-c459-4bce-83eb-af7bafe45ef1)

Dapat dilihat bahwa pada GrobeForest sudah tidak dapat melakukan ping, dikarenakan ping sudah dijalankan secara bersamaan di ketiga client lainnya.

## Soal 4
Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

Jalankan command berikut pada **SEIN** dan **STARK**

```
iptables -A INPUT -p tcp --dport 22 -s 10.65.8.0/22 -j ACCEPT
```

### Testing Soal 4
Pada **Sein**, jalankan command berikut untuk membuka koneksi port SSH
```
nc -l -p 22
```
Lakukan testing di **GrobeForest**. GrobeForest berhasil terhubung ke Sein melalui telnet

![image11](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/f11450df-f837-4eba-9e26-28f1f2c7847c)

Lakukan testing di **TurkRegion**. TurkRegion tidak berhasil terhubung ke Sein dan mengalami Connection refused.

![image1](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/8bfed818-4d25-413a-8d8f-d80f7b97cb9d)

## Soal 5
Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.

Jalankan command berikut pada **SEIN** dan **STARK**
```
iptables -A INPUT -p tcp --dport 22 -s 10.65.8.0/22 -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
```

### Testing Soal 5
Pada **LaubHills**, lakukan ping pada saat Rabu Jam 12 Siang. Ping dapat dilakukan karena merupakan jam kerja. 

![image13](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/8ca5e318-7701-419d-9372-08110ae1a5fc)

Lakukan ping kembali pada saat Rabu Jam 8 Malam. Ping gagal karena jam kerja sudah berakhir.

![image15](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/9bfb962a-97d7-4a11-b0aa-d6eb659a3282)

## Soal 6
Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).

Jalankan command berikut pada **SEIN** dan **STARK** 

```
iptables -A INPUT -p tcp --dport 22 -s 10.65.8.0/22 -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j DROP
iptables -A INPUT -p tcp --dport 22 -s 10.65.8.0/22 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j DROP

iptables -A INPUT -p tcp --dport 22 -j
```

### Testing Soal 6
Pada **LaubHills**, lakukan ping pada saat Rabu Jam 12.30 Siang. Ping gagal karena memasuki jam istirahat.

![image9](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/a31b72ec-a0bf-4dfd-8a14-94c53c54b30f)

Lakukan ping kembali pada saat Jumat Jam 11 Siang. Ping gagal karena memasuki jam sholat jumat.

![image4](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/103043684/2e5eda85-a8f3-47ee-af2c-f78eaefd807e)

## Soal 7
Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.

Pada node **HEITER** dan **FRIEREN** masukan command sebagai berikut:
```
iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.69.8.2 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.69.8.2
iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.69.8.2 -j DNAT --to-destination 10.69.14.138
iptables -A PREROUTING -t nat -p tcp --dport 443 -d 10.69.14.138 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.69.14.138
iptables -A PREROUTING -t nat -p tcp --dport 443 -d 10.69.14.138 -j DNAT --to-destination 10.69.8.2
```

Lalu lakukan konfigurasi sebagai berikut pada web server:
1. Install apache2 dengan `apt install apache2 -y`.
2. Lakukan konfigurasi pada `/etc/apache2/ports.conf` sebagai berikut:
```
Listen 80
Listen 443

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>
```
3. Lakukan konfigurasi pada `/var/www/html/index.html` menjadi sesuatu yang menandakan node yang sedang ditujukan **Sein** / **Stark**
4. Lakukan konfigurasi pada `/etc/apache2/sites-available/sein.conf`:
```
<VirtualHost *:80>
    ServerName 10.65.8.2
    DocumentRoot /var/www/html
</VirtualHost>
<VirtualHost *:443>
    ServerName 10.65.8.2
    DocumentRoot /var/www/html
</VirtualHost>
```
5. Lakukan konfigurasi pada `/etc/apache2/sites-available/stark.conf`
```
<VirtualHost *:80>
    ServerName 10.65.14.138
    DocumentRoot /var/www/html
  #  ErrorLog \${APACHE_LOG_DIR}/error.log
   # CustomLog \${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
<VirtualHost *:443>
    ServerName 10.65.14.138
    DocumentRoot /var/www/html
  #  ErrorLog \${APACHE_LOG_DIR}/error.log
  #  CustomLog \${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### Testing Soal 7
```
curl 10.65.8.2:80
curl 10.65.14.138:443
```
![Screenshot 2023-12-20 194915](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/113527799/21954421-13d9-45ff-abd9-26ec003d0ced)

## Soal 8
Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

```
revolte="10.65.14.148/30"
pemilu_start=$(date -d "2023-10-19T00:00" +"%Y-%m-%dT%H:%M")
pemilu_end=$(date -d "2024-02-15T00:00" +"%Y-%m-%dT%H:%M")

iptables -A INPUT -p tcp -s $revolte --dport 80 -m time --datestart "$pemilu_start" --datestop "$pemilu_end" -j DROP
```

## Soal 9
Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. 
(clue: test dengan nmap).

submit command dibawah di webserver:
```
iptables -N portscan
iptables -A INPUT -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP
iptables -A FORWARD -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP
iptables -A INPUT -m recent --name portscan --set -j ACCEPT
iptables -A FORWARD -m recent --name portscan --set -j ACCEPT
```

Lalu lakukan testing terhdapat webserver dari client dengan cara sebagai berikut:
`10.65.8.2 -c 25`.
![image](https://github.com/wiridlangit/Jarkom-Modul5-IT03-2023/assets/113527799/dd8ed607-829d-4615-86df-2e53357dc75f)

## Soal 10
Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 

`iptables -A INPUT -j LOG --log-level debug --log-prefix 'Dropped Packet' -m limit --limit 1/second --limit-burst 10`

tambahkan command diatas untuk semua node.
