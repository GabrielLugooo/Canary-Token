<img align="center" src="https://i.imgur.com/ZgHWFhw.png" alt="gabriellugo" />

# CANARY TOKEN

<a href="https://github.com/GabrielLugooo/Canary-Token/blob/main/README%20Spanish.md" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Tóken%20Canary%20Español-000000" alt="Canary Español" /></a>
<a href="https://github.com/GabrielLugooo/Canary-Token" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Tóken%20Canary%20Inglés-green" alt="Canary Inglés" /></a>

## Objetivos

Aquí se explica desde la perspectiva defensiva y de forma conceptual qué es un website copier como _HTTrack_, cómo los atacantes lo aprovechan para copias y phishing, y cómo defenderse con _Canarytokens_ y un _Servidor de Canarytokens_.

En términos generales los website copiers, son una amenaza para la suplantación (phishing) y qué medidas de detección/mitigación recomendamos (con especial foco en Canarytokens).

Este repositorio es informativo y orientado a la defensa. No contiene (ni solicita) instrucciones para realizar ataques.

Está pensado para equipos de seguridad, administradores web y desarrolladores.

## Habilidades Aprendidas

- Comprensión avanzada de los conceptos del HTTrack Website Copier y su funcionamiento práctico.
- Comprensión avanzada de los conceptos del CanaryToken y su aplicación práctica.
- Competencia en el uso de CanaryToken Server.
- Capacidad para generar y reconocer firmas y patrones de ataques.
- Mayor conocimiento de las vulnerabilidades de seguridad.
- Desarrollo de habilidades de pensamiento crítico y resolución de problemas en ciberseguridad.

## Herramientas Usadas

