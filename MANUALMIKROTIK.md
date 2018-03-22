# Manual Básico MIKROTik

Información Básica
¿Qué es Router OS?

Es el sistema operativo del hardware MikroTik RoaterBOARD, tiene las siguientes características:

•   Router
•   Servidor DHCP
•   Firewall
•   VPN
•   Wireless
•   Calidad de Servicio (QoS)
•   VLAN
•   Hotspot
•   Balanceo de Carga
•   Control de Trafico
•   Etc.

Características de RouterOS

El sistema RouterOS nos permite controlar y programar un dispositivo Router MikroTik desde un punto de vista granular, con lo que nos permite moldear cada parte de nuestro router, como el comportamiento de cada interface.

Configuración y Acceso

•   Acceso basado en MAC para cuando no tiene configuración el equipo.
•   WinBox: Herramienta de configuración gráfica (GUI) para Windows.


Arquitecturas de MikroTik

|Arquitectura	|Series|
|-----|-----|
|mipsbe	|CRS, RB4xx, RB9xx, SXT, OmniTik, Groove, METAL, SEXTANT|
|smips	hAP lite|
|tile|	CCR|
|ppc|	RB3xx, RB600, RB800, RB1xxx
|x86|	PC / x86, RB230|
|arm	|RB3011|
|mmips|	RB750Gr3|
|mipsle|	RB1xx, RB5xx, RB Crossroads (discontinuando)|
 
 
Cuando se va a realizar un Upgrade, Downgrade, o reinstalación de Sistema Operativo es indispensable realizar la identificación de la arquitectura que tiene el Router.

Si se llega a cargar una archivo con la arquitectura incorrecta no realizara ninguna acción el sistema operativo.

Ingresando a RouterOS

De las formas de ingresar al router veremos las siguientes:

•   Web browser
•   WinBox
Ingreso por Web browser

Este método solo puede ser usado cuando el router ya tiene parámetros previamente configurados. Solo hay que ingresar en la barra de navegación la dirección IP asignada al router. Por defecto se utiliza 192.168.88.1

Ingreso por WinBox

Para obtener el software WinBox se puede acceder a la siguiente dirección web: http://
www.mikrotik.com/download

Y en el apartado Useful tools and utilities damos clic en el link de WinBox 


El Winbox es un archivo autoejecutable el cual no se requiere instalar. Acceder al Winbox
•   Ejecutar el icono WinBox, para abrir la aplicación

 

•	Si queremos que el Winbox encuentre nuestro Router tenemos que cambiar a la pestaña Neighbors

•   Darle click en refresh.

•   Seleccionar la dirección MAC o la dirección IP del equipo.

•   Hacer clic en Conectar

 

•   Esperar a que se cargue la interfaz completa. 


Una ves que se conecte con el Router se cargara la interface de configuración y en la parte izquierda se muestra el Menú Principal.

  


MODULO 2 Configuración del Router MikroTik
Actividad 1.- Actualizar Router OS

Identificar la Arquitectura del Router

Primero hay que conocer la arquitectura del Router al que se desea actualizar el Sistema
Operativo (RouterOS)

Para conocer el tipo de arquitectura se puede ver de la siguiente manera:

1. Barra del titulo del Winbox.

La barra del título nos muestra la siguiente información:

•   Usuario con el que se conecta.

•   Dirección IP del equipo.

•   Versión del RouterOS v6.32.2

•   Tipo de activo hAP lite en arquitectura (smips).

 


2. Atravez del menu en el Winbox en System / Resources podemos ver la arquitectura:

  


3. Por medio de la consola con el comando:

/system resource print

 

Descargar RouterOS

En la pagina de Mikrotik accedemos a la sección de Download y nos posesionamos en el apartado:

Hay que elegir la arquitectura correcta para nuestra Router. Para esta caso smips. Y nos desplegara los recursos disponibles.

Main package: es el archivo principal con el sistema RouterOS

Extra packages: son extensiones y funciones adicionales para el RouterOS

