ip default-gateway 10.23.63.254
interface 1
   name "SRV-eno1"
   exit
interface 2
   name "RTR-bge5"
   exit
interface 3
   name "SRV-eno2"
   exit
interface 4
   name "RTR-bge0"
   exit
interface 5
   name "SRV-enp2s0"
   exit
interface 6
   name "RTR-bge1"
   exit
interface 7
   name "VMW-FJTS"
   exit
interface 8
   name "HP-WS"
   exit
snmp-server community "public" unrestricted
vlan 1
   name "DEFAULT_VLAN"
   no untagged 1-8
   untagged 9-10
   ip address dhcp-bootp
   exit
vlan 10
   name "LAN"
   untagged 1-2,8
   tagged 7
   ip address 10.23.0.128 255.255.192.0
   exit
vlan 20
   name "DMZ"
   untagged 3-4
   tagged 7
   ip address 10.23.64.128 255.255.192.0
   exit
vlan 30
   name "SRV"
   untagged 5-7
   ip address 10.23.128.128 255.255.192.0
   exit
