Simulacion del funcionamiento de un sistema operativo. Parte practica de la asignatura "sistemas operativos"  de la UTN FRBA 1C 2024.
Este protecto esta desarrollado en C y esta dividido principalmente en 4 modulos:
1- Kernel
2- CPU
3- Memoria 
4- Entrada salida

Ademas, se creo otro modulo extra para aquellas funciones y logica que repiten todos los modulos. 

ENUNCIADO: https://docs.google.com/document/d/1-AqFTroovEMcA1BfC2rriB5jsLE6SUa4mbcAox1rPec/edit

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
  
# Sobre configs
# tp-scaffold

Esta es una plantilla de proyecto diseñada para generar un TP de Sistemas
Operativos de la UTN FRBA.

## Dependencias

Para poder compilar y ejecutar el proyecto, es necesario tener instalada la
biblioteca [so-commons-library] de la cátedra:

```bash
git clone https://github.com/sisoputnfrba/so-commons-library
cd so-commons-library
make debug
make install
```

## Compilación

Cada módulo del proyecto se compila de forma independiente a través de un
archivo `makefile`. Para compilar un módulo, es necesario ejecutar el comando
`make` desde la carpeta correspondiente.

El ejecutable resultante se guardará en la carpeta `bin` del módulo.

## Importar desde Visual Studio Code

Para importar el workspace, debemos abrir el archivo `tp.code-workspace` desde
la interfaz o ejecutando el siguiente comando desde la carpeta raíz del
repositorio:

```bash
code tp.code-workspace
```

## Checkpoint

Para cada checkpoint de control obligatorio, se debe crear un tag en el
repositorio con el siguiente formato:

```
checkpoint-{número}
```

Donde `{número}` es el número del checkpoint.

Para crear un tag y subirlo al repositorio, podemos utilizar los siguientes
comandos:

```bash
git tag -a checkpoint-{número} -m "Checkpoint {número}"
git push origin checkpoint-{número}
```

Asegúrense de que el código compila y cumple con los requisitos del checkpoint
antes de subir el tag.

## Entrega

Para desplegar el proyecto en una máquina Ubuntu Server, podemos utilizar el
script [so-deploy] de la cátedra:

```bash
git clone https://github.com/sisoputnfrba/so-deploy.git
cd so-deploy
./deploy.sh -r=release -p=utils -p=kernel -p=cpu -p=memoria -p=entradasalida "tp-{año}-{cuatri}-{grupo}"
```

El mismo se encargará de instalar las Commons, clonar el repositorio del grupo
y compilar el proyecto en la máquina remota.

Ante cualquier duda, podés consultar la documentación en el repositorio de
[so-deploy], o utilizar el comando `./deploy.sh -h`.

[so-commons-library]: https://github.com/sisoputnfrba/so-commons-library
