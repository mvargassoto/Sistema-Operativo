# Sistema Operativo
**Si querés saber en detalle de qué trata ingresá** [acá](https://github.com/mvargassoto/Sistema-Operativo/blob/main/Explicacion-detallada.md)

Este proyecto consiste en desarrollar una solución distribuida para simular un sistema operativo (SO) funcional, permitiendo la planificación de procesos, la administración de memoria y la gestión de un sistema de archivos. El sistema se implementa en lenguaje C sobre una plataforma Linux, utilizando técnicas de programación de sistemas como multihilo, archivos de configuración y logs.

### Arquitectura del Sistema
El SO se divide en cuatro módulos principales que se comunican entre sí para simular el comportamiento de una computadora real:
 - **Kernel**: Actúa como el administrador central del sistema. Se encarga de la planificación de procesos utilizando un diagrama de 5 estados (NEW, READY, EXEC, EXIT, BLOCKED) y algoritmos como FIFO, Round Robin (RR) y Virtual Round Robin (VRR). También gestiona los recursos del sistema (WAIT/SIGNAL) y las peticiones de entrada/salida.
 - **CPU**: Simula el ciclo de instrucción (Fetch, Decode, Execute y Check Interrupt). Incluye registros de propósito general (como AX, BX, PC, entre otros) y una MMU para traducir direcciones lógicas a físicas mediante un esquema de paginación. Para optimizar estas traducciones, implementa una TLB con algoritmos de reemplazo FIFO o LRU.
 - **Memoria**: Administra el espacio de usuario de forma contigua y bajo un esquema de paginación simple. Responde a peticiones de lectura, escritura y ajuste de tamaño (resize) de los procesos, además de cargar las instrucciones desde archivos de pseudocódigo.
 - **Interfaz de I/O**: Representa los dispositivos periféricos que se conectan dinámicamente al Kernel. Existen cuatro tipos: Genéricas (solo retardo), STDIN (lectura de teclado), STDOUT (salida por pantalla) y DialFS (sistema de archivos).

### Funcionalidades y Alcance Técnico
El sistema permite a un programador interactuar con el SO a través de una consola en el Kernel, desde donde puede iniciar scripts, finalizar procesos o listar estados.
 - Gestión de Procesos: Cada proceso posee un PCB con su identificador (PID), contador de programa y registros. El Kernel coordina la multiprogramación y el desalojo de procesos por interrupciones o fin de quantum.
 - Sistema de Archivos (DialFS): Implementa una asignación contigua de bloques. Utiliza un archivo de bloques (bloques.dat), un bitmap para gestionar el espacio libre (bitmap.dat) y archivos de metadata para cada archivo creado. Soporta operaciones de creación, eliminación y compactación cuando el espacio libre no es contiguo.


## Instalacion (Linux)
Primero descargar e instalar [so-commons-library]:
- descargar el repositorio
- ejecutar:
```
make debug
make install
```
Instalar dependencias básicas
```
apt install build-essential
apt install libreadline-dev
```
Configurar IPs y puertos
- En cada modulo vas a tener que indicar a que IP se va a conenctar el mismo y en que puerto, procura asegurar la consistencia para que haya una conexión

# Sistemas Operativos UTN FRBA
En la materia se abordan los siguientes temas:
1. **Arquitectura y Fundamentos de Hardware**
    - Ciclo de Instrucción: Se estudia cómo la CPU busca, decodifica y ejecuta instrucciones de forma cíclica.
    - Registros: Uso de registros específicos como el PC (puntero de instrucción), el IR (instrucción actual) y el PSW (estado del procesador).
    - Interrupciones: Mecanismos para que el hardware o el software soliciten atención inmediata del procesador.

2. **El Sistema Operativo como Interfaz**
    - Modos de Ejecución: Diferencia entre el Modo Usuario (restringido para aplicaciones) y Modo Kernel (privilegiado para el SO) para proteger el hardware.
    - Llamadas al Sistema (Syscalls): Son las funciones que permiten a los programas pedirle servicios directamente al Kernel.
    - Estructura del SO: Modelos de diseño como sistemas monohilo, multihilo y arquitecturas de micro-núcleo.

3. **Gestión de Procesos e Hilos**
    - Procesos: Un programa en ejecución que incluye su propio espacio de memoria dividido en Código, Datos, Stack y Heap.
    - PCB (Bloque de Control de Proceso): Estructura de datos donde el SO guarda toda la información necesaria para administrar un proceso.
    - Planificación (Scheduling): Algoritmos (como FIFO, Round Robin o Prioridades) que deciden qué proceso usa la CPU en cada momento.

4. **Administración de Memoria**
    - Memoria Virtual: Técnica que permite ejecutar procesos más grandes que la RAM física disponible.
    - Paginación y Segmentación: Métodos para dividir y organizar la memoria de manera eficiente para evitar la fragmentación.
    - Algoritmos de Reemplazo: Estrategias para decidir qué página quitar de la RAM cuando está llena (ej: FIFO, Reloj, LRU).

5. **Sistemas de Archivos y Entrada/Salida**
    - Archivos y Directorios: Cómo se organiza la información lógicamente en el disco.
    - Implementaciones: Comparativa entre sistemas como NTFS (Windows) y el uso de i-nodos en Linux.
    - RAID: Agrupamiento de discos rígidos para mejorar la velocidad o la seguridad de los datos (Niveles 0, 1, 5).
    - Gestión de I/O: Técnicas de comunicación con periféricos, como polling o acceso directo a memoria.

6. **Seguridad y Administración Práctica**
    - Amenazas y Protección: Tipos de software malicioso (virus, intrusos) y cómo el SO protege los recursos.
    - Shell Scripting: Automatización de tareas en Linux mediante comandos y estructuras de control (if, for, while).
    - Usuarios y Permisos: Gestión de accesos y grupos para mantener la integridad del sistema.

[so-commons-library]: https://github.com/mvargassoto/so-commons-library
