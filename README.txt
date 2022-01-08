Escenario 2, ya esto se va poniendo interesante:


Cada cierto tiempo un fichero es copiado a un SFTP, se desea implementar una solución que haga lo siguiente:
1. Lea el contenido del fichero en el FTP que existe en ese momento y usando la funcionalidad batch extraiga dicho contenido.
2. Por cada registro del fichero debe cifrarlo usando  AES 256  con el componente crypto de Mule. Cada registro cifrado debe ser almacenado en un fichero .txt.
3. Cuando se escriba el fichero cifrado con el registro en el sftp notificar a otro servicio de Mules que puede ir a procesar el fichero para descifrarlo y meter los registros en una BD. (esto con colas o servicios)
4. El servicio que almacena en BD debe ser expuesto como se explica en el punto 3 a través de una cola o a través de un endpoint REST o SOAP, queda a su elección.
4. En caso de error hacer tratamiento de errores para cuando un registro no se pueda procesar, generar un fichero de errores en el sftp. Y  después ese .txt que no tiene que estar cifrado, comprimir a .zip y escribirlo en sftp.

Cosas que deben considerar:
1. La estructura del fichero con los registros queda a discreción de ustedes, preferiblemente que contenga un registro de varios datos en texto plano. Pueden ser en formado json, en xml o pura cadena de texto con tabulaciones o separadores.
2. El diseño de la BD y el servicio que almacena en ella debe estar en correspondencia con la estructura de los registros.

Cualquier duda me la tiran por aquí y así la aclaramos entre todos.

Los que falten por el repo, lo sigo solicitando, no pierdan el chance.
