Simulacion del funcionamiento de un sistema operativo. Parte practica de la asignatura "sistemas operativos"  de la UTN FRBA 1C 2024.
Este protecto esta desarrollado en C y esta dividido en 5 actores principales:
1. KERNEL
2. CPU
3. MEMORIA
4. I/O
5. FILE SYSTEM

El sistema operativo presenta las siguiente caracteristicas:
* Diagrama de 5 estaods : New - Ready - Exec - Blocked - Exit
* Algoritmos del planificador de corto plazo: FIFO - Round Robin - Virtul Round Robin
* Consola interactiva en Kernel: EJECUTAR_SCRIPT -INICIAR_PROCESO -FINALIZAR_PROCESO , etc.
* Ciclo de instruccion : Fetch -Decode -Execute
* Instrucciones en codigo Asembler y registro de CPU : SET - MOV_IN - MOV_OUT - SUM- SUB -WAIT - SIGNAL ,AX , BX , EAX, EBX , etc..
* Desarrollo de MMU
* Implementacion de TLB con algoritmos : FIFO - LRU
* Esquema de paginacion simple (contigua) : tabla de paginas 
* Desarrollo de File System: Creacion de Metadata por archivo regular - tabla de procesos abiertos - archivo para el contenido de los archivos creados (bloque.dat) - creacion de bitmap- compactacion de archivos
* Asignacion de bloques contiguo 
* Desarrollo de interfaces input y output
* Desarollo de interfaz generica : retardo de tiempo unicamente

# Sistemas Operativos UTN FRBA

## Links e info util de Práctica
ENUNCIADO: https://docs.google.com/document/d/1-AqFTroovEMcA1BfC2rriB5jsLE6SUa4mbcAox1rPec/edit
### Ellos
https://github.com/sisoputnfrba

https://docs.utnso.com.ar/guias/

## Sobre configs
### tp-scaffold

Esta es una plantilla de proyecto diseñada para generar un TP de Sistemas
Operativos de la UTN FRBA.

### Dependencias

Para poder compilar y ejecutar el proyecto, es necesario tener instalada la
biblioteca [so-commons-library] de la cátedra:

```bash
git clone https://github.com/sisoputnfrba/so-commons-library
cd so-commons-library
make debug
make install
```

### Compilación

Cada módulo del proyecto se compila de forma independiente a través de un
archivo `makefile`. Para compilar un módulo, es necesario ejecutar el comando
`make` desde la carpeta correspondiente.

El ejecutable resultante se guardará en la carpeta `bin` del módulo.

### Importar desde Visual Studio Code

Para importar el workspace, debemos abrir el archivo `tp.code-workspace` desde
la interfaz o ejecutando el siguiente comando desde la carpeta raíz del
repositorio:

```bash
code tp.code-workspace
```

[so-commons-library]: https://github.com/mvargassoto/so-commons-library
