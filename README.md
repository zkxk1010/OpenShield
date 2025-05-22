# OpenShield

## Descripción
La clave  en este proyecto, es que info vamos a recopilar y como vamos a recogerla, para poder hacer las correlaciones pertinentes y que el monitor sea capaz de generar alertas en base a una serie de lógicas que vamos a pre configurar.

La idea, es recopilar todo aquello que nos ayude a saber en que estado se encuentra nuestrp sistema, excepto a nivel de hardware y así poder hacer la correlación con las vulnerabilidades que extraigamos de una fueta abierta.

El producto de Openshield va a ser caapz de recopilar la siguiente información sobre una máquina linux(por ejemplo), que es la que usaremos para realizar el testing del aplicativo OPENSHIELD:


1.Hacer un descubrimiento de los servicios que están corriendo en los puertos habilitados y la version de ese servicio.

Esto lo haríamos con la herramienta de nmap. Los parámetros claves a obtener, serán "Product_Name" , "Product_Version" y "Port"

ejemplo: nmap - p 22,23,3389,445,80,21,161 (puertos + criticos) -sV (version del servicio) -sN IP > ports_services_running.xml (después en el script habría que hacer una inetegración para pasarlo a .json)

.
.
.
.
.

2.Listar todas las aplicaciones instaladas y su respectiva versión

ejemplo : apt list --installed 2>/dev/null | tail -n +2 | awk -F '[ /]' '{print "{\"package\": \""$1"\", \"version\": \""$2"\", \"architecture\": \""$3"\"}"}' | jq -s '.' > paquetes_instalados.json


output:

<img width="316" alt="{FBAB2CF4-5273-4B65-99D6-9C5A3AEC6ACA}" src="https://github.com/user-attachments/assets/6d0f028b-d8fe-4406-ac4f-6c65989f0ad6" />



.
.
.
.
.



3. Listar versión del kernel y del S.O

ejemplo: echo "{\"Product_Name\": \"$(uname -s)\", \"Product_Version\": \"$(uname -r)\"}" > OS_info.json

output:

<img width="260" alt="{9B8AD801-36AE-4BD3-9D2A-863B41AB2D02}" src="https://github.com/user-attachments/assets/f2775117-c27f-4c4b-8537-88124c2266e5" />
TODO
