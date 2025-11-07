en
!
conf t
!
hostname SW-MFDR
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
!
interface f0/1
 description "SRV-eno1"
 switchport access vlan 10
 switchport mode access
!
interface f0/2
 description "RTR-bge5"
 switchport access vlan 10
 switchport mode access
!
interface f0/3
 description "HP-WS"
 switchport access vlan 10
 switchport mode access
!
interface f0/4
 description Borne_1
 switchport access vlan 10
 switchport mode access
!
interface f0/5
 switchport access vlan 10
 switchport mode access
 !
interface f0/11
 description "SRV-eno2"
 switchport access vlan 20
 switchport mode access
!
interface f0/12
 description "RTR-bge0"
 switchport access vlan 20
 switchport mode access
!
interface f0/13
 description "SRV-enp2s0"
 switchport access vlan 30
 switchport mode access
!
interface f0/14
 description "RTR-bge1"
 switchport access vlan 30
 switchport mode access
!
interface f0/21
 description HyperV8-MFDR
 switchport access vlan 10
 switchport mode access
