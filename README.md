# SMX2-M12.2-Sintesi-Fase4-A06

#### Clasificacion de las IP's

Hay 5 clases de IP y la clasififcacion se basa en la cantidad de bits que se utilizan para indentificar la red y el host.
Las direcciones IP pueden ser fijas o dinámicas. Las direcciones IP fijas se asignan de forma manual y no cambian, mientras que las direcciones IP dinámicas cambian cada vez que se reinicia el router.

Por ejemplo en la clase A los primeros 8 bits se utilizan para identificar la red y los 24 restantes para el host.

|Clase de la IP |Desde-Hasta |Mascara de red |
|----------|:----------:|:----------|
|Clase A |0.0.0.0 a 127.255.255.255 |255.0.0.0  /8 |
|Clase B |128.0.0.0 a 191.255.255.255 |255.255.0.0  /16 |
|Clase C |192.0.0.0 a 223.255.255.255 |255.255.255.0  /24 |
|Clase D |224.0.0.0 a 239.255.255.255 |Multicast |
|Clase E |240.0.0.0 a 255.255.255.255 |Reservadas para uso futuro |

Todos los dispositivos conectados a un router comparten la misma dirección IP pública esas direcciones IP públicas son visibles desde todo Internet.

#### Clasificacion de las IP's privadas

Las direcciones IP privadas solo operan de forma local y se utilizan para identificar a cada dispositivo conectado a una red privada, como una red doméstica o de oficina.

Hay tres rangos de direcciones IP privadas que se pueden utilizar en redes privadas:

|Clase de la IP |Desde-Hasta |
|----------|:----------:|
|Clase A |10.0.0.0 a 10.255.255.255 |
|Clase B |172.16.0.0 a 172.31.255.255 |
|Clase C |192.168.0.0 a 192.168.255.255 |

#### Que IPs se utilizan para servidores y cuales IPs para puertas de enlace

los servidores utilizan direcciones IP públicas y IP privadas, las IP públicas para que puedan ser accesibles desde cualquier lugar de Internet y las IP privadas para IP privadas para comunicarse con otros dispositivos dentro de la red privada. Estas direcciones IP se asignan a los servidores de forma estática, lo que significa que no cambian con el tiempo.

Las IPs que se utilizan para los servidorrs son IPs grandes, por ejemplo __192.168.16.200__ hasta __192.168.16.254__ ya que se considera una IP alta de la 200 a la 254, todo lo que entre en ese rango lo consideraremos una IP alta.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Fotoservidor.png "imagen")

Las puertas de enlace utilizan direcciones IP privadas y Públicas, usa las IP privadas para comunicarse con otros dispositivos dentro de la red privada y las IP públicas para permitir el acceso desde Internet.. Estas direcciones IP se asignan de forma estática o dinámica, dependiendo de la configuración de la red.

Las IPs que utilizamos para las puertas de enlace son las mas bajas, es decir las que asignaremos al ruter, por ejemplo si el ruter tiene una ip __192.168.16.1__ nuestra puerta de enlace sera esa.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/imagenpc.png "imagen")

#### Funcionalidad de la máscaras de red y cómo se calculan según la clasificación de IP's.

Una máscara de red es una combinación de bits que permite delimitar el ámbito de una red de ordenadores1. La función de la máscara de red es indicar a todos los dispositivos qué parte de la dirección IP es la correspondiente al número de la red, a la máscara de subred y la que corresponde al host1.

Las máscaras de red se utilizan para saber si una dirección IP pertenece a una subred2. Con un conjunto de 32 bits consecutivos para determinar la parte de red de una dirección y el resto de los 32 bits todos a cero para determinar la parte que identifica al host.

La división, teniendo en cuenta la clase de dirección IP, se realiza de la siguiente forma:

|Clase de la IP |Desde-Hasta |
|----------|:----------:|
|Clase A: |Máscara de red de 8 bits (255.0.0.0) |
|Clase B: |Máscara de red de 16 bits (255.255.0.0) |
|Clase C: |Máscara de red de 24 bits (255.255.255.0) |

El cálculo de la máscara de subred se realiza de la siguiente forma:

Cantidad de subredes y notación rápida: Determina cuántas subredes necesitas y utiliza una notación rápida para representarlas.
Calcular máscara de red y de subred: Calcula la máscara de red y la máscara de subred basándote en la cantidad de subredes que necesitas.
Calcular cantidad de hosts por subred y el salto de red: Determina cuántos hosts pueden existir en cada subred y calcula el salto de red.
Asignar IP a nuestras subredes: Asigna las direcciones IP a las subredes.

#### VLAN (qué es y para qué sirve, configuración en Packet Tracer)

las VLAN permiten dividir la red en grupos lógicos en lugar de físicos, lo que ayuda a liberar al personal de TI de las restricciones del diseño de red y la infraestructura de cableado existente.

Las VLAN son una colección de computadoras en una o varias LAN que se agrupan en un solo dominio de difusión, independientemente de su ubicación física. Esto significa que los dispositivos pueden estar ubicados en diferentes lugares físicos, pero aún así pueden comunicarse entre sí como si estuvieran en la misma ubicación física.

