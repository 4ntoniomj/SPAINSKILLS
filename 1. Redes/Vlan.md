Virtual local area network

```bash
vtp mode server # Servidor para no crear vlan en todo los switches
vtp domain antonio.local
vtp password 1
vlan 10 # Creamos vlan 10
name vlan10 # Con nombre
int f3/1 # Accedemos
switchport mode trunk # Mode trunk que todas las vlan accedan y se puedan comunicar con otros switches
switchport allowed vlan 10,20 # Vlans permitidas
int f1/1
switchport mode acces # Modo acceso
switchport access vlan 10 # A la vlan 10
do show ip interfaces brief
do show interface vlan 10
```