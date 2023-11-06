![[Pasted image 20230808181834.png]]

payload:

esta sera la variable a agregar en el header:

foo:

bar\r\n
\r\n
GET /x HTTP/1.1\r\n
Host: id del lab


refreco la primera peticion GET del lab:

![[Pasted image 20230808182314.png]]

![[Pasted image 20230808182335.png]]

![[Pasted image 20230808182357.png]]

cambio a la version 2 y busco conectarme a un endpoint que no existe:

![[Pasted image 20230808182443.png]]

luego le doy en el request header y agrego el payload en foo:

![[Pasted image 20230808182550.png]]

...

![[Pasted image 20230808182802.png]]

despues de darle add empiezo a obtener 404:

![[Pasted image 20230808182858.png]]

y hay que enviar sends de manera pausadas - como 10 segundos entre ellos- hasta obtener el token del admin:

![[Pasted image 20230808183401.png]]

Location: /my-account?id=administrator
Set-Cookie: session=wugQsxe5or5xTa1NTNQ0SX1NlfA6n4KI; 

trato de acceder al endpoint admin:

![[Pasted image 20230808183515.png]]

![[Pasted image 20230808183532.png]]

esta vez enciendo el intercept y cambio la cookie session:

antes:

![[Pasted image 20230808183654.png]]

despues:

![[Pasted image 20230808183734.png]]

despues de darle forward:

![[Pasted image 20230808183801.png]]

sin apagar el intercep le doy delete a Carlos y vuelvo a actualizar la cookie:

antes:

![[Pasted image 20230808183912.png]]

despues:

![[Pasted image 20230808183949.png]]

![[Pasted image 20230808184012.png]]