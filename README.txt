Escenario 2
Cada cierto tiempo un fichero es copiado a un SFTP, se desea implementar una solución que haga lo siguiente:
1. Lea el contenido del fichero en el FTP que existe en ese momento y usando la funcionalidad batch extraiga dicho contenido.
2. Por cada registro del fichero debe cifrarlo usando  AES 256  con el componente crypto de Mule. Cada registro cifrado debe ser almacenado en un fichero .txt.
3. Cuando se escriba el fichero cifrado con el registro en el sftp notificar a otro servicio de Mules que puede ir a procesar el fichero para descifrarlo y meter los registros en una BD. (esto con colas o servicios)
4. Luego se debe enviar un mensaje a una cola previamente definida, en ese mensaje debe ir un id de la transacción y el path del fichero en el FTP para que otro componente lo lea, tome el mensaje, obtenga el path del fichero, lo desencriptara, y el registro obtenido será persistido en BD.
5. Si algún registro no se puede procesar en el componente 1 el flujo no se debe detener, se debe continuar y dicho registro se almacena en un fichero que tendrá todos los registros no procesados.
6. Cuando un fichero es procesado completamente se debe eliminar de la carpeta donde esté y será movido a otra carpeta.
Cosas que deben considerar:

Cofiguracion del FTP: RebexTinySftpServer-Binaries-Latest v1.0.13
Server IP:              192.168.43.118 
Server port:            22 
User:          	        tester
Password:      	        password
User public keys:   	(disabled) 
User root directory: 	Z:\cursos\mule\RebexTinySftpServer-Binaries-Latest\data
Configuration file: 	Z:\cursos\mule\RebexTinySftpServer-Binaries-Latest\RebexTinySftpServer.exe.Config
