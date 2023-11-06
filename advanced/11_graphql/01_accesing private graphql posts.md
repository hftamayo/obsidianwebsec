![[Pasted image 20230809183003.png]]

este lab requiere la extension inQL que a su vez requiere de jython, favor usar estas refs:

https://burpsuite.guide/runtimes/python/

con el intercept en off inicio el lab y le doy click a un post cualquiera:

![[Pasted image 20230809185758.png]]


![[Pasted image 20230809185817.png]]

![[Pasted image 20230809185901.png]]

![[Pasted image 20230809185937.png]]

			notese que tengo 2 grapql, favor enviar al repeater el segundo que es el que corresponde al postid:

![[Pasted image 20230809190354.png]]

![[Pasted image 20230809190419.png]]

![[Pasted image 20230809190449.png]]

hoy me regreso al proxy history y copio el url del endpoint que acabo de enviar al repeater:

![[Pasted image 20230809190608.png]]

luego me voy a inQL Scanner y pego el link y presiono el boton load, en el resultado puedo desplegarlo dandole doble click:

![[Pasted image 20230809190753.png]]

![[Pasted image 20230809190834.png]]

el getAllBlogPosts lo mando al repeater:

![[Pasted image 20230809190927.png]]

click en la pestana inQL y le doy send:

![[Pasted image 20230809191022.png]]

![[Pasted image 20230809191051.png]]

veo que hay una variable que se llama postPassword en null.

hoy me regreso al inQL Scanner y mando al repeater el segundo query:

![[Pasted image 20230809191155.png]]

![[Pasted image 20230809191218.png]]

en lugar de 1334 le pongo 5 que es el post que yo tengo seleccionado:

![[Pasted image 20230809191322.png]]

en los repeater, el primer valido copio la variale y la pego en el grapql #1:

![[Pasted image 20230809191456.png]]

![[Pasted image 20230809191600.png]]

de ahi cambio al id: 3 en el parametro de la funcion y ahi si jala el password:

![[Pasted image 20230809191714.png]]

"postPassword": "v2zp4rjkc809f9biylkalnhg07agw157"

![[Pasted image 20230809191757.png]]

![[Pasted image 20230809191810.png]]



