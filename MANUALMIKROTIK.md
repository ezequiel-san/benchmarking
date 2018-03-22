# Manual Básico MIKROTik

Información Básica
¿Qué es Router OS?

Es el sistema operativo del hardware MikroTik RoaterBOARD, tiene las siguientes características:

-   Router
-   Servidor DHCP
-   Firewall
-   VPN
-   Wireless
-   Calidad de Servicio (QoS)
-   VLAN
-   Hotspot
-   Balanceo de Carga
-   Control de Trafico
-   Etc.

Características de RouterOS

El sistema RouterOS nos permite controlar y programar un dispositivo Router MikroTik desde un punto de vista granular, con lo que nos permite moldear cada parte de nuestro router, como el comportamiento de cada interface.

Configuración y Acceso

-   Acceso basado en MAC para cuando no tiene configuración el equipo.
-   WinBox: Herramienta de configuración gráfica (GUI) para Windows.


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

-   Web browser
-   WinBox
Ingreso por Web browser

Este método solo puede ser usado cuando el router ya tiene parámetros previamente configurados. Solo hay que ingresar en la barra de navegación la dirección IP asignada al router. Por defecto se utiliza 192.168.88.1

Ingreso por WinBox

Para obtener el software WinBox se puede acceder a la siguiente dirección web: http://
www.mikrotik.com/download

Y en el apartado Useful tools and utilities damos clic en el link de WinBox 


El Winbox es un archivo autoejecutable el cual no se requiere instalar. Acceder al Winbox
-   Ejecutar el icono WinBox, para abrir la aplicación

 

-	Si queremos que el Winbox encuentre nuestro Router tenemos que cambiar a la pestaña Neighbors

-  Darle click en refresh.

-   Seleccionar la dirección MAC o la dirección IP del equipo.

-   Hacer clic en Conectar

 

-   Esperar a que se cargue la interfaz completa. 


Una ves que se conecte con el Router se cargara la interface de configuración y en la parte izquierda se muestra el Menú Principal.

  


# MODULO 2 Configuración del Router MikroTik
Actividad 1.- Actualizar Router OS

Identificar la Arquitectura del Router

Primero hay que conocer la arquitectura del Router al que se desea actualizar el Sistema
Operativo (RouterOS)

Para conocer el tipo de arquitectura se puede ver de la siguiente manera:

1. Barra del titulo del Winbox.

La barra del título nos muestra la siguiente información:

-  Usuario con el que se conecta.

-   Dirección IP del equipo.

-   Versión del RouterOS v6.32.2

-   Tipo de activo hAP lite en arquitectura (smips).

 


2.  Atravez del menu en el Winbox en System / Resources podemos ver la arquitectura:

  


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


## Actividad 4.- Configuración de la Red LAN

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


## Actividad 5.- Configurar Interface WAN

Un puerto WAN en un Router es por el cual recibimos un servicio desde otro router.

Configurando Parámetros de forma Manual

La ruta por defecto es el destino de todo el tráfico (paquetes) que se envían a subredes desconocidos. (Se puede conocer también como la ruta a internet).

 

Sintaxis del código de programación:
/ip route add gateway=10.1.1.Y

Configuración del Puerto WAN

El puerto WAN (Wide Area Network en inglés) es el puerto en que vamos a recibir nuestro servicio de internet.
Para configurar la direction IP hay que entrar a IP en el menú principal, después elegir la opción Address, aquí generaremos una nueva dirección IP.

 

Sintaxis del código de programación:
/ip address add address=10.1.1.Z/30 interface=wlan1 network=10.1.1.X 


Configuración de DNS para el Router.

Habilitaremos el DNS (Domain Name System), para que al buscar las páginas por nombre encontremos la dirección IP del servidor donde se encuentra alojada la pagina WEB.

De esta forma nuestro router sera el encargado de ir a consultar las direcciones de las Paginas Web a las que quieren acceder los clientes conectados a nuestra red LAN, y el Router almacenara esos nombres de Dominio y sus direcciones IP en un Cache de 2MB de Memoria, de esta forma se optimizaran las consultas de todos los clientes que tengamos.

