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
	address 192.235.2.3
	netmask 255.255.255.0
	gateway 192.235.2.0
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