Changelog: aquí se puede ver el archivo con las especificaciones que se agregaron en en la actualización.

  


Cargar RouterOS en el Router

Solo tenemos que tomar el archivo routeros-smips-x.xx.x.npk y ponerlo en el Winbox, de esta forma la aplicación enviara el archivo al apartado File List.

 

Realizando la Actualización

Para aplicar la actualización se tiene que acceder a New Terminal.

  


Ahora solo hay que reiniciar el Router el comando es el siguiente:

/system reboot
pedirá confirmación.

 

Realizar un downgrade de versión

A los equipos MikroTik se les puede realizar un downgrade de Sistema Operativo si así lo requerimos ya sea por bugs que se encuentren en la versión más reciente o por cambios en la operación.

Hacer downgrade del RouterOS, solo hay que descargar el archivo y pasarlo a el Router que se cargue en la sección Files, una vez que tengamos el paquete del Sistema operativo en la memoria del Router solo hay que ejecutar la siguiente instrucción en la Terminal.

Sintaxis del código de programación:
/system package downgrade
Al reiniciar podemos ver en nuestro WinBox que la versión de nuestro Router está actualizada (o cargada la versión que queremos). 


Actividad 2.- Borrar la configuración del Router

Primero hay que borrar la configuración básica que tiene el Router ya que esta configurado para trabajar como SOHO Router.

Puerto 1: WAN entrada de Internet sin permitir la administración del equipo.

Puertos del 2 al 4: configuración LAN de la misma red 192.168.88.0/24 con el Gateway
192.168.88.1

Puerto WLAN: agregado a la Red LAN.

Configuración desde Cero con Mikrotik

Una configuración desde cero nos permite crear nuestras propias reglas, rutas y subredes, así como también saber exactamente qué es lo que está programado en nuestro Router.

Reset configuration

 

La ventana de reset nos da 3 opciones para elegir antes de realizar el Reset de la configuración.
Keep User Configuration.- reinicia el equipo pero mantiene los usuarios y contraseñas. No Default Configuration.- esta es la opción que regresa el Router a cero, borra toda la
configuración (no borra los archivos que están en Files).

Do Not Backup.- no crea un respaldo automático.

Run After Reset.- se especifica un archivo de respaldo que se quiere que se cargue después de que se reinició el Router.

Sintaxis para resetear el Router desde la Terminal:

/system reset-configuration no-defaults=yes
al ejecutar preguntara si quiere continuar

Dangerous! Reset anyway? [y/N]: 


Actividad 3.- Definir Nombres y Direcciones IP

En base a la tabla siguiente cada alumno tomara un numero W que representara su numero de estudiante, y trabajara con los números correspondientes a la fila de su numero:

| |	X	|Y	|Z	|Broadcast|
|-|-----|---|---|---------|
|W=1|	0|	1|	2|	3|
|W=2|	4|	5|	6|	7|
|W=3|	8|	9|	10|	11|
|W=4|	12|	13|	14|	15|
|W=5|	16|	17|	18|	19|
|W=6|	20|	21|	22|	23|
|W=7|	24|	25|	26|	27|
|W=8|	28|	29|	30|	31|
|W=9|	32|	33|	34|	35|
|W=10|	36|	37|	38|	39|
|W=11|	40|	41|	42|	43|
|W=12|	44|	45|	46|	47|
|W=13|	48|	49|	50|	51|
|W=14|	52|	53|	54|	55|
|W=15|	56|	57|	58|	59|
|W=16|	60|	61|	62|	63|
|W=17|	64|	65|	66|	67|
|W=18|	68|	69|	70|	71|
|W=19|	72|	73|	74|	75|
|W=20|	76|	77|	78|	79|
 


En base al numero de estudiante se le dara un nombre al Router que se conoce como identidad, para darle un nombre de Identidad al router hay que acceder al Menu Principal a la Opción: "System" y despues elegir la sub-opcion "Identity".

 

