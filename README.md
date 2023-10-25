# SMX2-M12.2-Sintesi-Fase4-A06

#### Clasificacion de las IP's

|Clase de la IP |Desde-Hasta |Mascara de red |
|----------|:----------:|:----------|
|Clase A |0.0.0.0 a 127.255.255.255 |255.0.0.0  /8 |
|Clase B |128.0.0.0 a 191.255.255.255 |255.255.0.0  /16 |
|Clase C |192.0.0.0 a 223.255.255.255 |255.255.255.0  /24 |
|Clase D |224.0.0.0 a 239.255.255.255 |Multicast |
|Clase E |240.0.0.0 a 255.255.255.255 |Reservadas para uso futuro |

#### Clasificacion de las IP's privadas

|Clase de la IP |Desde-Hasta |
|----------|:----------:|
|Clase A |10.0.0.0 a 10.255.255.255 |
|Clase B |172.16.0.0 a 172.31.255.255 |
|Clase C |192.168.0.0 a 192.168.255.255 |

#### Que IPs se utilizan para servidores y cuales IPs para puertas de enlace. 

Las IPs que se utilizan para los servidorrs son IPs grandes, por ejemplo __192.168.16.200__ o __192.168.16.254__ ya que se considera una IP alta de la 200 a la 254, todo lo que entre en ese rango lo consideraremos una IP alta.

![U+200E](https://github.com/JxviHub/SMX2-M12.2-Sintesi-Fase4-A06-Javier-Izan-Gabriel/blob/main/Fotoservidor.png "imagen")

Las IPs que utilizamos para las puertas de enlace son las mas bajas, es decir las que asignaremos al ruter, por ejemplo si el ruter tiene una ip __192.168.16.1__ nuestra puerta de enlace sear esa.

#### VERSIONES ANTERIORES A LA 17.10

Utilizaremos el comando **"nano \etc\network\interfaces"** para entrar en la configuracion de las redes.
El comando **nano** se utiliza para entrar o modificar el archivo.


Para hacer que nos asignen una IP dinamica por DHCP, escribiremos lo siguiente en el fichero **interfaces**.
- auto enp0s3
- iface enp0s3 inet dhcp

[(E+200U)"imagen"]

Para asignar una IP estatica , escribiremos lo sigueiente en el fichero **interfaces**.
- auto enp0s3
- iface enp0s3 inet static
- address 192.255.255.0
- netmask 255.255.255.0
- gateway 192.168.1.1

Aqui hos dejamos una representación de como queda todo en la terminal.

[(E+200U)"imagen"]

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

[(E+200U)"imagen"]

#### VERSIONES POSTERIORES A LA 17.10

Estas versiones utilizan netplan.
 
Para encontrar el fichero en el cual debemos modificar la IP, tendremos que escribir el siguiente comando **/etc/netplan/****.yaml**.

En caso de que no exista el fichero usaremos el comando **sudo netplan generate** para generar un fichero.

Para establecer una IP estatica deberemos seguir los siguientes pasos:
- dhcp4 : no (En caso de que usemos IPv6 lo pondremos en el dhcp6)
- address 192.255.255.0/24
- gateway 192.168.1.1

Despues de establecer la ip con la mascara y el gateway, establecermos el servidor, en este caso deberemos poner el nombre y la IP:
- Google: 8.8.8.8

Para apolicar todos estos cambios usaremos el comando **sudo netplan apply**

Aqui hos dejamos una representación de como queda todo en la terminal.

[(E+200U)"imagen"]

Para establecer una IP dinamica simplemente tendremos que poner "yes" en el apartado del dhcp y escribir el comando **sudo netplan apply** para aplicar los cambios, tras hacer esto se nos asignara una IP automaticamente.

Aqui hos dejamos una representación de como queda todo en la terminal.

[(E+200U)"imagen"]