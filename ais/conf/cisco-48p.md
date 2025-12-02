```
interface GigabitEthernet1/0/1
 description "SRV-eno1"
 switchport access vlan 10
 switchport mode access
!
interface GigabitEthernet1/0/2
 description "RTR-bge5"
 switchport access vlan 10
 switchport mode access
!
interface GigabitEthernet1/0/3
 description "HP-WS"
 switchport access vlan 10
 switchport mode access
!
interface GigabitEthernet1/0/5
 switchport access vlan 10
 switchport mode access
!
interface GigabitEthernet1/0/13
 description "SRV-eno2"
 switchport access vlan 20
 switchport mode access
!
interface GigabitEthernet1/0/14
 description "RTR-bge0"
 switchport access vlan 20
 switchport mode access
!
interface GigabitEthernet1/0/23
 description "SRV-enp2s0"
 switchport access vlan 30
 switchport mode access
!
interface GigabitEthernet1/0/24
 description "RTR-bge1"
 switchport access vlan 30
 switchport mode access
!
interface GigabitEthernet1/0/25
 description "VMW-FJTS"
 switchport trunk allowed vlan 10,20,30
 switchport mode trunk
!
interface GigabitEthernet1/0/46
 description Borne_1
 switchport access vlan 10
 switchport mode access
!
interface Vlan1
 ip address dhcp
!
interface Vlan10
 description "LAN"
 ip address 10.23.0.128 255.255.192.0
!
interface Vlan20
 description "DMZ"
 ip address 10.23.64.128 255.255.192.0
!
interface Vlan30
 description "SRV"
 ip address 10.23.128.128 255.255.192.0
!
ip default-gateway 10.23.63.254
```