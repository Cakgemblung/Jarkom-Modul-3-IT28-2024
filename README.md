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
