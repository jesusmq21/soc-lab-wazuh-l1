# A1 – Ataque de Fuerza Bruta SSH

## Descripción
Este escenario simula un ataque de **fuerza bruta contra el servicio SSH** del endpoint monitoreado, con el objetivo de evaluar la capacidad del SOC para **detectar intentos repetidos de autenticación fallida** y generar alertas de seguridad relevantes.

El ataque se ejecuta **desde otra máquina dentro de la red local**, representando un escenario realista de **amenaza interna o atacante con acceso a la red**.

---

## Objetivo del Ataque
- Generar múltiples intentos fallidos de autenticación SSH.
- Validar la correcta ingesta de logs (`/var/log/auth.log`).
- Confirmar la detección automática por parte de **Wazuh**.
- Analizar la alerta desde la perspectiva de un **SOC Analyst L1**.

---

## Entorno
- **SOC Server:** Ubuntu Server 22.04 con Wazuh Manager + Dashboard
- **Endpoint monitoreado:** Kali Linux con Wazuh Agent
- **Servicio atacado:** OpenSSH (puerto 22)

---

## Ejecución del Ataque 

Desde la máquina atacante (diferente al SOC):

``bash
ssh fakeuser@192.168.0.122

Se realizaron múltiples intentos de autenticación utilizando:

Usuarios inexistentes (fakeuser)

Contraseñas incorrectas

Este comportamiento genera entradas repetidas de error en los logs de autenticación.

Evidencia en el Endpoint

En el endpoint monitoreado se verifican los eventos en tiempo real:

sudo tail -f /var/log/auth.log


Ejemplo de eventos registrados:

Failed password for invalid user fakeuser from 192.168.0.127 port 41610 ssh2
Connection closed by invalid user fakeuser 192.168.0.127

Detección en Wazuh

Wazuh detecta automáticamente el patrón de fuerza bruta SSH y genera alertas de seguridad asociadas a:

Intentos fallidos repetidos

Usuario inválido

Origen remoto persistente

Las alertas son visibles en el Wazuh Dashboard, clasificadas con severidad media/alta.

Evidencias 

Las siguientes evidencias fueron recolectadas y almacenadas en:

screenshots/ssh/

Análisis SOC (Nivel 1)

Desde la perspectiva de un SOC Analyst L1:

El evento corresponde a un ataque de fuerza bruta SSH.

No se evidencia compromiso exitoso.

El origen es una IP interna, lo que sugiere:

Amenaza interna

Equipo comprometido dentro de la red

Acción recomendada:

Monitoreo continuo

Posible bloqueo de IP

Revisión de políticas de acceso SSH

Resultado

✅ Ataque detectado correctamente
✅ Logs ingeridos sin errores
✅ Alerta visible y analizable en el Dashboard
✅ Escenario documentado con enfoque SOC defensivo



