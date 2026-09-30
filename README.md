Informe de Auditoría de Red Wi-Fi Insegura

Introducción

Las redes Wi-Fi públicas pueden presentar diversos riesgos de seguridad, ya que diversos usuarios están conectados a una misma infraestructura de red. Un atacante conectado a la misma red podría intentar analizar el tráfico y realizar ataques. 

Para esta práctica se analizó el sitio web http://neverssl.com, utilizando las herramientas de desarrollador del navegador, con el objetivo de observar las características de una conexión HTTP y comprender que información puede quedar expuesta. 


Parte 1 - Exploración
	1. Se ingresó al sitio web http://neverssl.com y se abrió el modo de desarrollador del navegador, 	presionando F12.
	2. Seleccionando la pestaña Network
	3. Se recargó la página.
	4. Se seleccionó la primera solicitud realizada.
	5. Observa los siguientes dados:
		- URL solicitada: http://neverssl.com
		- Método HTTP: GET
		- Host: innermajesticsilvermorning.neverssl.com
		- Protocolo utilizado: HTTP (versión 1.1)
		- Headers enviados: 
		{
		"requestHeaders": {
		"headers": [
			{
				"name": "Accept",
				"value": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8"
			},
			{
				"name": "Accept-Encoding",
				"value": "gzip, deflate, br, zstd"
			},
			{
				"name": "Accept-Language",
				"value": "en-US,en;q=0.5"
			},
			{
				"name": "Connection",
				"value": "keep-alive"
			},
			{
				"name": "Host",
				"value": "innermajesticsilvermorning.neverssl.com"
			},
			{
				"name": "Priority",
				"value": "u=0, i"
			},
			{
				"name": "Referer",
				"value": "http://neverssl.com/"
			},
			{
				"name": "Sec-Fetch-Dest",
				"value": "document"
			},
			{
				"name": "Sec-Fetch-Mode",
				"value": "navigate"
			},
			{
				"name": "Sec-Fetch-Site",
				"value": "cross-site"
			},
			{
				"name": "Upgrade-Insecure-Requests",
				"value": "1"
			},
			{
				"name": "User-Agent",
				"value": "Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0"
			}
			]
		}
		}



Parte 2 - Analysis
	1. ¿Qué protocolo utiliza el sitio?
		El sitio analizado (neverssl.com) utiliza el protocolo HTTP. 
		HTTP no proporciona cifrado de extremo a extremo para el contenido de la comunicación. Dependiendo 		del tráfico y de las condiciones de red, determinados datos pueden ser observados o modificados 		por un ataque que consiga interceptar la comunicación.
		
		En cambio HTTPS protege la comunicación mediante cifrado y autenticación del servidor.
		En HTTP, la comunicación no tiene cifrado de TLS
		En HTTPS, la comunicación es protegida mediante TLS

	2. ¿Qué información puede observarse durante la solicitud?
		Durante el análisis de la solicitud HTTP pueden observarse diferentes elementos técnicos, entre 		ellos:

			Host
			Indica el servidor o dominio al que se realiza la solicitud.

			Ejemplo: neverssl.com

			URL
			Indica el recurso que el navegador está intentando solicitar.


			GET
			El método GET se utiliza habitualmente para solicitar información a un servidor.


			User-Agent
			Permite identificar características del cliente que realiza la solicitud, como el navegador e información relacionada con el sistema operativo.


	3. ¿Qué riesgos existen al navegar mediante HTTP desde una red Wi-Fi pública?
			Utilizar HTTP desde una red Wi-Fi pública presenta riesgos porque la comunicación no está protegida mediante TLS.

			Un atacante que consiga interceptar el tráfico podría potencialmente observar información transmitida mediante HTTP.

			Ejemplos de riesgos:

			Exposición del contenido de las comunicaciones HTTP.
			Exposición de URLs y recursos solicitados.
			Identificación de los sitios visitados.
			Posibilidad de manipulación del tráfico.
			Exposición de información que una aplicación transmita sin cifrado.
		

	4. ¿Cómo cambiaría este escenario utilizando una VPN?
		Cifrado:
		Protege el contenido del tráfico entre el dispositivo y el servidor VPN.

		Encapsulamiento:
		Los paquetes originales son transportados dentro de una comunicación protegida por la VPN.

		Túnel seguro:
		La conexión entre el dispositivo y el servidor VPN funciona como un canal protegido a través de la red pública.

		Protección del tráfico:
		Reduce el riesgo de que otros usuarios de la misma red puedan analizar directamente el contenido de las comunicaciones protegidas por la VPN.

		Privacidad:
		El servidor VPN actúa como intermediario para las conexiones posteriores hacia Internet. Sin embargo, una VPN no proporciona anonimato absoluto y requiere confiar en el proveedor del servicio.

		Una observación es que una VPN no reemplaza HTTPS. Lo recomendable es utilizar ambos mecanismos en esta situación:

		Wi-Fi pública -> VPN cifrada -> HTTPS -> Sitio Web


	5. Escribe tus 3 Reglas de Oro para navegar en redes Wi-Fi públicas.
		
		Regla 1 - No confiar automáticamente en Wi-Fi pública
		Aunque una red tenga contraseña, no significa que sea segura. Antes de conectarse, recomiendo que verifiquen que la red realmente sea proporcionada por el establecimiento.

		Regla 2 - Utilizar HTTPS y VPN cuando sea necesario
		Comprobar si los sitios que vas a ingresar, utilicen HTTPS. Y cuando esta conectado a una red publica no confiable, lo recomendable es conectarse a una VPN, para agregar capa adicional de protección.

		Regla 3 - Evitar operaciones sensibles en redes desconocidas
		Evitar realizar operaciones sensibles desde redes públicas, como por ejemplo, operaciones bancarias. También es recomendable desactivar el uso compartido de archivos y mantener el sistema operativo y los aplicativos siempre actualizados.



 

		

