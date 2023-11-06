![[Pasted image 20230830141954.png]]

![[Pasted image 20230830142032.png]]

![[Pasted image 20230830142056.png]]

este es el payload: http://192.168.0.1:8080/product/stock/check?productId=3&storeId=2

cayendo en la tentaction de meter ips al azar:

![[Pasted image 20230830142425.png]]

quizas debo comprender cómo poder explotar la vuln pues es seguro que se requiere aprovechar el acceso a los endpoints.

Antes de seguir vi este video: https://www.youtube.com/watch?v=Ku6CK3Aes8Y

Inicialmente tenia la presuncion que tenia que usar el Burp Intruder pero por algun motivo no lo hice, el miedo que da en afectar algo parece ser que es clave vencerlo para explorar las plataformas.

Enviando el request al Intruder, seteando un payload en el ultimo octeto de la IP y haciendo un ataque de numeros del 1 al 255:

![[Pasted image 20230831134825.png]]

![[Pasted image 20230831134852.png]]

![[Pasted image 20230831135000.png]]

el status 404 significa que ese asset no existe, sin embargo nos damos cuenta que esa ip es interna y esta encendida, aca el truco seria tratar de encontrar que endpoint es, se infiere en los laboratorios de PSwigger que es admin:

![[Pasted image 20230831135143.png]]

decodificando el payload:

![[Pasted image 20230831135327.png]]

![[Pasted image 20230831135409.png]]

![[Pasted image 20230831135421.png]]

....

![[Pasted image 20230831135439.png]]

actualizando el payload:

![[Pasted image 20230831135509.png]]

![[Pasted image 20230831135520.png]]

