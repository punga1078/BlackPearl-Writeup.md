# TRABAJO FINAL CIBERSEGURIDAD


---

## Datos Generales

* Máquina Virtual elegida: Black Pearl
* Fecha de análisis: 06/11/2025
* Equipo/entorno utilizado: KALI LINUX


## Descripción del Caso

El objetivo del análisis fue realizar un reconocimiento, identificación de servicios y vulnerabilidades en la máquina virtual 'Black Pearl', proporcionada en el documento compartido Course VMs de la Diplomatura en Ciberseguridad. Durante la investigación se determinó que el servidor ejecutaba Nginx sobre un sistema Debian con PHP 7.3.27 y alojaba un CMS vulnerable denominado Navigate CMS v2.8.

## Alcance de la Investigación

El alcance incluyó el escaneo de puertos y servicios, enumeración de directorios web, identificación del sistema operativo, detección de vulnerabilidades conocidas y prueba de explotación controlada para confirmar la existencia de vulnerabilidades en el sistema.

## Metodología y herramientas

Se siguió una metodología basada en reconocimiento pasivo y activo utilizando las siguientes herramientas:

* **Nmap:** detección de puertos y servicios.
* **Gobuster:** enumeración de directorios y rutas ocultas.
* **Searchsploit:** búsqueda de exploits públicos asociados al CMS detectado.
* **Metasploit Framework:** verificación y explotación del módulo Navigate CMS Remote Code Execution (RCE).

## Análisis y Hallazgos

El análisis permitió identificar que la máquina Black Pearl presenta una vulnerabilidad crítica de tipo RCE debido a una versión obsoleta de Navigate CMS y configuración insegura del sistema (binario PHP con SUID). Esto permitiría a un un atacante ejecutar comandos remotos sobre el servidor sin necesidad de autenticación, comprometiendo la integridad y confidencialidad del sistema.

Además se tuvo que tener en cuenta que se presentaron problemas:

> **Problemas generado a la hora de instalar la maquina**
> La maquina venia ya configurada con la red NAT, esto no me daba una ipv4, solo me daba una ipv6 con la cual no podía hacer nada. Cambie la configuración a NAT y ahí sí me daba ipv4, pero había incompatibilidad porque las dos vm (kali, black pearl) tenían la misma ip, entonces la máquina no sabía a qué hosts hacer el escaneo. Por último, cambie las dos máquinas a Adaptador puente o Bridge y desde ahí pude hacer andar las dos vm bien, con sus respectivas ipv4.

## Conclusiones

El análisis de la máquina Black Pearl no solo permitió poner en práctica herramientas y técnicas de ciberseguridad, sino que también evidenció la importancia de comprender cada etapa del proceso, desde la configuración del entorno hasta la interpretación de resultados. Más allá de las vulnerabilidades identificadas, este ejercicio reforzó la necesidad de mantener una mirada crítica y metódica al trabajar con sistemas reales, donde incluso detalles aparentemente menores como la configuración de red o versiones de software pueden cambiar completamente el curso de una investigación.



---

## 🔎 Ver el Paso a Paso Detallado (Anexos)

Puedes encontrar los comandos utilizados, el log del sistema y el detalle del proceso de explotación en el archivo separado: **[Paso-a-Paso.md](./Paso-a-Paso.md)**
