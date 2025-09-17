## MAC

Dirección física de una tarjeta de red compuesta por 48 bits

---

## Tabla MAC

Base de datos de switch que contiene direcciones MAC de equipos conectados por los puertos físicos.

Para ver la tabla MAC:
```bash
show mac-address-table
```

---

## Métodos de Reenvío del Switch

1. **Unicast:** Reenvía la trama **solo por un puerto específico** (el asociado a la MAC de destino en la tabla).

2. **Flooding (Inundación):** Reenvía la trama por **todos los puertos, excepto por el de entrada**. Se usa cuando la MAC de destino es **desconocida** (no está en la tabla) o es una dirección de **broadcast/multicast**.

3. **Filtering (Filtrado):** **Descarta** la trama. Ocurre cuando la dirección MAC de destino está en la misma tabla que el puerto de entrada (el destino está en el mismo segmento que el origen).