Ademas habilitaremos la función para que todas las peticiones de DNS las resuelva nuestro Router.

 

Sintaxis del código de programación:
/ip dns set allow-remote-requests=yes servers=10.1.1.Z

Configurando Parámetros de forma Manual

La forma mas rápida de configurar los valores es conectarte a un equipo que ya los entrega de forma automática, cuando ya tenemos un equipo que la configuración de su RED lo único que requerimos es activar el Servicio DHCP Client.

Para tomar la configuración lo único es que tenemos que activar el DHCP en una interface especifica. En nuestro caso activaremos el DHCP Cliente en el puerto "ether1".

para acceder a la configuración hay que entrar a IP en el menú principal y elegir la opción
"DHCP Client"

  


Enmascaramiento de la Red LAN

Ahora hay que configurar el NAT del router para que el tráfico que saldrá de nuestra RED
local LAN salga con la dirección IP pública que tiene en la interfaz WAN.

 

Sintaxis del código de programación:
/ip firewall nat add action=masquerade chain=srcnat out- interface=wlan1 


## Actividad 6.- Configurar el Firewall

Proteger el Router y a los clientes de la LAN

¿Cómo funciona el Firewall? Opera usando reglas. Estas tienen 2 opciones:

-	The matcher.- Todas las condiciones tienen que ser verificadas y deben coincidir, para poder aplicar.

-	The Action.- Una vez que todos los parámetros coinciden y pasa la primera verificación, se procede con la acción.

Se creara una lista con el ID de nuestra red LAN que tienen permiso de pasar atravez de nuestro Router.

 

Sintaxis del código de programación:
/ip firewall address-list
add address=192.168.(100+W).0/24 list=RedLAN


La configuración las reglas de filtrado no permitirían proteger nuestra red de ataques y conexiones no deseados.

Sintaxis del código de programación:
/ip firewall filter
add chain=input comment=IN_CONN_ESTABLISHED connection-
state=established
add chain=input comment=IN_CONN_RELATED connection-state=related
add action=drop chain=input comment=IN_CONN_INVALID connection-
state=invalid
add chain=input comment=IN_CONN_RELATED connection-state=related
add chain=input comment=IN_IP_PERMITIDAS src-address-list=RedLAN
add action=drop chain=input comment=IN_DENEGAR_RESTO
### Para proteger a los clientes internos de la RED.
add chain=forward comment=FW_CONN_ESTABLISHED connection- state=established
add chain=forward comment=FW_CONN_RELATED connection-state=related 


add action=drop chain=forward comment=FW_CONN_INVALID connection- state=invalid
add chain=forward comment=FW_IP_PERMITIDAS src-address-list=RedLAN
add action=drop chain=forward comment=FW_DENEGAR_RESTO

Obligar a usar el DNS del Router

Accion Redirect + DNS

En muchas ocaciones los clientes pueden manipular la configuración de su equipo y colocar una dirección de servidor IP foráneo, lo que ocasionara que nuestro trafico saliente se incremente y solo por el hecho de resolver Nombres de Dominio.

No importa que DNS tengan configurado los equipos clientes, si nuestro Router tiene memoria para guardar DNS podemos forzar a que sea el que se utilice por default.

Para esto vamos a la pestaña de NAT y crearemos las siguientes reglas:























Sintaxis del código de programación:
/ip firewall nat
add action=redirect chain=dstnat dst-port=53 protocol=tcp to-
ports=53 comment=DNS_Transparente
add action=redirect chain=dstnat dst-port=53 protocol=udp to-
ports=53 


Se creara una segunda regla similar, lo único que va a cambiar es que el Protocolo será
"UDP".

 

De esta forma como se sabe que el DNS utiliza el puerto 53 ya sea en Protocolo TCP o UDP, lo que estamos haciendo es que todo el trafico que entra a nuestro Router y va a realizar una consulta de Nombre de Dominio, lo vamos a re dirigir a nuestro propio Router, para que nuestro router sea quien le entregue la dirección IP al cliente del sitio WEB al
que quiere acceder. 


