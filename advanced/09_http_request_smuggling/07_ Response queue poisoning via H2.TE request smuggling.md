![[Pasted image 20230720181120.png]]

![[Pasted image 20230720182618.png]]

![[Pasted image 20230720182652.png]]

![[Pasted image 20230720182712.png]]

cambio a request y version 2, tambien limpio:

![[Pasted image 20230720182758.png]]

en el menu del repeater activo la opcion: Allow HTTP/2 ALPN override y desactivo la content length. luego agrego este payload:

![[Pasted image 20230720182957.png]]

![[Pasted image 20230720183016.png]]

![[Pasted image 20230720183036.png]]


![[Pasted image 20230720183050.png]]

tiene que darme un 302 para que sea la cookie del admin:

![[Pasted image 20230720183429.png]]

![[Pasted image 20230720183457.png]]

El payload que es valido para Bounty Espana es este:

![[Pasted image 20230720184005.png]]

leyendo la solucion oficial dice que al final del host debe tener estos caracteres: \r\n\r\n

agregando:

![[Pasted image 20230720184603.png]]

probando (le hice varias veces, como 5 veces hasta que aparecio):

![[Pasted image 20230720184720.png]]

![[Pasted image 20230720184734.png]]

session=f6S8kElLlS1OKZ4Rf3Vj9Dz0F2PXNjbJ

esta cookie la sustituyo en el lab:

![[Pasted image 20230720184814.png]]

sustituyendo:


![[Pasted image 20230720184857.png]]

refresco la pagina y aparece:

![[Pasted image 20230720184930.png]]

![[Pasted image 20230720185006.png]]

![[Pasted image 20230720185028.png]]