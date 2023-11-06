
![[Pasted image 20230914143023.png]]


![[Pasted image 20230918143705.png]]

![[Pasted image 20230918143727.png]]

no hay opcion de hacer request al backend (consultar el stock), entonces queda navegar y ver que hay en el header:

![[Pasted image 20230918144610.png]]

![[Pasted image 20230918144636.png]]

el dato en comun es el valor de Referer, si aca trato de poner un burp collaborator y verifico si tengo respuesta, por favor no eliminar el protocolo https, en efecto, la primrea vez sólo pegue la direccion del burp collaborator y no me funcionaba:

![[Pasted image 20230918145502.png]]

![[Pasted image 20230918145517.png]]

![[Pasted image 20230918145528.png]]

la idea aca sería ver si puedo ejecutar un RCE.