## Actividad 7.- Configuración Inalámbrica.

Los equipos MikroTik RouterBoard, nos permite conectarlos a una Red Inalámbrica existente con su modo de operación "Station" o propagar una red Inalámbrica para recibir conexiones en su modo "AP Bridge".

Adicionalmente a partir de la versión 6.37 del RouterOS, se pueden configurar los equipos con radio Wi-Fi, para conectarlos a una red Inalámbrica y generar al mismo tiempo otra Red Alterna de forma independiente.

Conectar el equipo a la red Inalámbrica PTMP

Perfiles de Seguridad

Ya sea para conectar el equipo a una red Inalámbrica o generar una red Inalámbrica se requiere generar un perfil de seguridad para conectarse a la red o permitir que se conecten a nuestra red.

Dar de alta la contraseña de la red inalámbrica: cursomikrotik

Para configurar el Perfil de seguridad hay que entrar a la opción "Wireless" del menú principal, y acceder a la pestaña "Security Profiles" y generar un nuevo perfil en donde solo esta seleccionada la opción "WPA2 PSK" y la WPA2 Pre-Shared Key será "cursomikrotik"

  


Sintaxis del código de programación:
/interface wireless security-profiles
add authentication-types=wpa2-psk management-protection=allowed
mode=dynamic-keys name="Password Curso" wpa2-pre-shared-
key=cursomikrotik

Configurando el modo Station

El modo Station nos permite conectarnos a una Red Inalámbrica a la que tengamos acceso y nos encontremos cerca.

En esta actividad el Alumno se conectara a la Red Inalámbrica que esta propagando el instructor, con el SSID "MikroTik-PTMP".

Lo primero que tenemos que hacer es acceder a la opción "Wireless" del Menú principal.














Como podremos ver nuestra interface se encuentra desactivada, lo primero que realizaremos es activar la interface "wlan1" dando un solo clic en el registro, y posteriormente la habilitaremos en el botón que tiene el símbolo de check. Podremos ver que el color de las letras del registro cambio de "gris" a "negro".

Para configurar el comportamiento de la interface "wlan1" daremos doble clic en el renglón.

  


Los parámetros que únicamente se van a configurar son:

Band: elegiremos la opción 2GHz-only-N
SSID: escribiremos el nombre de la red que esta propagando el Instructor, "MikroTik-PTMP"

Security Profile: aqui se va a elegir el Perfil de seguridad que se creo con anterioridad.

La forma de saber si el enlace de comunicación se realizo con éxito es que en la tabla de Wireless en el registro de la "wlan1" a la izquierda aparece una letra "R" que significa "Running".

 

Sintaxis del código de programación:
/interface wireless
set [ find default-name=wlan1 ] mode=station band=2ghz-onlyn
disabled=no security-profile="Password Curso" ssid=MikroTik-PTMP
wireless-protocol=any

Configurando el Modo AP

Nuestro router con una version de RouterOS 6.37 en delante, nos permite crear una interface Virtual, la cual la podremos configurar como un Access Point para generar una red Inalámbrica.

Primero estando en la ventana de Wireless table ala cual accedemos desde el menu principal en el Boton Wireless.

Desplegaremos el menu que pararece en el Boton con el Simbolo de MAS (+), y se elegiría la opción "Virtual".

  


De esta forma nos aparece una nueva ventana en donde se creara una Nueva Interface del tipo Inalámbrica.

 

Los únicos parámetros que nos interesa configurar son:

SSID: el estudiante creara una red inalámbrica con el Nombre "Estudiente-W", donde hay que recordar que la W es el numero de estudiante y tiene que manejar 2 (dos) dígitos.

De esta forma tendremos una interface del tipo Virtual que depende del radio físico que posee nuestro router. Viéndose de la siguiente manera.

 

Sintaxis del código de programación:
/interface wireless
add disabled=no master-interface=wlan1 mode=ap-bridge name=wlan2
security-profile="Password Curso" ssid=Estudiante-(W)

