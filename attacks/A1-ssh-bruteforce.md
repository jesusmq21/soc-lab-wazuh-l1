# A1 – Ataque de Fuerza Bruta SSH

## Descripción

Este escenario simula un ataque de fuerza bruta contra el servicio SSH del endpoint monitoreado, con el objetivo de evaluar la capacidad del SOC para detectar intentos repetidos de autenticación fallida y generar alertas de seguridad relevantes.

El ataque se ejecuta desde otra máquina dentro de la red local, representando un escenario realista de **amenaza interna** o de un **atacante con acceso a la red**.

---

## Objetivo del Ataque

* Generar múltiples intentos fallidos de autenticación SSH.
* Validar la correcta ingesta de logs (`/var/log/auth.log`).
* Confirmar la detección automática por parte de Wazuh.
* Analizar la alerta desde la perspectiva de un **SOC Analyst Nivel 1**.

---

## Entorno

* **SOC Server:** Ubuntu Server 22.04 con Wazuh Manager y Wazuh Dashboard.
* **Endpoint monitoreado:** Kali Linux con Wazuh Agent instalado.
* **Servicio atacado:** OpenSSH (puerto 22).

---

## Ejecución del Ataque

Desde la máquina atacante (diferente al SOC Server), se realizaron múltiples intentos de autenticación SSH contra el endpoint monitoreado utilizando usuarios inexistentes y contraseñas incorrectas.

```bash
ssh fakeuser@192.168.0.122
```

Este comportamiento genera entradas repetidas de error en los logs de autenticación del sistema.

---

## Evidencia en el Endpoint

En el endpoint monitoreado se verifican los eventos en tiempo real mediante el archivo de logs de autenticación:

```bash
sudo tail -f /var/log/auth.log
```

Ejemplo de eventos registrados:

```text
Failed password for invalid user fakeuser from 192.168.0.127 port 41610 ssh2
Connection closed by invalid user fakeuser 192.168.0.127
```

---

## Detección en Wazuh

Wazuh detecta automáticamente el patrón de **fuerza bruta SSH** y genera alertas de seguridad asociadas a:

* Intentos fallidos repetidos de autenticación.
* Uso de usuarios inválidos.
* Origen remoto persistente desde la misma dirección IP.

Las alertas son visibles en el **Wazuh Dashboard**, clasificadas con severidad **media a alta**, permitiendo su análisis desde el punto de vista operativo del SOC.

---

## Evidencias

Las capturas de pantalla asociadas a este escenario se encuentran almacenadas en la siguiente ruta del repositorio:

```
screenshots/ssh/
```

Incluyen:

* Eventos de autenticación fallida en el endpoint.
* Alertas generadas en el Wazuh Dashboard.

---

## Análisis SOC (Nivel 1)

Desde la perspectiva de un **SOC Analyst Nivel 1**, el evento corresponde a un ataque de fuerza bruta contra el servicio SSH.

No se evidencia compromiso exitoso del sistema.

El origen de la actividad es una **IP interna**, lo que sugiere:

* Posible amenaza interna.
* Equipo comprometido dentro de la red local.

Este evento **no requiere una respuesta inmediata de contención**, pero sí seguimiento y correlación con otros eventos para descartar actividad maliciosa persistente.

**Acciones recomendadas:**

* Monitoreo continuo de intentos de autenticación.
* Evaluación para posible bloqueo de la dirección IP.
* Revisión y endurecimiento de las políticas de acceso SSH.

---

## Resultado

* ✅ Ataque detectado correctamente.
* ✅ Logs ingeridos sin errores por el agente Wazuh.
* ✅ Alerta visible y analizable en el Wazuh Dashboard.
* ✅ Escenario documentado con enfoque SOC defensivo.