Las VLAN facilitan el diseño, la implementación y la administración de la red al permitir que los dispositivos se agrupen según su función o patrón de tráfico, en lugar de su ubicación física. Por ejemplo, los dispositivos que necesitan comunicarse con frecuencia se pueden agrupar en una VLAN separada para mejorar el rendimiento y reducir el tráfico innecesario en la red.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/vlan.png "imagen")

Configuración en Packet tracer: 
  
Es bastante sencillo, la red consistirá en 6 ordenadores, 2 switches y la red dividida en 3 VLANS.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Vlan2.png "imagen")

Debemos realizar la conexión de los Switches y las PCs. Los switches se conectan por la interfaz Fa3/1 de cada uno de ellos con cable cruzado y en modo trunk  

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Vlan3.png "imagen")

Para asignar las IPs y la máscara de Red de nuestros equipos haremos doble click en la interfaz gráfica en cada uno de ellos en IP configuration introducimos la IP y su máscara de red. 

El Gateway y DNS no son necesarios en este ejemplo. 

Así usaremos una máscara de red /24 por lo tanto 255.255.255.0

#### Configuracion de red Windows

Para acceder a la configuracion dinamica de Windows abriremos el CMD. Para liberar la IP usaremos el comando: ipconfig/release. Asi podremos cambiar la IP. En el CMD veremos lo siguiente:

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/ConfiguracionWindowsdinamica.png "imagen")

Una vez hemos liberado la IP, tendremos que usar este comando: ipconfig/renew. Esta IP sirve para solicitar una nueva IP al servidor DNS. Una vez se ejecute el comando veremos lo siguiente:

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Configuracionfinalwindoes.png "imagen")

Para acceder a la configuracion estatica dentro de Windows iremos a __Configuracion__, dentro de configuracion veremos la opcion de __Red e Internet__, Una vez dentro iremos a __Ethernet__. Nos saldra lo siguiente: 

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/ConfiguracionWindows.png "imagen")

Le daremos a __Editar__ en el apartado __Asignación de IP__ y seleccionaremos __Manual__. Veremos lo siguiente:

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/configuracionwindowsmanual.png "imagen")

#### Configuracion de red Ubuntu 16.04

Utilizaremos el comando **"nano \etc\network\interfaces"** para entrar en la configuracion de las redes.
El comando **nano** se utiliza para entrar o modificar el archivo.


Para hacer que nos asignen una IP dinamica por DHCP, escribiremos lo siguiente en el fichero **interfaces**.
- auto enp0s3
- iface enp0s3 inet dhcp

[(E+200E)"imagen"]

Para asignar una IP estatica , escribiremos lo sigueiente en el fichero **interfaces**.
- auto enp0s3
- iface enp0s3 inet static
- address 192.168.1.2
- netmask 255.255.255.0
- gateway 192.168.1.1

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/CONFIGURACION16.04.png "imagen")

Aqui hos dejamos una representación de como queda todo en la terminal.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/FINALIP16.04.png "imagen")

(#) -> funciona para comentar una linea y decir que esa linea es puro texto y no lo interprete.

Una vez hagamos los cambios que queremos tenemos la opcion de reiniciar todas las interfaces, pero esto puede ser un tanto bruto en algunos casos, este reinicio se ejecuta con estos comandos.
- sudo service network restart
- sudo service network stop
- sudo service network start

Tambien tenemos la opcion de reiniciar solo la interfaz que queremos, esta seria la mejor opcion, y se realizaria de la siguiente forma
- sudo ifdown enp0s3
- sudo ifup enp0s3

Para configurar el servidor DNS desberemos poner la siguiente direccion **fichero/etc/resolv.conf**, dentro de esta deberemos escribir lo siguiente:
- nameserver 8.8.8.8

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/16.04uLTIMA.png "imagen")

#### Configuracion de red Ubuntu 22.04

Estas versiones utilizan netplan.
 
Para encontrar el fichero en el cual debemos modificar la IP, tendremos que escribir el siguiente comando **/etc/netplan/****.yaml**.

En caso de que no exista el fichero usaremos el comando **sudo netplan generate** para generar un fichero.

Para establecer una IP estatica deberemos seguir los siguientes pasos:
- dhcp4 : no (En caso de que usemos IPv6 lo pondremos en el dhcp6)
- address 192.168.1.2/24
- gateway 192.168.1.1

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Estatica22.04.png "imagen")

Despues de establecer la ip con la mascara y el gateway, establecermos el servidor, en este caso deberemos poner el nombre y la IP:
- Google: 8.8.8.8

Para apolicar todos estos cambios usaremos el comando **sudo netplan apply**

Aqui hos dejamos una representación de como queda todo en la terminal.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Finalip22.04.png "imagen")

Para establecer una IP dinamica simplemente tendremos que poner "yes" en el apartado del dhcp y escribir el comando **sudo netplan apply** para aplicar los cambios, tras hacer esto se nos asignara una IP automaticamente.

Aqui hos dejamos una representación de como queda todo en la terminal.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/configuraciondinamica22.04.png "imagen")