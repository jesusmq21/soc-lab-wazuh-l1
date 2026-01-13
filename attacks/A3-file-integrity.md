# A2 – Abuso de Privilegios (Uso Indebido de Sudo)

## Descripción

Este escenario simula un **abuso de privilegios** mediante el uso indebido del comando `sudo` en el endpoint monitoreado, con el objetivo de evaluar la capacidad del SOC para detectar elevaciones de privilegios sospechosas y generar alertas de seguridad relevantes.

El escenario representa un caso común de **amenaza interna**, donde un usuario con acceso legítimo intenta ejecutar comandos con privilegios elevados fuera de su flujo normal de trabajo.

---

## Objetivo del Ataque

* Simular el uso indebido de privilegios administrativos.
* Validar la correcta ingesta de eventos relacionados con `sudo`.
* Confirmar la detección automática por parte de Wazuh.
* Analizar la alerta desde la perspectiva de un **SOC Analyst Nivel 1**.

---

## Entorno

* **SOC Server:** Ubuntu Server 22.04 con Wazuh Manager y Wazuh Dashboard.
* **Endpoint monitoreado:** Kali Linux con Wazuh Agent instalado.
* **Componente monitoreado:** Uso del comando `sudo`.

---

## Ejecución del Ataque

Desde el endpoint monitoreado (Kali Linux), se ejecutaron comandos con privilegios elevados utilizando `sudo`, simulando un uso anómalo o fuera de contexto.

Ejemplo de comandos ejecutados:

```bash
sudo su
```

```bash
sudo nano /etc/passwd
```

Estos comandos generan eventos de auditoría asociados a elevación de privilegios en los logs del sistema.

---

## Evidencia en el Endpoint

Los eventos generados por el uso de `sudo` se registran en el archivo de logs de autenticación del sistema:

```bash
sudo tail -f /var/log/auth.log
```

Ejemplo de eventos registrados:

```text
sudo:     zus : TTY=pts/0 ; PWD=/home/zus ; USER=root ; COMMAND=/usr/bin/su
sudo: pam_unix(sudo:session): session opened for user root(uid=0) by zus(uid=1000)
```

---

## Detección en Wazuh

Wazuh detecta automáticamente eventos relacionados con **uso de privilegios elevados**, generando alertas asociadas a:

* Ejecución de comandos con `sudo`.
* Cambio de contexto de usuario a `root`.
* Sesiones administrativas abiertas.

Las alertas son visibles en el **Wazuh Dashboard**, permitiendo su análisis desde el punto de vista operativo del SOC.

---

## Evidencias

Las capturas de pantalla asociadas a este escenario se encuentran almacenadas en la siguiente ruta del repositorio:

```
screenshots/sudo/
```

Incluyen:

* Eventos de uso de `sudo` en el endpoint.
* Alertas generadas en el Wazuh Dashboard.

---

## Análisis SOC (Nivel 1)

Desde la perspectiva de un **SOC Analyst Nivel 1**, el evento corresponde a un **posible abuso de privilegios**.

Aunque el uso de `sudo` puede ser legítimo, su ejecución fuera de horarios habituales, de forma repetitiva o sin justificación documentada debe ser considerada sospechosa.

No se evidencia compromiso del sistema, pero el evento requiere **validación contextual**.

**Acciones recomendadas:**

* Verificar si el usuario tiene autorización para usar `sudo`.
* Correlacionar con otros eventos del mismo usuario.
* Revisar políticas de mínimo privilegio.
* Considerar alertas de mayor severidad si el patrón persiste.

---

## Resultado

* ✅ Uso de privilegios detectado correctamente.
* ✅ Logs ingeridos sin errores por el agente Wazuh.
* ✅ Alerta visible y analizable en el Wazuh Dashboard.
* ✅ Escenario documentado con enfoque SOC defensivo.

---
y seguimos completando el laboratorio 🔍🛡️