![Static Badge](https://img.shields.io/badge/HTTracks-000000?logo=github&logoSize=auto)
![Static Badge](https://img.shields.io/badge/CanaryToken-000000?logo=github&logoSize=auto)
![Static Badge](https://img.shields.io/badge/CanaryServer-000000?logo=github&logoSize=auto)

- HTTrack: Herramienta de _website copier/offline browser_.
- Herramienta de análisis _Canarytoken_ (tripwires)
- Servidor privado de _CanaryTokens_ para detectar accesos no autorizados y enlaces clonados.

## ¿Qué es HTTrack Website Copier?

Un Website Copier (como HTTrack) es una utilidad que descarga páginas, imágenes y recursos de un sitio web para recrearlo localmente o en otro servidor. Se usa legítimamente para archivado o navegación offline, pero la misma capacidad puede facilitar la creación de réplicas de sitios.

### Layout del Ataque

#### Layout General del Ataque

<img align="center" src="assets/HttrackLayout.jpg" alt="Httrack Layout" />

#### Web de HTTrack

<img align="center" src="assets/HttrackWeb1.jpg" alt="Httrack Web" />

#### Download de HTTrack

<img align="center" src="assets/HttrackWeb2.jpg" alt="Httrack Download" />

#### Setup inicial

<img align="center" src="assets/HttrackSetup1.jpg" alt="Httrack Setup" />

#### Nombrar el proyecto

<img align="center" src="assets/HttrackSetup2.jpg" alt="Httrack Project Name" />

#### Copiar direccion de la web _REAL_

<img align="center" src="assets/WellsFargoReal.jpg" alt="Httrack Copy Dir" />

#### Pegar la direccion de la web a copiar

<img align="center" src="assets/HttrackSetup3.jpg" alt="Httrack Paste Dir" />

#### Operacion de _Mirroring_ o clonado

<img align="center" src="assets/HttrackSetup4.jpg" alt="Httrack Mirroring init" />

#### Operacion de mirroring finalizada

<img align="center" src="assets/HttrackSetup5.jpg" alt="Httrack Mirroring Finish" />

#### Resultado de la web _FAKE_ (ver HHTTP en Local)

<img align="center" src="assets/WellsFargoFake.jpg" alt="Httrack Results" />

## Canarytokens: ¿Qué son y por qué ayudan?

Canarytokens son “tripwires” sencillos (links, documentos, DNS names, API keys falsas, etc.) que, cuando son accedidos/ejecutados, generan una alarma notificando que algo sospechoso ocurrió. Son una forma económica y efectiva de detectar actividad maliciosa temprano.

Servidor propio: Thinkst publica herramientas y imágenes Docker para correr tu propio servidor de Canarytokens — útil para evitar depender de servicios públicos y para escalabilidad/privacidad.

### Layout de Defensa

#### Objetivo de la amenaza

<img align="center" src="assets/HttrackLayout2.jpg" alt="Httrack Objetive" />

#### Seleccionar el token cloned website en la web de Canary

<img align="center" src="assets/CanaryWeb1.jpg" alt="Canary Web Select Token" />

#### En el token cloned website ingresar datos solicitados:

- mail para alertas
- nombre del token
- web a proteger del clonado

<img align="center" src="assets/CanaryWeb2.jpg" alt="Canary Token Info " />

#### Copiar el Javascript del token

<img align="center" src="assets/CanaryWeb3.jpg" alt="Canary Token Javascript" />

#### Abrir el index.html de la web _REAL_

<img align="center" src="assets/CanaryTokenJS1.jpg" alt="Canary Token Javascript" />

#### Pegar el Javascript del token (no olvidar los <script></script>)

<img align="center" src="assets/CanaryTokenJS2.jpg" alt="Canary Token Javascript" />

#### Triggering del token

- Si alguien clona la web se dispara el token y nos llegara la alerta por mail con los detalles basicos:

<img align="center" src="assets/CanaryTokenJS4.jpg" alt="Canary Token Mail" />

#### Tambien podemos ver el trigger de la alerta en la web de CanaryToken y mas detalles como la ubicacion

de la amenaza:

<img align="center" src="assets/CanaryTokenJS5.jpg" alt="Canary Token Map" />

#### Obfuscacion del Javascript del token

- Si la amenaza inspecciona el index.html de la web antes del clonado puede determinar que la web contiene
  un Token Canary, para reforzar la seguridad y invisibilizar el Token procedemos con la ofuscacion del .JS
  mediante la web obfuscator.io:

<img align="center" src="assets/CanaryTokenJS6.jpg" alt="Token Javascript obf 1" />

#### Una vez ejecutado (click en boton obfuscate), copiar el token Javascript obfuscado, seria algo similar a:

<img align="center" src="assets/CanaryTokenJS7.jpg" alt="Token Javascript obf 2" />

#### Pegar el el token Javascript obfuscado en el index.html de la web:

<img align="center" src="assets/CanaryTokenJS8.jpg" alt="Token Javascript obf 3" />

#### Pinging la web canarytokens.com

- En CMD procedemos a hacer un Ping sobre la web canarytokens.com, eso nos dara la IP del servidor por lo que permite enmascarar el dominio canarytokens.com:

- Copiamos la IP y la pegamos como indica la imagen ('HTTP://52.18.63.80/') en el token obfuscado, en el
  index.html donde antes estaba el dominio canarytokens.com.

<img align="center" src="assets/CanaryTokenJS9.jpg" alt="Canary Token Javascript" />

#### Ocultacion del token final

- finalmente nos deberia quedar algo asi si una amenaza inspecciona el codigo del index.html
  de la web real:

<img align="center" src="assets/CanaryTokenJS10.jpg" alt="Canary Token Javascript" />

- de manera publica es la mayor invisibilidad que se puede lograr para ocultar el Canary Token,
  en la siguiente seccion (Servidor Privado) se puede seguir ampliando la seguridad.

## Servidor Privado de CanaryToken para mas seguridad

### AQUI !!!

## Estrategia de Defensa Recomendada (resumen práctico, sin comandos):

- Inventario y priorización: identificar activos críticos (login pages, repositorios de claves, portales internos).
- Colocar canary tokens en puntos “atractivos” para un atacante: páginas de login no accesibles públicamente, archivos “secreto.txt” en rutas administrativas, variables de entorno en repositorios (como tokens falsos).

_Mi favorito: usar tokens en páginas sensibles y en GitHub secrets para detectar exfiltración_

- Servidor Canarytokens privado: desplegar si necesitas control y privacidad; usar Docker images oficiales como punto de partida.
- Monitorización y alertas: integrar las notificaciones de token con tu SIEM, Slack/Teams o un correo de respuesta rápida.
- Higiene web adicional: HTTPS estricto, HSTS, validación de certificados, DMARC/SPF/DKIM para correo, y CSP (Content Security Policy) para reducir riesgos de inyecciones.
- Educación y playbooks: entrenar a usuarios sobre comprobar dominios, y tener un playbook de respuesta a phishing detectado.

## Detección específica de clones/phishing (qué buscar):

- Peticiones a hosts sospechosos que devuelven contenido idéntico al tuyo.
- Tokens canarios que se disparan desde IP/ASN inusuales o desde países donde no operas.
- Múltiples intentos de autenticación a cuentas desde la URL clonada (si puedes correlacionarlo).
- Monitoreo de DMARC/forensics de correo para detectar envíos con dominios parecidos.

_(Estos puntos son indicativos — diseñalos según tus capacidades de monitoring.)_

## Respuesta ante detección (checklist):

- Confirmar la trampa: validar el token que disparó y su contexto (IP, UA, referer).
- Capturar evidencia (logs, pcap si aplica, capturas de pantalla).
- Bloquear la URL/hosting donde está el clon (reportar al proveedor/registrador).
- Notificar a equipos legales/PR si hay fuga de datos o riesgo reputacional.
- Rotar credenciales potencialmente comprometidas y forzar MFA donde aplique.
- Revisar y fortalecer controles donde el incidente explotó una debilidad.

## Buenas prácticas para reducir la superficie de phishing:

- Aplicar MFA obligatorio en accesos sensibles.
- Implementar DMARC/ SPF / DKIM para mitigar spoofing por correo.
- Forzar HSTS, certificados válidos y certificado pinning donde sea práctico.
- Revisar exposición de assets en repositorios públicos (secrets scanning).
- Emplear detecciones "canary" en repositorios y configuraciones

_(mi favorito: token tipo AWS API key fake en GitHub para detectar leaks)_

## Consideraciones éticas y legales

- No usar técnicas de honeypot/canary que puedan violar leyes locales (p. ej. recolección de datos personales sin aviso).
- Coordina con el equipo legal antes de desplegar sensores que interactúen con usuarios externos.
- Los canary tokens no deben usarse para “hackear de vuelta”.

## Recursos útiles (lecturas oficiales)

- HTTrack — sitio oficial sobre qué es y uso legítimo.
  https://www.httrack.com/

- Canarytokens / Thinkst (repositorio y docs).
  https://github.com/thinkst/canarytokens?utm_source=chatgpt.com

- Canarytokens.org — página pública y generador.
  https://canarytokens.org/nest/

- Artículo resumen sobre descargadores de sitios y riesgos generales.
  https://www.lifewire.com/how-to-download-a-website-for-offline-reading-4769529?utm_source=chatgpt.com

### Limitaciones

CanaryToken es solo para fines educativos bajo la licencia MIT.

---

<h3 align="left">Conecta Conmigo</h3>

<p align="left">
<a href="https://www.youtube.com/@gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=55200&format=png" alt="@gabriellugooo" height="40" width="40" /></a>
<a href="http://www.tiktok.com/@gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=118638&format=png" alt="@gabriellugooo" height="40" width="40" /></a>
<a href="https://instagram.com/lugooogabriel" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=32309&format=png" alt="lugooogabriel" height="40" width="40" /></a>
<a href="https://twitter.com/gabriellugo__" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=phOKFKYpe00C&format=png" alt="gabriellugo__" height="40" width="40" /></a>
<a href="https://www.linkedin.com/in/hernando-gabriel-lugo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=50&id=8808&format=png" alt="hernando-gabriel-lugo" height="40" width="40" /></a>
<a href="https://github.com/GabrielLugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.icons8.com/?size=80&id=AngkmzgE6d3E&format=png" alt="gabriellugooo" height="34" width="34" /></a>
<a href="mailto:lugohernandogabriel@gmail.com"> <img align="center" src="https://img.icons8.com/?size=50&id=38036&format=png" alt="lugohernandogabriel@gmail.com" height="40" width="40" /></a>
<a href="https://linktr.ee/gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://simpleicons.org/icons/linktree.svg" alt="gabriellugooo" height="40" width="40" /></a>
</p>

<p align="left">
<a href="https://github.com/GabrielLugooo/GabrielLugooo/blob/main/Readme%20Spanish.md" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Versión%20Español-000000" alt="Versión Español" /></a>
<a href="https://github.com/GabrielLugooo/GabrielLugooo/blob/main/README.md" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Versión%20Inglés-Green" alt="Versión Inglés" /></a>

</p>

<a href="https://linktr.ee/gabriellugooo" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/Créditos-Gabriel%20Lugo-green" alt="Créditos" /></a>
<img align="center" src="https://komarev.com/ghpvc/?username=GabrielLugoo&label=Vistas%20del%20Perfil&color=green&base=2000" alt="GabrielLugooo" />
<a href="" target="_blank" rel="noreferrer noopener"> <img align="center" src="https://img.shields.io/badge/License-MIT-green" alt="Last Edited" /></a>
