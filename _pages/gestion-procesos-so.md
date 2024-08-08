---
layout: page
title: "Conceptos Básicos"
permalink: /gestion-procesos-so/
---

### UNIDAD II: Gestión de Procesos

#### 2.1. Procesos

Un proceso es un programa en ejecución que incluye el código del programa, su estado actual, y toda la información necesaria para su ejecución. Los sistemas operativos modernos permiten la ejecución de múltiples procesos simultáneamente mediante técnicas de multitarea.

- **Estados de un Proceso:**
  - **Nuevo:** El proceso está siendo creado.
  - **Ejecutando:** El proceso está siendo ejecutado en la CPU.
  - **Bloqueado:** El proceso está esperando un evento, como la finalización de una operación de E/S.
  - **Listo:** El proceso está preparado para ejecutarse tan pronto como la CPU esté disponible.
  - **Terminado:** El proceso ha completado su ejecución.

- **Control de Procesos:**
  - **PCB (Process Control Block):** Es una estructura de datos que contiene información sobre el proceso, como el estado del proceso, el contador de programa, los registros de la CPU, y la información de memoria.

#### 2.2. Procesos livianos, hilos, hebras

- **Hilos (Threads):**
  - Un hilo es la unidad básica de utilización de la CPU. Los hilos comparten el mismo espacio de direcciones y recursos del proceso padre, pero se ejecutan de manera independiente.
  - **Hilos del Kernel:** Son gestionados directamente por el sistema operativo.
  - **Hilos del Usuario:** Son gestionados por una biblioteca de hilos a nivel de usuario.

- **Diferencias entre Procesos y Hilos:**
  - Los procesos tienen sus propios espacios de direcciones separados, mientras que los hilos comparten el mismo espacio de direcciones.
  - La creación y gestión de hilos es más eficiente que la de procesos, debido a la menor sobrecarga de contexto.

#### 2.3. Planificación de procesos

La planificación de procesos es una de las funciones clave del sistema operativo, que decide qué procesos deben ejecutarse y en qué orden.

- **Objetivos de la Planificación:**
  - Maximizar el uso de la CPU.
  - Minimizar el tiempo de respuesta.
  - Maximizar el rendimiento del sistema.
  - Garantizar la equidad entre los procesos.

- **Tipos de Planificación:**
  - **Planificación a Largo Plazo:** Decide qué procesos se admiten en el sistema.
  - **Planificación a Medio Plazo:** Gestiona la cantidad de procesos en memoria principal.
  - **Planificación a Corto Plazo:** Decide qué proceso debe ejecutarse a continuación.

#### 2.4. Algoritmos de planificación

- **FIFO (First In, First Out):** Los procesos se atienden en el orden en que llegan.
- **SJF (Shortest Job First):** El proceso con el menor tiempo de ejecución se atiende primero.
- **RR (Round Robin):** Los procesos se atienden en ciclos de tiempo fijos.
- **Prioridad:** Los procesos se atienden según su prioridad.

- **Algoritmos Avanzados:**
  - **Multilevel Queue Scheduling:** Los procesos se dividen en diferentes colas basadas en sus características.
  - **Multilevel Feedback Queue Scheduling:** Similar a multilevel queue, pero permite mover procesos entre colas basadas en su comportamiento y necesidades.

#### 2.5. Planificación de procesos en ambientes multiprocesador

- **Planificación Asimétrica:** Un único procesador toma todas las decisiones de planificación.
- **Planificación Simétrica (SMP):** Cada procesador planifica sus propios procesos.
- **Algoritmos para Ambientes Multiprocesador:**
  - **Balanceo de Carga:** Distribuye equitativamente los procesos entre los procesadores.
  - **Afinidad de Procesadores:** Trata de mantener los procesos en el mismo procesador para reducir la sobrecarga de la caché.

#### 2.6. Planificación en Windows y Linux

- **Planificación en Windows:**
  - Utiliza un algoritmo de planificación basado en prioridades, con 32 niveles de prioridad.
  - Emplea un esquema de cola de multilevel feedback.
  - Ofrece soporte para hilos y procesos en tiempo real.

- **Planificación en Linux:**
  - Usa el algoritmo Completely Fair Scheduler (CFS), que trata de proporcionar un reparto equitativo del tiempo de CPU entre todos los procesos.
  - Implementa prioridades y tiempos compartidos, adaptándose a las necesidades del sistema.
  - Ofrece diferentes clases de planificación, como tiempo compartido y tiempo real, para diferentes tipos de procesos.

Este contenido proporciona una visión integral de la gestión de procesos, abordando desde los conceptos básicos hasta la implementación en sistemas operativos específicos como Windows y Linux.