La identidad del Router esta compuesta de la siguiente forma "Estudiante-W", donde W es el numero de estudiante, donde el numero se compondrá de 2 dígitos ejemplo: si es el estudiante 2 la Identidad de su Router será: "Estudiante-02" y para el estudiante 12 sera "Estudiante-12". 


Actividad 4.- Configuración de la Red LAN

Configuración de un Router MikroTik desde cero, para que nos funcione como un Router con acceso a internet.

Que es lo que requiere una Red LAN.

Una interface para actuar como Gateway para los equipos de la LAN, en nuestro ejercicio usaremos la Interface Virtual de tipo Bridge:

Para crear esta interface lo que requerimos es ir en nuestro menú principal a la opción
Bridge.

Una vez en la ventana Bridge crearemos una interface Bridge, lo único que requerimos es crear un Bridge, el único parámetro que se requiere es el nombre.

 

Syntaxis del código de programación:
/interface bridge add name=bridge-RedLAN

Una ves creado el Bridge lo que vamos a realizar es crear la configuración de Red LAN, para esto lo primero que se realizara es asignarle una dirección IP a la interface Bridge.

 

Syntaxis del código de programación:
/ip address add address=192.168.(100+W).1/24 interface=bridge- RedLAN network=192.168.(100+W).0 


Crearemos el Servidor DHCP

El Pool son las direcciones IP que va a entregar nuestro equipo a los clientes, un Pool de direcciones es un rango de donde va a tomar cuales son las IP’s que le dará a cada uno de los equipos que se conecte a la interface de la Red LAN.

Para crear un Pool, hay que acceder al menú principal a la sección IP, de hay seleccionar la opción Pool.

Un Pool lo que requiere es un Nombre para poder conocerlo en ventanas proximas.

En Address ingresaremos la dirección IP de inicio y la IP final del rango, ambas separadas por un guión “-”.

 

Sintaxis del código de programación:
/ip pool add name=pool-RedLAN ranges=192.168.(100+W).10-192.168. (100+W).254

El Servicio de DHCP se lo asignaremos a la Interface Bridge que se creo con anterioridad: RedLAN, el servidor DHCP lo que hace es que entrega las direcciones IP a cada Cliente que se conecte a nuestro router.

  


Sintaxis del código de programación:
/ip dhcp-server add address-pool=pool-RedLAN disabled=no interface=bridge-RedLAN name=server-DHCP

El servidor DHCP lo único que hace es enviar las direcciones IP a los equipos clientes, para decirle a cada equipo quien va a ser su Gateway, y el DNS.

En la pestaña Network configuraremos los parámetros de red que le asignaremos a los clientes de nuestra red LAN que son todas las IP de la Red 192.168.(100+W).0/24

 

Sintaxis del código de programación:
/ip dhcp-server network add address=192.168.(100+W).0/24 dns- server=192.168.(100+W).1 gateway=192.168.(100+W).1 


Agregar interfaces físicas a un virtual.

Ahora que tenemos una configuración de Red LAN, lo que necesitamos hacer es que nuestros puertos Ethernet formen parte de nuestro Bridge.

Para realizar que nuestro puerto físico tenga la misma configuración de nuestra interface virtual, le diremos a nuestro puerto ether2 que formara parte de nuestro Bridge.

Para esto accederemos a la opción Bridge y hay nos cambiamos a la pestaña Ports y agregaremos la relación entre la interface y el bridge

 

Obteniendo un registro donde nos indica que nuestro puerto físico "ether2" es parte de una interface virtual de tipo Bridge con el nombre "birdge-RedLAN"

  


Crear la configuración de Switch

Para hacer que el resto de los puertos LAN estén dentro de la misma red y dominio de
Broadcast hacemos que los demás puertos sean esclavos del puerto ether2.

Para esto entraremos a la opción de Interfaces y entraremos a la configuración del puerto
"ether3" y le diremos que su Master Port será el "ether2".

 

Sintaxis del código de programación:
/interface ethernet
set [ find default-name=ether3 ] master-port=ether2 


