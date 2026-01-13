# 🛡️ Laboratorio SOC Nivel 1 con Wazuh

## 📌 Descripción General

Este proyecto documenta la implementación y operación de un **laboratorio SOC Nivel 1** utilizando **Wazuh** como plataforma SIEM/XDR, enfocado en **detección, análisis y documentación de incidentes de seguridad** desde una perspectiva defensiva.

El laboratorio fue diseñado para simular **escenarios reales de monitoreo SOC**, priorizando la visibilidad, la correlación de eventos y el análisis inicial de alertas, **sin enfoque de pentesting**.

---

## 🎯 Objetivo del Proyecto

Demostrar competencias prácticas asociadas a un **SOC Analyst Nivel 1**, incluyendo:

* Monitoreo continuo de endpoints.
* Detección automática de actividades sospechosas.
* Análisis inicial de alertas de seguridad.
* Clasificación de eventos y evaluación de impacto.
* Documentación clara y estructurada de incidentes.

---

## 🧱 Arquitectura del Laboratorio

El laboratorio está compuesto por dos máquinas virtuales claramente separadas:

### 🔹 SOC Server

* **Sistema Operativo:** Ubuntu Server 22.04
* **Componentes:**

  * Wazuh Manager
  * Wazuh Indexer (OpenSearch)
  * Wazuh Dashboard
* **Rol:** Recolección, correlación y visualización de eventos.

### 🔹 Endpoint Monitoreado

* **Sistema Operativo:** Kali Linux
* **Componentes:**

  * Wazuh Agent
  * OpenSSH
  * rsyslog habilitado
* **Rol:** Generación de eventos y simulación de comportamiento malicioso interno.

📌 **Nota:** El endpoint no se utiliza como máquina atacante, sino como host monitoreado para simular amenazas internas o post-compromiso.

---

## 🧪 Escenarios de Seguridad Implementados

El laboratorio incluye los siguientes escenarios documentados:

### 🔸 A1 – Fuerza Bruta SSH

* Detección de múltiples intentos fallidos de autenticación.
* Análisis de logs `/var/log/auth.log`.
* Clasificación de severidad y evaluación de riesgo.

### 🔸 A2 – Abuso de Privilegios (sudo)

* Identificación de uso indebido o inusual de privilegios elevados.
* Correlación de eventos `sudo` desde logs del sistema.
* Análisis de impacto y legitimidad de la acción.

### 🔸 A3 – Integridad de Archivos (FIM)

* Monitoreo de cambios en archivos críticos.
* Detección de creación, modificación y eliminación de archivos.
* Evaluación de persistencia o manipulación no autorizada.

### 🔸 A4 – Reconocimiento Interno

* Detección de comandos de enumeración del sistema y red.
* Identificación de comportamiento post-compromiso.
* Correlación temporal de eventos sospechosos.

📁 La documentación detallada de cada escenario se encuentra en el directorio `attacks/`.

---

## 📸 Evidencias

Cada escenario incluye evidencias visuales almacenadas en:

```
screenshots/
├── ssh/
├── sudo/
├── fim/
└── recon/
```

Las capturas muestran alertas reales generadas y analizadas desde el **Wazuh Dashboard**.

---

## 🧠 Análisis SOC (Nivel 1)

Este laboratorio enfatiza el rol defensivo del analista SOC, enfocándose en:

* Identificación temprana de amenazas.
* Análisis contextual de eventos.
* Diferenciación entre actividad legítima y maliciosa.
* Propuesta de acciones de mitigación y escalamiento.

El análisis consolidado se encuentra documentado en:

```
notes/soc-analysis.md
```

---

## 🛠️ Tecnologías Utilizadas

* Wazuh (Manager, Agent, Dashboard)
* OpenSearch
* Ubuntu Server 22.04
* Kali Linux
* Linux Logging (auth.log, syslog)
* SSH
* rsyslog

---

## 💼 Valor Profesional

Este laboratorio demuestra habilidades prácticas clave para posiciones como:

* SOC Analyst Nivel 1
* Analista de Seguridad Junior
* Blue Team Trainee

El proyecto evidencia capacidad para **detectar, analizar y documentar incidentes reales**, siguiendo buenas prácticas de operación SOC.

---

## 📎 Notas Finales

* No se utilizaron herramientas de explotación (Metasploit, exploits, etc.).
* No se realizó escaneo agresivo de red.
* El enfoque es **100 % defensivo y orientado a SOC**.

---

## 👤 Autor

**Jesús Eduardo Machuca Quintero**
Laboratorio SOC Nivel 1 – Wazuh
Enero 2026
Solo dime qué sigue. 💼🛡️
