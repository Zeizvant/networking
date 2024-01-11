# VLAN
Switch>enable 
Switch#config
Switch(config)#vlan 10
Switch(config-vlan)#exit
Switch(config)#vlan 20
Switch(config-vlan)#exit
Switch(config)#interface fastEthernet 0/1
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 10
Switch(config)#interface fastEthernet 0/24
Switch(config-if)#switchport mode trunk

Router(config-subif)# no shutdown
Router(config-subif)# exit
Router(config)# interface fastEthernet 0/0.10
Router(config-subif)#encaplusation dot1Q10
Router(config-subif)#ip address 192.168.1.1 255.255.255.0

Static routing
Router(config)# ip route 10.10.20.0 255.255.255.0 10.10.10.2 -> (router interface ip)

Rip

router rip
version 2
no auto-summary
network 192.168.1.0

Eigrp

router eigrp 1
network 192.168.13.0 0.0.0.255
network 192.168.12.0 0.0.0.255

OSPF

router  ospf 1
network 192.168.13.0 0.0.0.255 area 0
network 192.168.12.0 0.0.0.255 area 0

IPV6 eigrp

Router(config)#ipv6 unicast-routing
Router(config)# interface GigabitEthernet 0/1
Router(config-if)#ipv6 enable
Router(config)# interface loopback 0
Router(config-if)#ipv6 address 2001::1/128 (სხვა როუტერზე 2001::2/128)
Router(config)#ipv6 router eigrp 1
Router(config-rtr)$router-id 1.1.1.1
Router(config-rtr)#no-shutdown
Router(config)#interface GigabitEthernet  0/1
Router(config-if)#ipv6 eigrp 1
Router(config)#interface loopback 0
Router(config-if)#ipv6 eigrp 1

IPV6 ospf

Router(config)#ipv6 unicast-routing
Router(config)# interface loopback 0
Router(config-if)#ipv6 address 2001::1/128 (სხვა როუტერზე 2001::2/128)
Router(config)# interface GigabitEthernet 0/1
Router(config-if)#ipv6 enable
Router(config)#ipv6 router ospf 1
Router(config-rtr)$router-id 1.1.1.1
Router(config-rtr)#exit
Router(config)#interface GigabitEthernet  0/1
Router(config-if)#ipv6 ospf 1 area 0
Router(config)#interface loopback 0
Router(config-if)#ipv6 ospf 1 area 0

Acess list
Router(config)#access-list deny ან acess
Router(config)#access-list 10 deny 172.16.40.0 0.0.0.255
Router(config)# interface fastEthernet 0/1
Router(config-if)# ip acess-group 10  out

Router(config)# acess-list 10 permit ip any any

STP
Switch(config)#spanning-tree vlan 10 root primary 
Switch2(config)#spanning-tree vlan 20 root primary 
Switch2(config)#spanning-tree vlan 10 root secondary