Red LAN con propagación Inalámbrica.
Ahora que tenemos una red inalámbrica propia es necesario agregarla a nuestra Red LAN, para eso hay que ir al menú Bridge y en la pestaña Ports, agregaremos nuestra nueva interface Virtual "wlan2".

 

Sintaxis del código de programación:
/interface bridge port
add bridge=bridge-RedLAN interface=wlan2 


## Actividad 8.- Respaldo y Exportación de Configuración.

Cuando se realiza una configuración de un router, nosotros podemos realizar dos acciones con esta configuración, ya sea que realicemos un respaldo o una exportación:

Respaldo.- Es un archivo de Backup que contiene todos los parámetros de configuración, a si como usuarios y contraseñas de acceso.

El archivo que se genera tiene una encriptación para la protección de la información.

Este archivo no se recomienda usar en otro router que no sea en el mismo que se genero fisicamente.

La forma de identificar este archivo es por que tiene una extension "*.backup"

Exportación.- Es un archivo de tipo Script, que es de tipo texto plano, el cual podremos ver su contenido sin problema si lo abrimos con editor de texto.

Este documento solo guarda la información de los parámetros de configuración, nunca los nombres de usuario y contraseñas.

Este es el archivo ideal para llevar la configuración de un Router a otro Router ya sea con las mismas características físicas o mas.

La forma de identificar este archivo es por que tiene una extension "*.rsc".

Para esta actividad vamos a realizar el Laboratorio de Respaldar nuestra configuración en
Backup y Script.

Laboratorio 8.1 Backup

Hay que acceder a la opción "Files" en el menú principal.

 

Lo único que tenemos que hacer es darle un Nombre al archivo y dar clic en el Botón
"Backup", y se generar un archivo en la memoria de nuestro Router del tipo Backup. 


Laboratorio 8.2 Script

Para generar un Script hay que elegir la opción New Terminal de nuestra menú principal.Y
se escribe el siguiente comando:

Sintaxis del código de programación:
export file=ConfiguracionPTMP

 

De esta forma en la memoria de nuestro Router tendremos dos archivos con el mismo nombre pero con diferente tipo de extension:


 

Estos archivos hay que copiarlos a nuestra computadora para tenerlos en un lugar seguro: 


Laboratorio 8.3 Restaurar desde un Backup

Para realizar este laboratorio, aplicaremos un "No Default Configuration" a nuestro Router.

* Asegurarse de tener los archivos respaldados en la computadora antes de borrar la configuración. Ya que esta acción también borrara los archivos en la memoria.

Una ves que entramos accediendo con MAC-Address, cargamos el archivo "*.Backup" a nuestro Router, automáticamente desplegara la ventana de "File List".

 

Para restaurar el backup hay que seleccionarlo y posteriormente pulsamos el Botón
"Restore".

 

y en la ventana de Restore confirmaremos que vamos a restaurar el archivo.

 

Por ultimo nos preguntara que si queremos restaurar la configuración y reiniciar. A esta pregunta la contestaremos con el Botón "Yes". 


Laboratorio 8.4 Cargar configuración desde un Script

Para realizar este laboratorio, aplicaremos un "No Default Configuration" a nuestro Router.

* Asegurarse de tener los archivos respaldados en la computadora antes de borrar la configuración. Ya que esta acción también borrara los archivos en la memoria.

Una ves que entramos accediendo con MAC-Address, cargamos el archivo "*.rsc" a nuestro Router, automáticamente desplegara la ventana de "File List".

 

Para generar un Script hay que elegir la opción New Terminal de nuestra menú principal.Y
se escribe el siguiente comando:

Sintaxis del código de programación:
import file=ConfiguracionPTMP.rsc
*Importante.- hay que escribir la extension del archivo, y respetar mayusculas y minúsculas, si no para el sistema será un archivo que no existe.

  


## Actividad 9.- Configuración de Control de Trafico

Configurar Marcado de Conexiones y Trafico con Mangle

El control de tráfico es la función del router mikrotik en la sección deMangle que nos permite limitar la velocidad de navegación de la información que requiere cada uno de los clientes que está en nuestra Red LAN.

