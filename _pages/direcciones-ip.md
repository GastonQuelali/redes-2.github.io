---
layout: page
title: "Direcciones IP"
permalink: /direcciones-ip/
---

## Tabla de Contenidos
- [Tabla de Contenidos](#tabla-de-contenidos)
- [Clases de Direcciones IP](#clases-de-direcciones-ip)
  - [Clase A](#clase-a)
  - [Clase B](#clase-b)
  - [Clase C](#clase-c)
  - [Clase D (Multidifusión)](#clase-d-multidifusión)
  - [Clase E (Investigación)](#clase-e-investigación)
- [Nombre de red y dirección IP de difusión (broadcast)](#nombre-de-red-y-dirección-ip-de-difusión-broadcast)
- [Direcciones IP sin clase (CIDR)](#direcciones-ip-sin-clase-cidr)

## Clases de Direcciones IP

### Clase A
- **Bits de red:** Primeros 8 bits
- **Bits de hosts:** Últimos 24 bits
- **Empiezan por:** "0" en binario
- **Rango decimal:** 1 a 127

### Clase B
- **Bits de red:** Primeros 16 bits
- **Bits de hosts:** Últimos 16 bits
- **Empiezan por:** "10" en binario
- **Rango decimal:** 128 a 191

### Clase C
- **Bits de red:** Primeros 24 bits
- **Bits de hosts:** Últimos 8 bits
- **Empiezan por:** "110" en binario
- **Rango decimal:** 192 a 223

### Clase D (Multidifusión)
- **Empiezan por:** "1110"

### Clase E (Investigación)
- **Empiezan por:** "1111"

## Nombre de red y dirección IP de difusión (broadcast)

Supón que tenemos la típica red `192.168.0.0` (clase C) con máscara `255.255.255.0`. Esto es en binario: `11111111.11111111.11111111.00000000`, por tanto, tenemos 24 bits para red y 8 bits para hosts (equipos conectados). Así, el número de equipos conectados será:

$$
Nº\ hosts = 2^n
$$

$$
2^8 = 256 \text{ hosts}
$$

Pues no, incorrecto. Tenemos que tener en cuenta que en redes IP:

- La primera dirección IP (toda la parte de host a ceros), en este caso la `.00000000` (0 en decimal) se reserva para referirse a toda la red, y se le llama nombre de red **(Segmentos)**.
- La última dirección IP (toda la parte de host a unos), en este caso la `.11111111` (255 en decimal) se reserva para dirección de difusión (paquetes que se envían a todos los hosts de la red), y se le llama dirección IP de difusión **(Broadcast)**.

Aplicando este descarte, la fórmula correcta sería:

$$
Nº\ hosts = 2^n - 2
$$

Donde `n` es el número de bits designados a hosts.

En el primer ejercicio, el número de hosts posibles sería `2^8 - 2 = 254`, así que para la red `192.168.0.0` con máscara `255.255.255.0`:

- `192.168.0.0` es el nombre de red.
- Los hosts ocuparían las IPs desde `192.168.0.1` hasta `192.168.0.254`.
- `192.168.0.255` sería la dirección broadcast. Cuando un host envíe un paquete a esa dirección, lo recibirán todos excepto él (porque es el remitente).

## Direcciones IP sin clase (CIDR)

En el principio de los tiempos:

- Una red clase A tenía siempre una máscara `255.0.0.0` (/8) (16 millones de hosts posibles).
- Una red clase B tenía siempre una máscara `255.255.0.0` (/16) (65532 hosts posibles).
- Una red clase C tenía siempre una máscara `255.255.255.0` (/24) (254 hosts posibles).

Pero luego se diseñó el enrutamiento sin clase (CIDR) (cuidado con el nombre que es falsillo). Casi siempre se usa el sistema sin clase:

- Una red clase A tiene una máscara `255.0.0.0` o superior (≥ /8) (como máximo 16M de hosts posibles).
- Una red clase B tiene una máscara `255.255.0.0` o superior (≥ /16) (como máximo 65532 hosts posibles).
- Una red clase C tiene una máscara `255.255.255.0` o superior (≥ /24) (como máximo 65532 hosts posibles).

Así, la red `192.168.0.0`, que es una red clase C, cuando se usa CIDR puede tener una máscara `/25`, `/26`…:

- Cuando tiene la máscara `255.255.255.0` (`11111111.11111111.11111111.00000000`) (/24) soporta hasta 254 hosts.
- Cuando tiene la máscara `255.255.255.128` (`11111111.11111111.11111111.10000000`) (/25) soporta hasta 126 hosts.
- Cuando tiene la máscara `255.255.255.192` (`11111111.11111111.11111111.11000000`) (/26) soporta hasta 62 hosts.
- Cuando tiene la máscara `255.255.255.224` (`11111111.11111111.11111111.11100000`) (/27) soporta hasta 30 hosts.
- Cuando tiene la máscara `255.255.255.240` (`11111111.11111111.11111111.11110000`) (/28) soporta hasta 14 hosts.
- Cuando tiene la máscara `255.255.255.248` (`11111111.11111111.11111111.11111000`) (/29) soporta hasta 6 hosts.
- Cuando tiene la máscara `255.255.255.252` (`11111111.11111111.11111111.11111100`) (/30) soporta hasta 2 hosts.

A la máscara de subred en notación “/24“, “/8”… se le llama prefijo CIDR.
