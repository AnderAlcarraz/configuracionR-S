# configuracionR-S
Configuracion de la red LAN con las interfaz vlan 


R1
*******
enable
conf terminal
hostname R1
inter g0/0.10
encapsulation dot1Q 10
ip add	192.168.1.1 255.255.255.0
no shut
ex
******* 
inter g0/0.20
encapsulation dot1Q 20
ip add	192.168.2.1 255.255.255.0
no shut
ex
*******
inter g0/0.30
encap doq 30
ip add	192.168.3.1 255.255.255.0
no shut
ex
*******
inter g0/0.40
encapsulation dot1Q 40
ip add	192.168.4.1 255.255.255.0
no shut
ex
******
inter g0/0.50
encap doq 50
ip add	192.168.5.1 255.255.255.0
no shut
ex
R1(config)#interface g0/0
R1(config-if)#no shu
R1(config-if)#no shutdown 
******SAVE CONFIG***
copy running-config startup-config

************wtrunk***
enable 
conf terminal
vlan 10
name Finanzas
ex
vlan 20
name Operaciones
ex
vlan 30
name Ventas
ex
vlan 40
name Mantenimiento
ex
vlan 50
name Logistica
ex
interface g0/1
switchport mode trunk
ex


copy running-config startup-config

****SFinanzas****
en
conf terminal 
SFinanzas(config)#vlan 10
SFinanzas(config-vlan)#name Finanzas
interface ran f0/2-23
switchport mode access
switchport access vlan 10
end
copy running-config startup-config
============================================================
****SOperaciones****
en
conf terminal 
SFinanzas(config)#vlan 20
SFinanzas(config-vlan)#name Operaciones
interface ran f0/2-23
switchport mode access
switchport access vlan 20
ex
inter	f0/24
switchport mode trunk
copy running-config startup-config
============================================================
*****SVentas******
en
conf terminal 
SFinanzas(config)#vlan 30
SFinanzas(config-vlan)#name Ventas
interface ran f0/2-23
switchport mode access
switchport access vlan 30
ex
inter	f0/24
switchport mode trunk
copy running-config startup-config
===========================================================
*****SMantenimiento***
en
conf terminal 
SFinanzas(config)#vlan 40
SFinanzas(config-vlan)#name Mantenimiento
interface ran f0/3-23
switchport mode access
switchport access vlan 40
ex
inter	f0/24
switchport mode trunk
copy running-config startup-config
===========================================================
*****sLogistica*****
en
conf terminal 
SFinanzas(config)#vlan 50
SFinanzas(config-vlan)#name Logistica
interface ran f0/2-23
switchport mode access
switchport access vlan 50
ex
inter	f0/24
switchport mode trunk
copy running-config startup-config
============================================================




