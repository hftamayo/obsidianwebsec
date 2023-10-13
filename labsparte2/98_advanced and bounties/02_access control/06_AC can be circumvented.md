
![[Pasted image 20231013134525.png]]

Recon:

![[Pasted image 20231013134609.png]]

![[Pasted image 20231013134623.png]]

probando wiener : peter

![[Pasted image 20231013134706.png]]

en los detalles de los productos no hay ninguna otra opcion activa, asi mismo, accediendo desde aca al Admin Panel siempre recibo "access denied"


cookies disponibles:

![[Pasted image 20231013134828.png]]

Verificando los requests dentro de Burp:

![[Pasted image 20231013135503.png]]

parece que GET /admin es el idoneo a alcanzar:

![[Pasted image 20231013135528.png]]

Estas son las modificaciones que hice (incluyendo el X-Original-URL):

![[Pasted image 20231013140000.png]]

el output obtenido es este:

![[Pasted image 20231013140032.png]]


![[Pasted image 20231013140017.png]]



tratando de usar el intercept para que las modificaicones sea hechas en el navegador:

![[Pasted image 20231013140135.png]]

![[Pasted image 20231013140159.png]]

haciendo click recibo: 

![[Pasted image 20231013140235.png]]
entonces tengo que capturar el get request y hacer la modificacion

capturando el click en carlos:

![[Pasted image 20231013140404.png]]

el request ya modificado:

![[Pasted image 20231013140457.png]]
Pero obtuve que hay un missing parameter -aun y cuando inclui a carlos en el request

el cambio en el request es asi:

![[Pasted image 20231013141012.png]]

aunque esta bien el request, en el intercept me volvio a generar un Access Denied, entonces lo hice en el Repeater y si obtuve un 302:

![[Pasted image 20231013141156.png]]

![[Pasted image 20231013141205.png]]

![[Pasted image 20231013141214.png]]


Url consultado:  https://infosecwriteups.com/begineers-crash-course-for-finding-access-control-vulnerabilities-in-the-web-apps-part-2-ce38eabfb81a