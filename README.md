# grupo-6-

RT-01

enable
configure terminal
hostname RT-01
banner motd "ACESSO APENAS PARA O DEPARTAMENTO DE TI"
enable secret SenhadaEnable
username ruthbraga privilege 15 secret bolo
username kaikyreis privilege 15 secret bolo
username jadisson privilege 15 secret bolo
username guilhermecezar privilege 15 secret bolo
username Leonardomelo privilege 15 secret bolo
login block-for 280 attempts 7 within 600
ip domain-name rede6.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
login local
transport input ssh
exec-timeout 5
exit
line console 0
password SenhadaConsole
login
exit
service password-encryption
interface gigabitEthernet 0/1
no shutdown
interface gigabitEthernet 0/1.26
encapsulation Dot1Q 26
ip address 192.168.26.1 255.255.255.0
ip  helper-address 192.168.249.5
interface gigabitEthernet 0/1.126
encapsulation Dot1Q 126
ip address 192.168.249.1 255.255.255.0
ip  helper-address 192.168.249.5
no shutdown
exit
do wr


SW-CORE

enable
configure terminal
hostname SW-CORE
banner motd "ACESSO APENAS PARA O DEPARTAMENTO DE TI"
enable secret SenhadaEnable
username ruthbraga privilege 15 secret bolo
username kaikyreis privilege 15 secret bolo
username jadisson privilege 15 secret bolo
username guilhermecezar privilege 15 secret bolo
username Leonardomelo privilege 15 secret bolo
login block-for 280 attempts 7 within 600
ip domain-name rede6.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
login local
transport input ssh
exec-timeout 5
exit
line console 0
password SenhadaConsole
login
exit
service password-encryption
vlan 26
name VLAN-26
vlan 126 
name VLAN-126
interface gigabitEthernet 1/1
switchport mode access
switchport access vlan 126
description SRV-01
interface gigabitEthernet 2/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 26,126,99
description INTERFACE ROUTER
interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 26,126,99
interface vlan 126
ip address 192.168.249.253 255.255.255.0
description INTERFACE DE GERENCIAMENTO
no shutdown
exit
ip default-gateway 192.168.249.1
do wr


SW-01

enable
configure terminal
hostname SW-1
banner motd "ACESSO APENAS PARA O DEPARTAMENTO DE TI"
enable secret SenhadaEnable
username ruthbraga privilege 15 secret bolo
username kaikyreis privilege 15 secret bolo
username jadisson privilege 15 secret bolo
username guilhermecezar privilege 15 secret bolo
username Leonardomelo privilege 15 secret bolo
login block-for 280 attempts 7 within 600
ip domain-name rede6.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
login local
transport input ssh
exec-timeout 5
exit
line console 0
password SenhadaConsole
login
exit
service password-encryption
vlan 26
name VLAN-26
vlan 126 
name VLAN-126
interface fastEthernet 0/1
switchport mode access
switchport access vlan 26
description PC 01
interface fastEthernet 0/2
switchport mode access
switchport access vlan 26
description PC 02
interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 26,126,99
interface vlan 126
ip address 192.168.249.254 255.255.255.0
description INTERFACE DE GERENCIAMENTO
no shutdown
exit
ip default-gateway 192.168.249.1
do wr
