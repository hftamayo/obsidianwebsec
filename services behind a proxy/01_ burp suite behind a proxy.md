
1. abrir un tunel con un equipo que tenga salida a internet: ssh -D 5555 "cuenta"@"host"

![[Pasted image 20231006145224.png]]


2. no necesito tener configurado ni en mi equipo ni en el host que servirá de puente la reserva del puerto 5555, de hecho, basta con que este libre en ambos y tambien puede ser uno distinto


3. como una manera de validar si la conexion se estableció y tiene navegacion puedo seguir el siguiente paso desde mi equipo:

![[Pasted image 20231006145332.png]]


4.  Configuro este proxy en mi burp, la ruta es: Pantalla principal de Burp -> User Options-> SOCKS Proxy:

![[Pasted image 20231006150108.png]]

![[Pasted image 20231006150120.png]]

finalmente esto lo configuro en el foxyProxy de mi navegador:

![[Pasted image 20231006150217.png]]


5. 