### 1.4
Switch 1

```bash
vlan database
vlan 1
vlan 21
vlan 31
exit
conf t
interface range f1/0 - 2
switchport mode access
switchport acces vlan 1
interface range f1/3 - 5
switchport mode access
switchport acces vlan 21
interface range f1/6 - 8
switchport mode access
switchport acces vlan 31
interface range f1/13 - 15
switchport mode trunk
switchport trunk allowed vlan 1,1002-1005
ip routing
interface vlan 1
no shutdown
ip address 10.0.1.1 255.255.255.0
interface vlan 21
no shutdown
ip address 10.0.21.1 255.255.255.0
interface vlan 31
no shutdown
ip address 10.0.31.1 255.255.255.0
interface f0/0
no shutdown
ip address 10.1.0.1 255.255.255.0

router rip
version 2
network 10.0.0.0
passive-interface vlan 1

end
write
```

Switch 3

```bash
vlan database
vlan 1
vlan 22
vlan 32
exit
conf t
interface range f1/0 - 2
switchport mode access
switchport acces vlan 1
interface range f1/3 - 5
switchport mode access
switchport acces vlan 22
interface range f1/6 - 8
switchport mode access
switchport acces vlan 32
interface range f1/13 - 15
switchport mode trunk
switchport trunk allowed vlan 1,1002-1005
ip routing
interface vlan 1
no shutdown
ip address 10.0.1.3 255.255.255.0
interface vlan 22
no shutdown
ip address 10.0.22.3 255.255.255.0
interface vlan 32
no shutdown
ip address 10.0.32.3 255.255.255.0
interface f0/1
no shutdown
ip address 10.2.0.3 255.255.255.0

router rip
version 2
network 10.0.0.0
passive-interface vlan 1

end
write
```

Switch 2

```bash
vlan database
vlan 1
exit
conf t
interface range f1/0 - 2
switchport mode access
switchport acces vlan 1
interface range f1/13 - 15
switchport mode trunk
switchport trunk allowed vlan 1,1002-1005
ip routing
interface vlan 1
no shutdown
ip address 10.0.1.2 255.255.255.0
interface f0/0
no shutdown
ip address 10.1.0.2 255.255.255.0
interface f0/1
no shutdown
ip address 10.2.0.2 255.255.255.0

router rip
version 2
network 10.0.0.0
passive-interface vlan 1

end
write
```

PC1

```bash
ip 10.0.1.10/24 10.0.1.1
```

PC2

```bash
ip 10.0.21.10/24 10.0.21.1
```

PC3

```bash
ip 10.0.31.10/24 10.0.31.1
```

PC4

```bash
ip 10.0.1.20/24 10.0.1.3
```

PC5

```bash
ip 10.0.22.20/24 10.0.22.3
```

PC6

```bash
ip 10.0.32.20/24 10.0.32.3
```