![[Pasted image 20231009135214.png]]


![[Pasted image 20231009135256.png]]

![[Pasted image 20231009135318.png]]

![[Pasted image 20231009135335.png]]


![[Pasted image 20231009135432.png]]

Descripcion sobre cómo trate de resolver el lab:

1. hice un recon de todo el sitio, por ejemplo, vi como se obtiene datos de un producto, trate con default creds y luego adivinando con el tipico /admin
2. luego agarre un GET request cualquiera y trate de entender el contenido de este, incluso intenté modificar el Referer pero no tuve mayor impacto:

este es el original:

![[Pasted image 20231009140655.png]]

y esta la modificacion:

![[Pasted image 20231009140720.png]]

aunque obtuve un 200 pero no significa nada

3. Esta es la parte importante porque la onda es no perder la calma, no desesperarse por no leer la solucion o buscar writeups, de todos modos, esto debe ser una practica para encontrar bounties.
4.  leí nuevamente la parte teorica y encontré que a veces hay leaks en el robots.txt


![[Pasted image 20231009141033.png]]

5. entonces traté de leer un robots mediante un GET request:

![[Pasted image 20231009141111.png]]


6. intentando acceder al recurso administrator-panel:


![[Pasted image 20231009141155.png]]

![[Pasted image 20231009141213.png]]