Primero marcamos los paquetes que van a transitar por el Router.

/ip firewall mangle
add action=mark-connection chain=prerouting connection-mark=no-
mark new-connection-mark=192.168.(100+W).254_conn src-
address=192.168.(100+W).254

 

/ip firewall mangle
add action=mark-packet chain=prerouting connection-mark=192.168.
(100+W).254 new-packet-mark=192.168.(100+W).254_traffic
passthrough=no

  


Configurar el Queue Tree

Se definen los servicios que tenemos disponibles y en que interfaces están trabajando,: Download.- es hacia la red LAN
Upload.- es hacia el WAN

Aquí es donde definimos cuanta velocidad tenemos disponible para nuestra red LAN en cada servicio.

/queue tree
add name="Servicio Download" parent=bridge-RedLAN queue=pcq-
download-default
add name="Servicio Upload" parent=wlan1 queue=pcq-upload-default

 

  


Registrar cada cliente con un plan de Download y Upload

Aquí es donde registraremos cada cliente en base a las marcas de paquetes que se realizaron en la sección de Mangle.

/queue tree
add max-limit=1M name=192.168.(100+W).254_DL packet-mark=192.168.
(100+W).254_traffic parent="Servicio Download" queue=pcq-download-
default
add max-limit=128k name=192.168.(100+W).254_UL packet-
mark=192.168.(100+W).254_traffic parent="Servicio Upload"
queue=pcq-upload-default

 

Una ves terminada este laboratorio hay que generar un Respaldo y un Export con el
Nombre: ConfiguracionControlTrafico. 


## Actividad 10.- VLAN

Una VLAN es una interface virtual dentro de una física, que sirve para separar el trafico que va de un dispositivo hacia otro, y no mezclarlo en los equipos físicos por los que son transportados los datos. Las VLAN son muy utilizadas en la separación de servicios, como cuando tenemos Datos / Telefonía / Video.

 

Cuando se Trabaja con VLAN se requiere de equipos de nivel Capa 2+ (Layer 2+) comúnmente llamados Administrables, El entrenador manejara un Switch con estas características en donde se tiene un puerto troncal, en donde se reciben todas las redes con un ID de VLAN para cada Estudiante, y de esta forma cada puerto de acceso de nuestro Switch es de tipo Híbrido, en donde se realiza el Untagged de una de las Redes VLAN, y se envían todas las redes con el TAG que solo podrían leer los equipos que conozcan ese mismo id TAG. Los puertos solo pueden una red Untagged, y N cantidad de Redes Tagged.

 

Para realizar este Laboratorio cada Alumno cargara el Backup de "ConfiguracionPTMP"

En este laboratorio recibiremos por un puerto troncal un ID VLAN. en el cual tendremos un servicio de datos. 


Laboratorio 10.1 Recibir Red con TAG

En la sección Interfaces accederemos y crearemos una nueva interface VLAN, con los siguientes datos:

Name: ether1-vlan(100+W) VLAN ID: (100+W) Interface: ether1


De esta forma tenemos un puerto donde recibimos un servicio identificado con un TAG Cuando entra un servicio de VLAN, el trafico que se genera tiene un identificador que solo
esa red conozca.

Ahora que tenemos configurado nuestra nueva interface Virtual le activaremos el Servicio DHCP Client. Si nuestra interface Virtual obtiene direction IP esta correcta nuestra configuración. 


Laboratorio 10.2 Realizar Untagged de una VLAN.

Ahora que tenemos un servicio con un ID VLAN (TAG), lo que vamos a realizar es que nuestra computadora pueda recibir el servicio de la Red.

Lo primero que tenemos que hacer es ir a Bridge y generar una nueva Interface con el
Nombre "bridge-vlan(100+W)".

 

Una vez que tengamos nuestro Bridge creado, ahora agregamos la interface Virtual VLAN "ether1-vlan(100+W)", y también la interface física "ether4".


 

De esta forma conectamos nuestra computadora en el puerto "ether4", obtendrá dirección
IP dentro del segmento de Red de la VLAN.



