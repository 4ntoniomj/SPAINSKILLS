## ARP

Traduce direcciones IPv4 a direcciones MAC.

#### **Funcionamiento básico:**

1. Un host necesita enviar un paquete a una IP dentro de la misma red.

2. Consulta su tabla ARP para ver si ya sabe qué MAC corresponde a esa IP.

3. Si no está, envía un ARP Request (broadcast: “¿Quién tiene esta IP?”).

4. El host dueño de esa IP responde con un ARP Reply (unicast: “yo soy, esta es mi MAC”).

5. El host guarda esa asociación en su tabla ARP por un tiempo limitado.

--- 
## Detección de vecinos IPv6 (NDP)

**NDP (Neighbor Discovery Protocol)** tiene la misma finalidad que arp y añade funciones como ver que vecinos siguen activos y descube routers y configuraciones.

#### Funcionamiento 

1. **Necesidad de comunicación**

	- Tu host A quiere enviar datos a la IP de un vecino B en la misma red local.
	- Antes de enviar datos, necesita saber **la dirección MAC de B**.

2. **Envía un Neighbor Solicitation (NS)**

	- Tu host pregunta: _“¿Quién tiene esta IP? Necesito tu MAC.”
	- Esto se envía como **mensaje multicast** (no broadcast como en ARP).

3. **Recibe un Neighbor Advertisement (NA)**

	- El vecino B responde: _“Soy yo, mi MAC es XX:XX:XX:XX:XX:XX”_.
	- Este mensaje va directamente a A (unicast).

4. **Actualiza la tabla de vecinos (Neighbor Cache)**

	- Host A guarda la IP ↔ MAC en su tabla para usarla de nuevo.

5. **Comprobación continua (Neighbor Unreachability Detection)**

	- IPv6 revisa periódicamente si el vecino sigue accesible.
	- Si deja de responder, marca la entrada como “no alcanzable” y volverá a preguntar antes de enviar paquetes.
