## Concepto

Switch capaz de hacer la función de switch capa 2 y enrutamiento

---
## Puertos ruteados

Interfaces físicas de switch que se configuran como las de un router
```bash
interface gigabitEthernet0/1
no switchport
ip address 10.10.10.1 255.255.255.252
no shutdown
```

---

## Puertos SVI (Switched Virtual Interface)

Es una **interfaz virtual** asociada a una VLAN específica. Actúa como la **puerta de enlace (gateway)** predeterminada para todos los dispositivos de esa VLAN, permitiendo el routing inter-VLAN.

```bash
ip routing # Activamos el routing
vlan 10
name vlan10
vlan 20
name vlan20
interface vlan 10 # Interfaz virtual
ip address 192.168.1.254 255.255.255.0
no shutdown
interface vlan 20 # Interfaz virtual
ip address 192.168.2.254 255.255.255.0
no shutdown
int f0/1
switchport trunk ecapsulation dot1q # Fuerza a escoger tipo de encapsulación
switchport mode trunk
switchport trunk allow vlan 10,20
do show vlan
do show ip interface brief
```