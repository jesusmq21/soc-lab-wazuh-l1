# A4 – Reconocimiento Interno (Internal Reconnaissance)

## Descripción

Este escenario simula actividades de **reconocimiento interno** realizadas desde el endpoint monitoreado, representando un comportamiento típico posterior a una intrusión o una amenaza interna.

El objetivo es evaluar la capacidad del SOC para detectar comandos de reconocimiento del sistema y la red que, aunque no son exploits, constituyen **indicadores tempranos de comportamiento malicioso**.

---

## Objetivo del Ataque

* Simular comandos de reconocimiento del sistema y la red.
* Generar eventos sospechosos desde el endpoint monitoreado.
* Validar la visibilidad de actividades de enumeración en Wazuh.
* Analizar las alertas desde la perspectiva de un **SOC Analyst Nivel 1**.

---

## Entorno

* **SOC Server:** Ubuntu Server 22.04 con Wazuh Manager y Wazuh Dashboard.
* **Endpoint monitoreado:** Kali Linux con Wazuh Agent instalado.
* **Tipo de actividad:** Reconocimiento interno post-compromiso.
* **Enfoque:** Detección y análisis SOC (no pentesting).

---

## Ejecución del Ataque

Desde el endpoint monitoreado (Kali Linux), se ejecutaron comandos básicos de reconocimiento del sistema y la red interna.

Ejemplos de comandos ejecutados:

```bash
whoami
id
uname -a
ip a
ip route
netstat -tulnp
```

Estos comandos permiten a un atacante comprender:

* Nivel de privilegios.
* Información del sistema operativo.
* Interfaces de red activas.
* Servicios y puertos en escucha.

---

## Evidencia en el Endpoint

La ejecución de estos comandos genera eventos que son registrados por el sistema y enviados al Wazuh Manager a través del agente.

Para observar la actividad del agente:

```bash
sudo tail -f /var/log/wazuh-agent/wazuh-agent.log
```

---

## Detección en Wazuh

Wazuh identifica estas acciones como **actividad de reconocimiento**, generando alertas asociadas a:

* Ejecución de comandos sensibles.
* Enumeración del sistema.
* Comportamiento anómalo en el endpoint.

Las alertas son visibles en el **Wazuh Dashboard**, permitiendo correlacionar múltiples eventos dentro de una misma ventana temporal.

---

## Evidencias

Las evidencias recolectadas para este escenario se encuentran en:

```
screenshots/recon/
```

Incluyen:

* Alertas de reconocimiento interno en el Dashboard.
* Detalles de los comandos ejecutados.

---

## Análisis SOC (Nivel 1)

Desde el punto de vista de un **SOC Analyst Nivel 1**, este comportamiento es altamente relevante, ya que el reconocimiento interno suele ser una fase temprana en la cadena de ataque.

Indicadores observados:

* Enumeración del sistema sin justificación aparente.
* Múltiples comandos ejecutados en corto tiempo.
* Posible preparación para movimientos laterales.

**Acciones recomendadas:**

* Verificar si la actividad fue autorizada.
* Correlacionar con eventos previos (SSH, sudo, FIM).
* Monitorear actividad posterior del host.
* Escalar el caso si se detecta continuidad del comportamiento.

---

## Resultado

* ✅ Actividad de reconocimiento detectada correctamente.
* ✅ Eventos correlacionados en el Wazuh Dashboard.
* ✅ Análisis SOC documentado de forma adecuada.
* ✅ Laboratorio cerrado con enfoque defensivo profesional.
