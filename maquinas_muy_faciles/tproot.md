Vulnerando la maquina Tproot en DockerLabs

Se despliega la maquina y se realiza un ping para comprobar la conxion entre la maquina atacante y vulnerable
![ping](https://github.com/JOGU-HP/Dockerlabs/blob/504e99f35b6098dbf4d0e668c87996b94da2d444/maquinas_muy_faciles/images/Tproot/ping.png)


Comprobada la conexion, se realiza un escaneo de puertos con nmap, observando el puerto 21 y 80 abierto
![scan](https://github.com/JOGU-HP/Dockerlabs/blob/504e99f35b6098dbf4d0e668c87996b94da2d444/maquinas_muy_faciles/images/Tproot/scan.png)


Como no existe el puerto 22 para hacer una conexion via ssh, pero al observar que el puerto 21 tiene vsftpd con la version 2.3.4 determino que es mejor usar Metasploit

Una vez ejecutado Metasploit, escribo search vsftpd 2.3.4 para buscar un exploit y utilizarlo
![search](https://github.com/JOGU-HP/Dockerlabs/blob/504e99f35b6098dbf4d0e668c87996b94da2d444/maquinas_muy_faciles/images/Tproot/busqueda_exploit.png)

Al encontrar el exploit, escribo use 0 para usar el exploit encontrado, seguido de show options para observar los parametros necearios y usar el payload
![options](https://github.com/JOGU-HP/Dockerlabs/blob/504e99f35b6098dbf4d0e668c87996b94da2d444/maquinas_muy_faciles/images/Tproot/parametros.png)

Veo que es necesario RHOSTS asi que escribo set RHOSTS <IP> para usar el payload

Una vez configurado el RHOSTS escribo run para poder usar el payload, que encuentra una shell y al escribir whoami veo que soy root
![conf](https://github.com/JOGU-HP/Dockerlabs/blob/504e99f35b6098dbf4d0e668c87996b94da2d444/maquinas_muy_faciles/images/Tproot/exploit.png)
