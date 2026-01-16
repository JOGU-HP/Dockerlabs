Ataque a la maquina myfirsthacking en DockerLabs

Se despliega la maquina y se comprueba la conectividad con un ping -c1 <IP>
![despliegue](https://github.com/JOGU-HP/Dockerlabs/blob/f8e90ea0013aed261f454d50a5f56ed4fca9698e/maquinas_muy_faciles/images/myfirsthacking/ping%20(myfh).png)

Procedo a realizar un escaneo de puertos
![despliegue](https://github.com/JOGU-HP/Dockerlabs/blob/f8e90ea0013aed261f454d50a5f56ed4fca9698e/maquinas_muy_faciles/images/myfirsthacking/scan.png)

Veo que solo existe un puerto abierto, el puerto 21 que es una puerta trasera, asi que procedo a buscar un exploit en Metasploit con mfsconsole y escribiendo search vsftpd 2.3.4, encontrando un exploit
![search_exploit](https://github.com/JOGU-HP/Dockerlabs/blob/f8e90ea0013aed261f454d50a5f56ed4fca9698e/maquinas_muy_faciles/images/myfirsthacking/busqueda_exploit.png)

Ahora que he encontrado un exploit escribo use 0 para usar el exploit encontrado, seguido de show options para ver que parametros son necesarios para ejecutar el exploit
![use](https://github.com/JOGU-HP/Dockerlabs/blob/f8e90ea0013aed261f454d50a5f56ed4fca9698e/maquinas_muy_faciles/images/myfirsthacking/options_exploit.png)

Veo que es necesario un RHOSTS asi que pongo la IP de la victima y con ello usar el exploit
(RHOSTS significa servidor remoto)

Una vez configurado el RHOSTS procedo a usar run para ejecutar el exploit y encuentra una shell

Escribo whoami y soy root

![exploit](https://github.com/JOGU-HP/Dockerlabs/blob/f8e90ea0013aed261f454d50a5f56ed4fca9698e/maquinas_muy_faciles/images/myfirsthacking/ejecucion_payload.png)
