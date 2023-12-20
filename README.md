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

