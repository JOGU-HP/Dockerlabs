Resolucion de la maquina BorazuwarahCTF

Primero se despliega la maquina, se hace un ping para comprobar la conectividad con la maquina vulnerable
![conect](https://github.com/JOGU-HP/Dockerlabs/blob/0485541056fc2f46478c1346f59fae1e43ac2a5a/maquinas_muy_faciles/BorazuwarahCTF/ping.png)

Ahora que hay comunicacion entre la maquina atacante y la atacada, procedo a realizar un escaneo de puertos
![scan](https://github.com/JOGU-HP/Dockerlabs/blob/0485541056fc2f46478c1346f59fae1e43ac2a5a/maquinas_muy_faciles/BorazuwarahCTF/scan.png)


Al analizar los puertos abiertos, veo el puerto 22 y 80, indicando que existe una pagina web, asi que entro a la pagina con la IP en el navegador

Entro en la pagina con la IP y lo unico que encuentro es una imagen, realizo una inspeccion del codigo fuente para ver si encuentro credenciales o pistas para continuar, pero no encuentro nada
![page](https://github.com/JOGU-HP/Dockerlabs/blob/0485541056fc2f46478c1346f59fae1e43ac2a5a/maquinas_muy_faciles/BorazuwarahCTF/page.png)

Invetigo sobre imagenes y encuentro que puedo realizar un escaneo par poder ver metadatos y con ello encontrar un posible usuario o contrasena, con la herramienta exiftool, por lo que descargo la imagen y ejecuto exiftool image.jpeg para observar metadatos
![metadatos](https://github.com/JOGU-HP/Dockerlabs/blob/0485541056fc2f46478c1346f59fae1e43ac2a5a/maquinas_muy_faciles/BorazuwarahCTF/use_exiftool.png)

Despues de usar la herramienta, encuentro al usuario pero no la contrasena, asi que uso hydra con el nombre de usuario que encontre y el diccionario rockyou.txt para ver si encuentro alguna contrasena

Encuentro la contrasena y procedo con la conexion via ssh
![hydra](https://github.com/JOGU-HP/Dockerlabs/blob/0485541056fc2f46478c1346f59fae1e43ac2a5a/maquinas_muy_faciles/BorazuwarahCTF/ataque_hydra.png)


Ahora, escribo sudo -l para ver si es necesario algun archivo para ser root, sin embargo el archivo necesario es un archivo bash asi que solo ejecuto sudo su, escribo la contrasena que econtre con anterioridad y ahora si me convierto en root
![root](https://github.com/JOGU-HP/Dockerlabs/blob/0485541056fc2f46478c1346f59fae1e43ac2a5a/maquinas_muy_faciles/BorazuwarahCTF/root.png)
