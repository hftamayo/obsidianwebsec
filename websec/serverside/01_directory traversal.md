

## Recomendaciones para el desarrollador

1. sanitizar o validar la entrada del parametro filename
2. todas las operaciones de la API debe seguir el principio de Least Privilege
3. Uno de los principales riesgos de un path traversal es subir una reverse shell, secuestrar llaves SSH
4. strict validation of user input: Java: getCanonicalPath, PHP: realpath
5. Aunque hay contramedidas para stripear los pattern mas comunes siempre pueden saltarse, favor verificar: https://www.redsentry.com/blog/exploring-the-dangers-of-path-traversal-vulnerabilities-in-web-applications


## Resolucion de los labs de port swigger:

```

- Lab01: usar un relative path con saltos hacia atras (3 creo)

- Lab02: usar un absolute path

- Lab03: este lab tenia medidas de proteccion (strips) pero aca se aprende los distintos bypass:
	- usar ....//....//.....//+el nombre del archivo
	- usar url encoding: filename=%2e%2e%2e%2e%2f%2f%2e%2e%2e%2e%2f%2f%2e%2e%2e%2e%2f%2fetc%2fpasswd

filename=%u002e%u002e%u002e%u002e%u2215%u2215%u002e%u002e%u002e%u002e%u2215%u2215%u002e%u002e%u002e%u002e%u2215%u2215etc%u2215passwd

- Lab04: utiliza bloqueadores que se parecen a path traversal, luego ejecuta un URL decode del input antes de usarlo

The whole **“_traversal sequences stripped with superfluous URL-decode_”** means that the input will be decoded using the URL decoding scheme, and if any path traversal sequence is found, that will be stripped away.


```