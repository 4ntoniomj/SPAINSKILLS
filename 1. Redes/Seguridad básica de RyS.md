## Configuración

```bash
ena
config t
line console 0 # Accedemos a la configurción de la líena de consola
password <contraseña> # Ponemos contraseña
login # Al acceder solicita la contraseña
exit # Salimos de la subconfiguración
enable secret <password> # Establecemos contraseña al superusuario
service password-encryption
```

---
## Acceso por ssh

```bash
ena
config t
line vty 0 15
password <password>
login # Al acceder pide contraseña
```

---

## CDP

Es un protocolo de capa 2 que permite a los dispositivos Cisco **descubrirse automáticamente** entre sí, **sin necesidad de configurar direcciones IP**. Funciona enviando mensajes multicast de forma periódica a todos sus puertos.

```bash
cdp run # Habilitamos globalmente
no cdp run
int f0/1
cdp enable # Lo habilita en esa interfaz
no cdp enable
cdp time 30 # Envía anuncios cada 30 segundos
cdp holdtime 120  # La información del vecino se mantiene 120 segundos
show cdp
show cdp neighbords
show cdp neighbords detail
```

Si se activa globalmente y se desactiva en una interfaz, para la interfaz estará deshabilitado.

Si se desactiva globalmente y se activa en una interfaz, para la interfaz estará desactivado.