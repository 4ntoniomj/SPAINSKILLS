Spaning tree protocol es un protocolo capa 2 diseñado para evitar bucles con topología redundante de switches.
Cómo funciona:
- Elige un **Root Bridge** (switch raíz).
- Calcula el **camino más corto** hacia el Root Bridge usando el **Bridge ID** y el **Path Cost**.
- Bloquea puertos redundantes para que no existan bucles, dejando solo un camino activo por VLAN.

Priner switch
```bash
config t
spanning-tree vlan 10 priority 0
spanning-tree vlan 20 priority 4096
spanning-tree vlan 30 priority 8192
```

Segundo
```bash
spanning-tree vlan 10 priority 8192
spanning-tree vlan 20 priority 0
spanning-tree vlan 30 priority 4096
```

Tercero
```bash
spanning-tree vlan 10 priority 4096
spanning-tree vlan 20 priority 8192
spanning-tree vlan 30 priority 0
```

Para los puertos que se van a conectar host finales se puede poner portfast para salar el estado listening y learning, que son estados que usa stp para aprender las rutas.
```bash
ing f0/1
spaning-tree portfast
```

Pero si alguien conectado al puerto empieza a mandar paquetes BPDU (usado por stp) puede ser perjudicial, por eso es importante decir que si alguien envía estos paquetes desactive la interfaz.
```bash
ing f0/1
spaning-tree portfast
spanning-tree bpduguard enable
```

---
## PVST+ (Per-VLAN Spanning Tree Plus)

Corre una instancia stp por cada vlan
```bash
spanning-tree mode pvst
```

---
## RSTP

```bash
spanning-tree mode rapid-pvst
```

---
## PVST + rápido

**Rapid PVST+ (Per-VLAN RSTP Plus):** cada VLAN corre su propia instancia de **RSTP (802.1w)**. Mucho más rápido, pero consume más recursos porque es “una instancia RSTP por VLAN”.