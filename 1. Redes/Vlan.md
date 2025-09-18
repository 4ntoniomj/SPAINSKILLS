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

---
## **Tipos de VLAN**

1. **VLAN Default (VLAN 1):** VLAN preconfigurada en switches. No puede eliminarse.

2. **VLAN Nativa:** VLAN sin etiquetar en un enlace troncal. Por defecto es la VLAN 1 (cambiable por seguridad).

3. **VLAN de Gestión:** VLAN dedicada para administrar el switch (ej. VLAN 99). Se asigna una IP para acceso remoto (SSH/HTTP).
```bash
switchport trunk native vlan 99
```

4. **VLAN de Voz:** VLAN prioritaria para tráfico de telefonía IP (Calidad de Servicio - QoS).

---
## **Enrutamiento Inter-VLAN**

Permite comunicación entre VLANs usando:
   
- **Router-on-a-Stick:** Subinterfaces en un router con encapsulación **802.1Q**.
```bash
int f0/0
no shutdown
int f0/0.10
no shutdown
encapsulation dot1Q 10
ip address 192.168.1.1 255.255.255.0
int f0/0.20
no shutdown
encapsulation dot1Q 20
ip address 192.168.2.1 255.255.255.0
do show ip interface brief
```

- **Switch Capa 3:** Inter-VLAN routing directamente en el switch (mediante SVIs - Switch Virtual Interfaces).
  
#### Route-on-a-stick

---
## **Protocolos**

- **DTP (Dynamic Trunking Protocol):** Negocia automáticamente enlaces troncales entre switches (modos: _dynamic auto/desirable_, _trunk/access_).

```bash
switchport mode dynamic desirable # Intenta formar un trunk activamente
switchport mode dynamic auto
switchport nonegotiate # Desactiva DTP en el puerto
```
**dynamic desirable**: el puerto intentará negociar trunk activamente mediante DTP.
**dynamic auto**: el puerto espera pasivamente; si el otro lado también es auto.

- **VTP (VLAN Trunking Protocol):** Sincroniza bases de datos de VLANs en switches de un mismo dominio (modos: _servidor/cliente/transparente_). **No recomendado** por riesgos de seguridad.

```bash
vtp mode server
vtp domain antonio.local
vtp password 1
# Cliente
vtp mode client
vtp domain antonio.local
vtp password 
```

---
## **802.1Q**

Estándar para etiquetar tramas Ethernet con información de VLAN (ID de 12 bits). Los frames etiquetados se envían por enlaces troncales.