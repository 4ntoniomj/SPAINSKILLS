```bash
ena # Modo super usuario
config t # Modo de configuración
exit # Sale del modo de subconfiguración
end # Pasa del modo de configuración o subconfiguración a modo priivilegiado
```

Configurciones:
```bash
ena
config t
hostname <nombre> # Cambia el nombre del dispositivo
banner motd #<mensaje># # Mensaje de bienvenida
do # Se pone al principio del comando para hacer un comando fuera del modo de configuración
do show startup-config # Vemos la configuración guardada en NVRAM
do show running-config # Configuración en RAM (corriendo)
do copy run star # Guardamos configuración actual
reload # Recargar configuración de NVRAM
erase startup-config # Borra configuración
```

Contraseñas:
```bash
ena
config t
line console 0 # Accedemos a la configurción de la líena de consola
password <contraseña> # Ponemos contraseña
login # Al acceder solicita la contraseña
exit # Salimos de la subconfiguración
enable secret <password> # Establecemos contraseña al superusuario
lint vty 0 15 # Accedemos a la configuración de las líneas de acceso remoto
password <contraseña>
login
exit
service password-encryption # Encriptamos las contraseñas
```

Asignación de IPs:
```bash
ena
config t
interface vlan 1 # Accedemos a la interfaz
ip address 192.168.1.254 255.255.255.0 # Asignamos IP
no shutdown # Activamos
do show ip interface brief # Vemos la config
```