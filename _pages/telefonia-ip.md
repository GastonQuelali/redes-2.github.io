---
layout: page
title: "Telefonía IP"
permalink: /telefonia-ip/
---

# Unidad 8: Telefonía IP

## Introducción a la Telefonía IP

La telefonía IP (VoIP) es una tecnología que permite la transmisión de voz y multimedia a través de redes IP, como Internet o redes privadas. Esta tecnología convierte la señal de voz en datos digitales que pueden ser transmitidos mediante protocolos IP.

#### Conceptos Clave

- **VoIP (Voice over IP):** Tecnología que permite realizar llamadas de voz a través de redes IP.
- **Codec:** Dispositivo o programa que comprime y descomprime datos digitales, específicamente para la transmisión de voz.
- **QoS (Quality of Service):** Mecanismos para asegurar que las llamadas VoIP tengan prioridad en la red y mantengan una calidad aceptable.

### Práctica

#### Caso de Estudio 1: Implementación de VoIP en una Pequeña Empresa

**Escenario:**
Una pequeña empresa desea implementar VoIP para reducir costos y mejorar la flexibilidad en las comunicaciones internas.

**Configuración Básica:**
1. **Configurar teléfonos IP en la red de la empresa.**
2. **Implementar un servidor VoIP para gestionar las llamadas internas.**
3. **Configurar QoS para priorizar el tráfico de voz.**

## La Voz en las Redes IP

La transmisión de voz a través de redes IP requiere convertir la señal de voz en paquetes de datos. Estos paquetes deben ser entregados de manera eficiente para mantener la calidad de la llamada.

#### Conceptos Clave

- **SIP (Session Initiation Protocol):** Protocolo utilizado para iniciar, mantener y finalizar sesiones de comunicación multimedia.
- **RTP (Real-time Transport Protocol):** Protocolo utilizado para la entrega de audio y video en tiempo real.
- **Jitter:** Variación en el retraso de la entrega de paquetes de datos de voz, que puede afectar la calidad de la llamada.

### Práctica

#### Caso de Estudio 2: Reducción del Jitter en una Red VoIP

**Escenario:**
Una empresa está experimentando problemas de calidad de voz debido al jitter.

**Configuración Básica:**
1. **Implementar mecanismos de QoS para priorizar el tráfico de voz.**
2. **Configurar buffers de jitter en los teléfonos IP y routers para suavizar la variabilidad en la entrega de paquetes.**

## Telefonía IP


La telefonía IP integra la tecnología VoIP con la infraestructura de telecomunicaciones existente, permitiendo realizar y recibir llamadas telefónicas tradicionales a través de una red IP.

#### Conceptos Clave

- **Gateway VoIP:** Dispositivo que conecta la red VoIP con la red telefónica tradicional (PSTN).
- **PBX IP (Private Branch Exchange):** Central telefónica privada que utiliza la tecnología IP para gestionar las llamadas dentro de una organización.

### Práctica

#### Configuración de un Gateway VoIP

**Paso a Paso:**

1. **Configurar el Gateway VoIP:**
    ```plaintext
    enable
    configure terminal
    voice service voip
    allow-connections h323 to h323
    allow-connections h323 to sip
    allow-connections sip to h323
    allow-connections sip to sip
    exit
    dial-peer voice 1 voip
    destination-pattern 9T
    session target ipv4:192.168.1.1
    codec g711ulaw
    exit
    ```

2. **Configurar el PBX IP:**
    - Configurar extensiones internas y rutas de salida en el PBX IP.
    - Integrar el PBX IP con el Gateway VoIP para enrutar llamadas externas.

## Unificación

La unificación de comunicaciones integra diversas tecnologías de comunicación (voz, video, mensajería instantánea, correo electrónico) en una única plataforma, mejorando la eficiencia y la colaboración en la organización.

#### Conceptos Clave

- **UC (Unified Communications):** Integración de múltiples servicios de comunicación en una plataforma.
- **Presencia:** Información sobre la disponibilidad y estado de los usuarios en tiempo real.

### Práctica

#### Caso de Estudio 3: Implementación de Comunicaciones Unificadas

**Escenario:**
Una empresa multinacional desea unificar sus comunicaciones para mejorar la colaboración entre equipos distribuidos geográficamente.

**Configuración Básica:**
1. **Implementar una solución de comunicaciones unificadas que incluya voz, video y mensajería instantánea.**
2. **Configurar la integración con el correo electrónico y las herramientas de colaboración existentes.**

## Cisco IP Conmutador

El Cisco IP Conmutador (Switch) es un dispositivo que permite gestionar y enrutar el tráfico de voz y datos en una red IP, optimizando el rendimiento y la calidad del servicio.

#### Conceptos Clave

- **VLAN (Virtual LAN):** Segmentación lógica de la red para separar el tráfico de voz y datos.
- **PoE (Power over Ethernet):** Tecnología que permite alimentar dispositivos como teléfonos IP a través del cable Ethernet.

### Práctica

#### Configuración de VLANs para VoIP en un Cisco Switch

**Paso a Paso:**

1. **Crear VLANs para Voz y Datos:**
    ```plaintext
    enable
    configure terminal
    vlan 10
    name VOICE
    vlan 20
    name DATA
    exit
    ```

2. **Configurar Puertos para Voz y Datos:**
    ```plaintext
    interface range fa0/1 - 24
    switchport mode access
    switchport access vlan 20
    switchport voice vlan 10
    exit
    ```

3. **Configurar QoS para Priorizar el Tráfico de Voz:**
    ```plaintext
    mls qos
    interface range fa0/1 - 24
    mls qos trust cos
    exit
    ```

## Conclusión

La implementación de Telefonía IP y la integración de comunicaciones unificadas son fundamentales para modernizar las infraestructuras de telecomunicaciones en las organizaciones. La comprensión de los conceptos de VoIP, la configuración de dispositivos y la implementación de QoS son esenciales para garantizar la calidad y eficiencia en las comunicaciones. Cisco Packet Tracer es una herramienta excelente para simular y practicar estas configuraciones, proporcionando un entorno seguro y controlado para aprender y experimentar.

---

### Recursos Adicionales

- [Introduction to VoIP](https://en.wikipedia.org/wiki/Voice_over_IP)
- [Quality of Service (QoS) Basics](https://www.cisco.com/c/en/us/products/quality-of-service-qos/index.html)
