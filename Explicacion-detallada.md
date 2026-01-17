# Sistema Operativo

El mismo consta de **4 módulos**
- **Kernel**
- **Cpu**
- **Memoria**
- **I/O**: en este ultimo se incluye la logica de File System

## Modulo Kernel
Este modulo es el orquestador, es quien dirige el funcionamiento de los 3 modulos restantes. En el encontramos responsabilidades como:
- Mostrar consola de control
  - **Ejecutar script**: se le podra pasar un archivo txt (por path) y el mismo ejecutara cada [instruccion] listada
  - **Iniciar proceso**: se podra iniciar un proceso que tendra sus intrucciones contenidas en el [File System del modulo Memoria]
  - **Finalizar proceso**: finaliza el proceso que contenga el PID señalado
  - **Detener planificacion**: pausa la planificación, ningun proceso cambiará de estado
  - **Iniciar planificacion**: reanuda la planificación
  - **Multiprogramacion**: permite tener a mas de un proceso en EXEC (medido en grados)
  - **Proceso estado**: lista todos los estados con lo procesos que lo tengan
- Gestionar procesos
  - Identificarlos:
      - mediante **PCB**
        - PID
        - Program Counter
        - Quantum
        - Registros de la CPU
  - Planificarlos: 
      - 5 estados: NEW - READY - BLOCKED - EXEC - EXIT
      - **Largo plazo**: INICIARLOS, FINALIZARLOS
      - **Corto plazo**: PAUSARLOS, EJECUTARLOS
- **Gestionar recursos**:
      Sistema de instancias, cuando se crea un recurso se le asigna una cantidad de instancias, un proceso puede tener todas las instancias de recursos que desee y por este motivo tener cuidado con los Deadlock's
- **Gestionar [interafaces I/O](#modulo-interfaces)**:
      Similar a los recursos, los modulos I/O que existan pueden ser solicitados por cualquier proceso y en caso de estar siendo utilizados el nuevo proceso solicitante queda bloqueado esperando la liberacion de la I/O

### Planificadores
**Corto Plazo**
Los posibles planificadores son:
- **FIFO**: primer proceso que entra a la lista READY es el primero que entra en la CPU, no hay tiempo limite para estar procesandose
- **Round Robin**: los procesos entran por al igual que en FIFO en la CPU pero con un limite de tiempo para procesarse (quantum)
- **Virtual Round Robin**: igual que RR pero ahora existe una cola prioritaria READY+ de la cual se toman primero a los procesos que se encuentran en ella, a esta solo acceden los procesos que salen de CPU por llamada a I/O

### Logs que se registran
- Creacion de Proceso
- Fin de Proceso
- Cambio de Estado
- Motivo de Bloqueo
- Fin de Quantum
- Ingreso a READY

### Archivo de configuración
- **PUERTO_CPU_DISPATCH**= puerto de escucha para recibir y desalojar procesos
- **PUERTO_CPU_INTERRUPT**= puerto de escucha para interrumpir procesos
- **MULTIPROGRAMACION_MAX**= grado de multiprogramacion 
- **PUERTO_MEM**= puerto de escucha para modulo Memoria
- **PUERTO_ESCUCHA**= puerto donde Kernel escucha peticiones 
- **INSTANCIAS_RECURSOS**= [n1, n2, ... , nn]
- **RECURSOS**= [nombreRecurso1, nombreRecurso2, ... ,nombreRecursoN]
- **QUANTUM**= tiempo maximo que tendra cada proceso en la CPU
- **IP_CPU**= IP de la maquina en donde se encuentre CPU
- **ALGORITMO**= algoritmo de planificacion de corto plazo (FIFO,RR,VRR)
- **IP_MEMORIA**= IP de la maquina en donde se encuentre MEMORIA  
- **IP**= IP de la maquina en donde se encuenntra KERNEL
- **RUTA_LOCAL**=/home/-path hasta la raiz del repo-/kernel

## Modulo Interfaces 
Las interfaces son una simulacion de las que conocemos en la vida real: teclado, monitor, mouse, impresora... 

En nuestro caso vamos a simular puntalmente dos: TECLADO y MONITOR. Como dijimos antes, estas interfaces van a recibir peticiones de procesos, y la politica de uso va a ser: si esta ocupada con un proceso A, entonces el proceso solicitante B debe bloquearse hasta que la I/O le avise a Kernel que esta libre. La cantidad de interfaces NO tiene limite.

### Archivo de configuración
Hay de momento 4 posibles modulos I/O

**I/O GENERICA SLEEP**

Esta interfaz lo unico que hace es "dormir" al proceso unna cantidad de tiempo (TIEMPO_UNIDAD_TRABAJO), entonces su unica instruccion posible es:
- IO_GEN_SLEEP


Al leer el archivo de configuración solo le van a importar las propiedades de:
- TIPO_INTERFAZ= GENERICA
- TIEMPO_UNIDAD_TRABAJO= cuanto tiempo en ms se va a quedar el proceso esperando
- IP_KERNEL= IP de la maquina donde se encuentre KERNEL
- PUERTO_KERNEL= puerto de escucha que tiene el KERNEL, es por donde se le va a notificar que esta libre (u ocupada)

**STDIN**

Esta interfaz no tiene unidad de trabajo ya que lo que hace es esperar que el usuario ingrese algo por teclado. Lo ingresado sera guardado en la direccion fisica indicada en la peticion de Kernel. La unica instruccion posible es:
- IO_STDIN_READ


Al leer el archivo de configuración solo le van a importar las propiedades de:
- TIPO_INTERFAZ= STDIN
- IP_KERNEL= IP de la maquina donde se encuentre KERNEL
- PUERTO_KERNEL= puerto de escucha que tiene el KERNEL, es por donde se le va a notificar que esta libre (u ocupada)
- IP_MEMORIA= IP de la maquina donde se encuentre MEMORIA
- PUERTO_MEMORIA= puerto de escucha que tiene el KERNEL, es por donde se le va a notificar que esta libre (u ocupada)

**STDOUT**

Las interfaces STDOUT se conectan a memoria para leer el valor que se encuentra en la o las direcciones físicas pedidas y mostrar el resultado por pantalla. La unica instruccion posible es:
- IO_STDOUT_WRITE

- TIPO_INTERFAZ= STDOUT
- IP_KERNEL= IP de la maquina donde se encuentre KERNEL
- PUERTO_KERNEL= puerto de escucha que tiene el KERNEL, es por donde se le va a notificar que esta libre (u ocupada)
- IP_MEMORIA= IP de la maquina donde se encuentre MEMORIA
- PUERTO_MEMORIA= puerto de escucha que tiene el KERNEL, es por donde se le va a notificar que esta libre (u ocupada)


**DialFS**
## Modulo CPU

