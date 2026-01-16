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



### Modulo CPU
linnea

linnea

linnea


linnea

linnea

linnea

linnea


linnea

linnea

linnea


linnea

linnea

linnea


linnea
linnea
linnea
linnea
linnea
linnea
linnea
linnea
linnea
linnealinnea
linnea
linnea
linnea
linnea
linnea
linnea
### Modulo Interfaces 
