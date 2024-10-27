# Jarkom-Modul-3-IT28-2024

## IT 28

|Nama  | NRP |
|--    | --  |
| Muhammad Hildan Adiwena  | 5027231077 |
| Syela Zeruya Tandi Lalong  | 5027231076 |

## Topologi

![WhatsApp Image 2024-10-22 at 19 22 42](https://github.com/user-attachments/assets/ca349be7-f441-4842-9ed8-8b3dbf3d0d93)

## Config

### Paradis
```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.247.1.0
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.247.2.0
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.247.3.0
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.247.4.0
	netmask 255.255.255.0
```

### Fritz
```
auto eth0
iface eth0 inet static
	address 192.247.4.2
	netmask 255.255.255.0
	gateway 192.247.4.0
```

### Tybur
```
auto eth0
iface eth0 inet static
	address 192.247.4.3
	netmask 255.255.255.0
	gateway 192.247.4.0
```

### Warhammer
```
auto eth0
iface eth0 inet static
	address 192.247.3.4
	netmask 255.255.255.0
	gateway 192.247.3.0
```

### Beast
```
auto eth0
iface eth0 inet static
	address 192.247.3.2
	netmask 255.255.255.0
	gateway 192.247.3.0
```

### Colossal
```
auto eth0
iface eth0 inet static
	address 192.247.3.3
	netmask 255.255.255.0
	gateway 192.247.3.0
```

### Annie
```
auto eth0
iface eth0 inet static
	address 192.247.1.2
	netmask 255.255.255.0
	gateway 192.247.1.0
```

### Berthold
```
auto eth0
iface eth0 inet static
	address 192.247.1.3
	netmask 255.255.255.0
	gateway 192.247.1.0
```

### Reiner
```
auto eth0
iface eth0 inet static
	address 192.247.1.4
	netmask 255.255.255.0
	gateway 192.247.1.0
```

### Armin
```
auto eth0
iface eth0 inet static
	address 192.247.2.2
	netmask 255.255.255.0
	gateway 192.247.2.0
```

### Eren
```
auto eth0
iface eth0 inet static
	address 192.247.2.3
	netmask 255.255.255.0
	gateway 192.247.2.0
```

### Mikasa
```
auto eth0
iface eth0 inet static
	address 192.247.2.4
	netmask 255.255.255.0
	gateway 192.247.2.0
```

### Zeke & Erwin
```
auto eth0
iface eth0 inet dhcp
```

## Soal 0
Pulau Paradis telah menjadi tempat yang damai selama 1000 tahun, namun kedamaian tersebut tidak bertahan selamanya. Perang antara kaum Marley dan Eldia telah mencapai puncak. Kaum Marley yang dipimpin oleh Zeke, me-register domain name marley.yyy.com untuk worker Laravel mengarah pada Annie. Namun ternyata tidak hanya kaum Marley saja yang berinisiasi, kaum Eldia ternyata sudah mendaftarkan domain name eldia.yyy.com untuk worker PHP (0) mengarah pada Armin.

### Script
> soal0.sh
```
apt-get update
apt-get install bind9 -y

forward="options {
directory \"/var/cache/bind\";
forwarders {
  	   192.168.122.1;
};

allow-query{any;};
listen-on-v6 { any; };
};
"
echo "$forward" > /etc/bind/named.conf.options

echo "zone \"marley.it28.com\" {
	type master;
	file \"/etc/bind/modul3/marley.it28.com\";
};

zone \"eldia.it28.com\" {
	type master;
	file \"/etc/bind/modul3/eldia.it28.com\";
};
" > /etc/bind/named.conf.local

mkdir /etc/bind/modul3

riegel="
;
;BIND data file for local loopback interface
;
\$TTL    604800
@    IN    SOA    marley.it28.com. root.marley.it28.com. (
        2        ; Serial
                604800        ; Refresh
                86400        ; Retry
                2419200        ; Expire
                604800 )    ; Negative Cache TTL
;                   
@    IN    NS    marley.it28.com.
@       IN    A    192.247.1.2
"
echo "$riegel" > /etc/bind/modul3/marley.it28.com

granz="
;
;BIND data file for local loopback interface
;
\$TTL    604800
@    IN    SOA    eldia.it28.com. root.eldia.it28.com. (
        2        ; Serial
                604800        ; Refresh
                86400        ; Retry
                2419200        ; Expire
                604800 )    ; Negative Cache TTL
;                   
@    IN    NS    eldia.it28.com.
@       IN    A    192.247.2.2
"
echo "$granz" > /etc/bind/modul3/eldia.it28.com

service bind9 restart
```


## Soal 1-5
(1) Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.

Jauh sebelum perang dimulai, ternyata para keluarga bangsawan, Tybur dan Fritz, telah membuat kesepakatan sebagai berikut:
1. Semua Client harus menggunakan konfigurasi ip address dari keluarga Tybur (dhcp).
3. Client yang melalui bangsa marley mendapatkan range IP dari [prefix IP].1.05 - [prefix IP].1.25 dan [prefix IP].1.50 - [prefix IP].1.100 (2)
4. Client yang melalui bangsa eldia mendapatkan range IP dari [prefix IP].2.09 - [prefix IP].2.27 dan [prefix IP].2 .81 - [prefix IP].2.243 (3)
Client mendapatkan DNS dari keluarga Fritz dan dapat terhubung dengan internet melalui DNS tersebut (4)
5. Dikarenakan keluarga Tybur tidak menyukai kaum eldia, maka mereka hanya meminjamkan ip address ke kaum eldia selama 6 menit. Namun untuk kaum marley, keluarga Tybur meminjamkan ip address selama 30 menit. Waktu maksimal dialokasikan untuk peminjaman alamat IP selama 87 menit. (5)

### Script
> soal1-5.sh (Paradis)
```
apt-get update
apt install isc-dhcp-relay -y

service isc-dhcp-relay start 

echo '# Defaults for isc-dhcp-relay initscript

# sourced by /etc/init.d/isc-dhcp-relay
# installed at /etc/default/isc-dhcp-relay by the maintainer scripts

#
# This is a POSIX shell fragment
#

# What servers should the DHCP relay forward requests to?
SERVERS="192.247.4.3" 

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3 eth4"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""' > /etc/default/isc-dhcp-relay


echo net.ipv4.ip_forward=1 > /etc/sysctl.conf

service isc-dhcp-relay restart
```

> soal1-5 (Tybur)
```
apt-get update
apt-get install isc-dhcp-server -y

echo 'INTERFACESv4="eth0"
INTERFACESv6=""
' > /etc/default/isc-dhcp-server

subnet="option domain-name \"example.org\";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

ddns-update-style-none;

subnet 192.247.1.0 netmask 255.255.255.0 {
    range 192.247.1.5 192.247.1.25;
    range 192.247.1.50 10.247.1.100;
    option routers 192.247.1.1;
    option broadcast-address 192.247.1.255;
    option domain-name-servers 192.247.4.2;
    default-lease-time 360;
    max-lease-time 5220;
}

subnet 192.247.2.0 netmask 255.255.255.0 {
    range 192.247.2.9 192.247.2.27;
    range 192.247.2.81 192.247.2.243;
    option routers 192.247.2.1;
    option broadcast-address 192.247.2.255;
    option domain-name-servers 192.247.4.2;
    default-lease-time 1800;
    max-lease-time 5220;
}

subnet 192.247.3.0 netmask 255.255.255.0 {
}

subnet 192.247.4.0 netmask 255.255.255.0 {
}

"
echo "$subnet" > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
