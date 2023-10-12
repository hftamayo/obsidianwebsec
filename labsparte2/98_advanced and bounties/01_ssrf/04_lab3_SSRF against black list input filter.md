![[Pasted image 20230831135941.png]]

![[Pasted image 20230831141407.png]]

![[Pasted image 20230831141432.png]]

![[Pasted image 20230831141516.png]]

![[Pasted image 20230831141604.png]]

si mando este request sin encriptar me genera un status 400:

![[Pasted image 20230831141738.png]]

probando hacer un request al localhost (el payload puede estar encriptado o no):

![[Pasted image 20230831141845.png]]

hice pruebas con los payloads decimal, octal y con los local CIDR de PayloadsAllTheThings pero nada, aca un ejemplo:

![[Pasted image 20230831142724.png]]

Nuevamente probando un par de payloads para black list encontrados aca: https://github.com/0x221b/Wordlists/blob/master/Attacks/SSRF/Blacklist-bypass.txt y ninguno funciono porque estaba probando bypasear el localhost y el endpoint a la vez:

![[Pasted image 20230911135833.png]]


Revisando en esta pagina encontré una explicacion bien chiva: https://infinitelogins.com/tag/ssrf/

* Probando si el localhost es alcanzable

![[Pasted image 20230911140654.png]]

![[Pasted image 20230911140722.png]]


* Probando bypasear el localhost

![[Pasted image 20230911140750.png]]

![[Pasted image 20230911141231.png]]

* Probando con el endpoint admin:

![[Pasted image 20230911141259.png]]

* Encodear el endpoint admin:

![[Pasted image 20230911141524.png]]

![[Pasted image 20230911141513.png]]



![[Pasted image 20230911141630.png]]


* Si encodeo incluso toda la cadena siempre obtengo el error, por tanto, la tecnica a usar se sugiere que sea la de Double URL Encoding el cual es poner al inicio del endpoint el caracter %25 y encodear la primera letra, luego queda a criterio encodear el resto del nombre del endpoint:

![[Pasted image 20230911142153.png]]

![[Pasted image 20230911142235.png]]

* Borrar la cuenta de carlos:


![[Pasted image 20230911142326.png]]

![[Pasted image 20230911142345.png]]



