# Segmentación del mensaje

Segmentar un mensaje es mas eficiente ya que si enviamos un mensaje no segmentado y de repente la conexión se pierde, tendremos que volver a enviar todo el mensaje, si esta segmentado no haría falta, esto **aumenta la eficiencia**

**Aumenta la velocidad:** debido a que una gran secuencia de datos se segmenta en paquetes, se pueden enviar grandes cantidades de datos a través de la red sin vincular un enlace de comunicaciones. Esto permite que muchas conversaciones diferentes se intercalen en la red llamada multiplexación.

Al enviar varios paquetes es necesario saber la secuencia con la que se envía para que el receptor lo pueda ordenar.

Al mismo tiempo que la aplicación se va pasando por la pila de protocolos para transmitirse se agrega información de cada nivel, a esto se el denomina **PDU (Protocol Data Unit)**.

En el proceso de encapsulamiento opera desde las capas superiores a inferiores y por cada capa se trata la capa superior como dato puro.
El desencapsulamiento es el proceso inverso.