Generar Respaldo y Exportación con el Nombre: "ConfiguracionVLAN" 


Actividad 11.- Balanceo de Cargas

Cuando un equipo está conectado a internet genera conexiones a servidores remotos. Por este motivo uno de los métodos de balanceo de cargas es PCC (Per Connection Classifier).

 
Para realizar la el Siguiente Laboratorio hay que cargar el Respaldo "ConfiguracionPTMP" Primero se tiene que tener las direcciones IP de nuestra Red de los 2 WAN y de la LAN Políticas que van a tener los paquetes en la red
/ip firewall mangle
add chain=prerouting dst-address=10.1.1.0/30 action=accept in-
interface=RedLAN

add chain=prerouting dst-address=172.16.100.0/24 action=accept in- interface=RedLAN


add chain=prerouting in-interface=wlan1 connection-mark=no-mark action=mark-connection new-connection-mark=ISP1_conn
add chain=prerouting in-interface=ether1 connection-mark=no-mark action=mark-connection new-connection-mark=ISP2_conn 


add chain=prerouting in-interface=RedLAN connection-mark=no-mark dst-address-type=!local per-connection-classifier=both-addresses:
2/0 action=mark-connection new-connection-mark=ISP1_conn
add chain=prerouting in-interface=RedLAN connection-mark=no-mark dst-address-type=!local per-connection-classifier=both-addresses:
2/1 action=mark-connection new-connection-mark=ISP2_conn


add chain=prerouting connection-mark=ISP1_conn in-interface=RedLAN
action=mark-routing new-routing-mark=to_ISP1 passthrough=no

add chain=prerouting connection-mark=ISP2_conn in-interface=RedLAN
action=mark-routing new-routing-mark=to_ISP2passthrough=no


add chain=output connection-mark=ISP1_conn action=mark-routing new-routing-mark=to_ISP1 passthrough=no

add chain=output connection-mark=ISP2_conn action=mark-routing new-routing-mark=to_ISP2 passthrough=no



Rutas de direcciones a internet
/ip route
add dst-address=0.0.0.0/0 gateway=10.1.1.Y routing-mark=to_ISP1
check-gateway=ping
add dst-address=0.0.0.0/0 gateway=172.16.100.1 routing-
mark=to_ISP2 check-gateway=ping
add dst-address=0.0.0.0/0 gateway=10.1.1.Y distance=1 check-
gateway=ping
add dst-address=0.0.0.0/0 gateway=172.16.110.1 distance=2 check-
gateway=ping


Enmascaramiento para usar las Ip’s Públicas en internet
/ip firewall nat
add chain=srcnat out-interface=wlan1 action=masquerade
add chain=srcnat out-interface=ether1 action=masquerade



Generar Respaldo y Exportación con el Nombre: "ConfiguracionBalanceo" 


Actividad 12.- Túneles

Configuración túnel PPTP

Cuando se crean túneles es para conectar 2 redes LAN separadas físicamente y que se comporte como una solo Red.

Cuando se va a crear un túnel entre 2 redes LAN hay que tener en cuenta que cada red
LAN que se va a integrar al túnel, cada una tiene que tener su propio segmento de RED.

El túnel PPTP es el tipo de túnel más sencillo ya que solo se tiene que generar un Secret en el equipo Servidor, y en el cliente se ingresa la dirección IP del servidor o el nombre de dominio si no se tiene una dirección IP publica estática, así como también ingresamos el secret que se generó en el servidor.

  


Laboratorio 12.1 Conectar al Servidor del Instructor.
Para conectarnos al Servidor del Túnel, accederemos a la opción PPP del menú principal. En la ventana "PPP", tenemos que estar en la pestaña Interface y daremos clic en el
botón "add" (+), y seleccionaremos la opción "PPTP Client"
En la pestaña General le daremos un nombre a nuestro túnel, el cual será "VPN".

 

Después nos cambiaremos a la pestaña "Dial Out" e ingresaremos los siguientes parámetros:
Connect To: 10.0.2.1
User: ppp-User
Password: userpptp

