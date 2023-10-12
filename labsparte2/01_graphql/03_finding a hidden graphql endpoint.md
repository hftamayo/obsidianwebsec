![[Pasted image 20230818135411.png]]

![[Pasted image 20230818135615.png]]

el root lo envio al intrudier

![[Pasted image 20230818135645.png]]

agrego en el root un payload:

![[Pasted image 20230818135746.png]]

en este paso BugBounty España usa un diccionario para tratar de hacer fuerza bruta pero no lo encuentra , este diccionario es de él por tanto no tengo como ejecutar este paso, sin embargo, no le da bola, unicamente obtuvo un error 400, tratando de replicar el diccionario:


![[Pasted image 20230818140321.png]]

![[Pasted image 20230818140413.png]]

la siguiente opcion debe estar desactivada antes de ejecutar el ataque:

![[Pasted image 20230818140445.png]]

![[Pasted image 20230818140537.png]]

el error 400 nos indica que tratando de formar bien un endpoint podemos tener un resultado. Enviandolo al Repeater:

![[Pasted image 20230818140620.png]]


usando el siguiente payload que esta sugerido en la lectura de la leccion sobre graphql:

![[Pasted image 20230818140821.png]]

GET /graphql?query=query%7B__schema%0A%7BqueryType%7Bname%7D%7D%7D

![[Pasted image 20230818141006.png]]

![[Pasted image 20230818141017.png]]

probando este payload:
query={getUser(id:1){id%0d%0ausername}}

![[Pasted image 20230818141218.png]]

![[Pasted image 20230818141232.png]]

esta traza la enviamos al intruder y el id será el payload:

![[Pasted image 20230818141339.png]]

los datos del ataque son estos:

![[Pasted image 20230818141423.png]]

aparece este warning pero presiono ignore:

![[Pasted image 20230818141450.png]]

a pesar del warning funciona bien el ataque y hit por hit puedo ir viendo el resultado:

![[Pasted image 20230818141605.png]]

![[Pasted image 20230818141624.png]]


![[Pasted image 20230818141651.png]]

ya que encontramos los datos de la cuenta de Carlos mando esta traza al repeater y usaré este payload:

![[Pasted image 20230818141803.png]]

mutation{deleteOrganizationUser(input:{id:3}){user{id}}}

![[Pasted image 20230818142230.png]]

![[Pasted image 20230818142240.png]]



![[Pasted image 20230818142201.png]]

