---
layout: page
title: "Routers"
permalink: /routers/
---

# Configuración de Rutas Estáticas y Dinámicas

## Introducción

En las redes de computadoras, las rutas permiten que los paquetes de datos viajen de un origen a un destino a través de diferentes redes. Existen dos tipos principales de enrutamiento: estático y dinámico.

### Rutas Estáticas

Las rutas estáticas son rutas configuradas manualmente por el administrador de red. Son adecuadas para redes pequeñas y simples donde los cambios de topología son poco frecuentes.

#### Ventajas de las Rutas Estáticas

- **Simplicidad:** Fácil de configurar y mantener en redes pequeñas.
- **Predecibilidad:** El tráfico sigue rutas predefinidas.
- **Bajo uso de recursos:** No requiere procesamiento adicional como el enrutamiento dinámico.

#### Desventajas de las Rutas Estáticas

- **Escalabilidad:** Difícil de mantener en redes grandes.
- **Falta de adaptabilidad:** No se ajusta automáticamente a cambios en la red.
- **Mayor mantenimiento:** Requiere actualizaciones manuales ante cualquier cambio en la topología.

#### Configuración de Rutas Estáticas en Cisco Packet Tracer

##### Ejemplo de Configuración

Supongamos que tenemos dos routers, `R1` y `R2`, conectados por una conexión serial. `R1` tiene una red local `192.168.1.0/24` y `R2` tiene una red local `192.168.2.0/24`.

1. **Configurar las interfaces:**

    ```plaintext
    R1:
    interface Serial0/0/0
    ip address 172.16.0.1 255.255.255.252
    no shutdown

    interface FastEthernet0/0
    ip address 192.168.1.1 255.255.255.0
    no shutdown

    R2:
    interface Serial0/0/0
    ip address 172.16.0.2 255.255.255.252
    no shutdown

    interface FastEthernet0/0
    ip address 192.168.2.1 255.255.255.0
    no shutdown
    ```

2. **Configurar rutas estáticas:**

    ```plaintext
    R1:
    ip route 192.168.2.0 255.255.255.0 172.16.0.2

    R2:
    ip route 192.168.1.0 255.255.255.0 172.16.0.1
    ```

3. **Verificación:**

    ```plaintext
    R1#ping 192.168.2.1
    R2#ping 192.168.1.1
    ```

### Rutas Dinámicas

Las rutas dinámicas son gestionadas automáticamente por protocolos de enrutamiento dinámico. Estos protocolos permiten a los routers intercambiar información de enrutamiento y adaptarse a los cambios en la red.

#### Protocolos de Enrutamiento Dinámico

- **RIP (Routing Information Protocol):**
  - Utiliza la métrica de "saltos" para determinar la mejor ruta.
  - Es adecuado para redes pequeñas.

- **OSPF (Open Shortest Path First):**
  - Utiliza el algoritmo de Dijkstra para calcular la ruta más corta.
  - Escalable y adecuado para redes grandes y complejas.

- **EIGRP (Enhanced Interior Gateway Routing Protocol):**
  - Propietario de Cisco, combina las ventajas de RIP y OSPF.
  - Utiliza múltiples métricas para determinar la mejor ruta.

#### Ventajas de las Rutas Dinámicas

- **Adaptabilidad:** Se ajusta automáticamente a cambios en la topología de la red.
- **Escalabilidad:** Adecuado para redes grandes.
- **Reducción de mantenimiento:** Menos intervención manual.

#### Desventajas de las Rutas Dinámicas

- **Complejidad:** Requiere configuración y comprensión más detallada.
- **Consumo de recursos:** Utiliza más recursos de CPU y memoria.

#### Configuración de Rutas Dinámicas en Cisco Packet Tracer

##### Ejemplo con RIP

1. **Configurar las interfaces:**

    ```plaintext
    R1:
    interface Serial0/0/0
    ip address 172.16.0.1 255.255.255.252
    no shutdown

    interface FastEthernet0/0
    ip address 192.168.1.1 255.255.255.0
    no shutdown

    R2:
    interface Serial0/0/0
    ip address 172.16.0.2 255.255.255.252
    no shutdown

    interface FastEthernet0/0
    ip address 192.168.2.1 255.255.255.0
    no shutdown
    ```

2. **Configurar RIP:**

    ```plaintext
    R1:
    router rip
    version 2
    network 192.168.1.0
    network 172.16.0.0

    R2:
    router rip
    version 2
    network 192.168.2.0
    network 172.16.0.0
    ```

3. **Verificación:**

    ```plaintext
    R1#show ip route
    R2#show ip route
    ```

##### Ejemplo con OSPF

1. **Configurar las interfaces:**

    (Igual que en los ejemplos anteriores)

2. **Configurar OSPF:**

    ```plaintext
    R1:
    router ospf 1
    network 192.168.1.0 0.0.0.255 area 0
    network 172.16.0.0 0.0.0.3 area 0

    R2:
    router ospf 1
    network 192.168.2.0 0.0.0.255 area 0
    network 172.16.0.0 0.0.0.3 area 0
    ```

3. **Verificación:**

    ```plaintext
    R1#show ip ospf neighbor
    R1#show ip route
    R2#show ip ospf neighbor
    R2#show ip route
    ```

## Conclusión

El enrutamiento es una parte fundamental en la gestión de redes. Las rutas estáticas son simples y predecibles, pero requieren mantenimiento manual. Las rutas dinámicas se adaptan automáticamente a los cambios en la red y son más adecuadas para redes grandes y complejas. Cisco Packet Tracer es una herramienta excelente para practicar y visualizar las configuraciones de enrutamiento.


# Referencia

- [Cómo configurar un router Cisco](https://ccnadesdecero.es/como-configurar-router-cisco/)
- [Introducción a la configuración de routers CISCO](https://fi.ort.edu.uy/innovaportal/file/98965/1/configuracion-routers-cisco-matturro.pdf)
- [Configuración básica de routers](https://eclassvirtual.com/configuracion-basica-de-routers/)
- [Configuración general de un router cisco utilizando packet tracer](https://neuromarketingytecnologia.com/configuracion-genera/)


