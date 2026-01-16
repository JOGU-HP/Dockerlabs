Resolucion de la maquina trust en DockerLabs

Se despliega la maquina trust con ayuda de bash como usuario root realizando un ping y verificar la conexion
![ping](https://github.com/JOGU-HP/Dockerlabs/blob/0d8a11a3040040e026ab7b16b382995b373f4523/maquinas_muy_faciles/images/ping%20(trust).png)

Una vez que se realiza el ping correctamente comienzo con un escaneo de puertos con nmap y la sintaxis nmap -p- -sS -sC --min-rate 1000 <IP>
![scan](https://github.com/JOGU-HP/Dockerlabs/blob/1782e536e084414ee43b162e43c039c58124d879/maquinas_muy_faciles/images/escaneo%20(trust).png)

Observo que hay 2 puertos abiertos (80 y 22) significa que de por medio hay una pagina web, asi que en el navegador, se busca la pagina con la IP otorgada
aunque no me dice nada aun viendo su codigo fuente
![page](https://github.com/JOGU-HP/Dockerlabs/blob/7d44e2f8c2cd3214d3f01ac45d40aa70d9c005f3/maquinas_muy_faciles/images/pagina%20(trus).png)

Realizo un escaneo con gobuster para encontrar directorios ocultos y encuentro un archivo .php llamado secret
![gobuster](https://github.com/JOGU-HP/Dockerlabs/blob/7d44e2f8c2cd3214d3f01ac45d40aa70d9c005f3/maquinas_muy_faciles/images/escaneo_gobuster%20(trust).png)

Al escribir 172.18.0.2/secret.php/ me lleva a otra pagina, que dice Hola Mario, posiblemente una credencial de Usuario
![secret](https://github.com/JOGU-HP/Dockerlabs/blob/7d44e2f8c2cd3214d3f01ac45d40aa70d9c005f3/maquinas_muy_faciles/images/Screenshot_2026-01-15_16_12_05.png)

Ahora, realizo un ataque con Hydra para encontrar la contrasena y poder conectarme por ssh
![hydra](https://github.com/JOGU-HP/Dockerlabs/blob/7d44e2f8c2cd3214d3f01ac45d40aa70d9c005f3/maquinas_muy_faciles/images/ataque_hydra%20(trust).png)

Con el usuario y contrasena obtenidos, me conecto via ssh para poder convertirme en root, escribiendo el comando sudo -l
![sudo](https://github.com/JOGU-HP/Dockerlabs/blob/5d5566a86e41ebd3b6a2b9ece4800c142ce4fd99/maquinas_muy_faciles/images/archivo_root%20(trust).png)

Me pide permisos para ver el contenido de archivos que pueden hacer root a un usuario, que al escribirla, veo que para poder ser root se debe
ejecutar un archivo vim
![conexion](https://github.com/JOGU-HP/Dockerlabs/blob/5d5566a86e41ebd3b6a2b9ece4800c142ce4fd99/maquinas_muy_faciles/images/conexion_ssh%20(trust).png)

En GTFOBins encuentro el arhcivo vim para ser root y escribo sudo vim mario -c ':!/bin/sh'
![attack](https://github.com/JOGU-HP/Dockerlabs/blob/5d5566a86e41ebd3b6a2b9ece4800c142ce4fd99/maquinas_muy_faciles/images/GTFOBins%20Vim.png)

Ejecutado el comando correctamente, escribo whoami y porfin soy root
![root](https://github.com/JOGU-HP/Dockerlabs/blob/5d5566a86e41ebd3b6a2b9ece4800c142ce4fd99/maquinas_muy_faciles/images/ejecucion_archivo_vim%20(trust).png)
