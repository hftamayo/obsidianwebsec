

![[Pasted image 20230830132141.png]]

![[Pasted image 20230830132158.png]]
el mambo es disparar un request, imagino que se puede si es POST o GET:

![[Pasted image 20230830132232.png]]

![[Pasted image 20230830132336.png]]

revise ambos request y me recorde que el SSRF lo ejecutaron en el POST:

![[Pasted image 20230830132548.png]]

el payload para decodificarlo le doy click derecho y la mando al decoder, sombreo toda la cadena y selecciono la opcion URL:

![[Pasted image 20230830132905.png]]

http://stock.weliketoshop.net:8080/product/stock/check?productId=1&storeId=3

Entonces el chiste del SSRF es tratar de hacer un hit a un asset local desde un recurso publicado en la web o interno, asi que me voy al repeater y cambio:

![[Pasted image 20230830133019.png]]

![[Pasted image 20230830133056.png]]

Ctrl+U para encodearlo:

![[Pasted image 20230830133128.png]]

![[Pasted image 20230830133158.png]]

![[Pasted image 20230830133320.png]]

esto lo estoy viendo en el Render, ahora para poder resolver el lab debo interceptar el request y hacer el cambio, enciendo el intercept primero y hago el request nuevamente:

![[Pasted image 20230830133604.png]]


![[Pasted image 20230830133639.png]]

![[Pasted image 20230830133717.png]]

Al intentar borrarlo:

![[Pasted image 20230830133758.png]]


pense que dando click en el link iba a funcionar, leyendo en el repeater en el HTML tenemos el endpoint:

![[Pasted image 20230830134354.png]]

que sucede si lo pongo en la barra de direcciones:

![[Pasted image 20230830134444.png]]

pasa lo mismo, si modifico el POST en el repeater:

![[Pasted image 20230830134535.png]]

aca me quede sin saber que hacer, tuve que ver el video de Rana Khalil y ahi me di cuenta que en el payload puedo enviar acceso a cualquier otro endpoint, de manera que la solucion es:

![[Pasted image 20230830135032.png]]

stockApi=http%3a//localhost/admin/delete?username=carlos

![[Pasted image 20230830135056.png]]


por que motivo no podía eliminar la cuenta desde el navegador o haciendo click a un link? aca lo explica la leccion:

![[Pasted image 20230830135422.png]]

![[Pasted image 20230830135538.png]]

