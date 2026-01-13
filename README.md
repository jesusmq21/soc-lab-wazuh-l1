# 🛡️ Laboratorio SOC Nivel 1 con Wazuh

## 📌 Descripción General

Este repositorio documenta un **Laboratorio SOC Nivel 1 (L1)** completamente funcional, diseñado para demostrar capacidades reales de **monitoreo, detección, análisis y documentación de incidentes de seguridad**, utilizando **Wazuh** como plataforma SIEM/XDR.

El laboratorio está enfocado estrictamente en una **mentalidad SOC defensiva**, no en pentesting, y replica escenarios reales que un **SOC Analyst L1** enfrenta en entornos productivos.

---

## 🎯 Objetivo del Laboratorio

Demostrar de forma práctica y documentada que soy capaz de:

* Implementar una arquitectura SOC básica correcta
* Integrar endpoints a un SIEM
* Detectar comportamientos maliciosos comunes
* Analizar alertas de seguridad
* Clasificar eventos por severidad
* Documentar incidentes de forma profesional

---

## 🧱 Arquitectura del SOC

El laboratorio utiliza una arquitectura **SOC centralizado con separación de roles**:

### 🔹 SOC Server

* **Sistema:** Ubuntu Server 22.04
* **Componentes:**

  * Wazuh Manager
  * Wazuh Indexer (OpenSearch)
  * Wazuh Dashboard
* **Rol:** Correlación, análisis y visualización de eventos

### 🔹 Endpoint Monitoreado

* **Sistema:** Kali Linux
* **Componentes:**

  * Wazuh Agent
  * SSH habilitado
  * rsyslog activo
* **Rol:** Generación de eventos y simulación de actividad maliciosa interna

📌 *Importante:* Kali Linux se utiliza **como endpoint**, no como atacante externo.

📷 Diagrama de arquitectura disponible en:

```
architecture/soc-architecture.png
```

---

## 🚨 Escenarios de Ataque Simulados

Todos los ataques fueron ejecutados de forma controlada para validar la capacidad de detección del SOC.

### 🔴 A1 — Fuerza Bruta SSH

* Múltiples intentos fallidos de autenticación SSH
* Detección automática por reglas de Wazuh
* Clasificación de severidad

📄 Documentación detallada:

```
attacks/A1-ssh-bruteforce.md
```

---

### 🔴 A2 — Abuso de Privilegios (sudo)

* Uso indebido de comandos con privilegios elevados
* Registro en logs de autenticación
* Alerta correlacionada por Wazuh

📄 Documentación detallada:

```
attacks/A2-sudo-abuse.md
```

---

### 🔴 A3 — Integridad de Archivos (FIM)

* Modificación de archivos críticos del sistema
* Detección por File Integrity Monitoring
* Registro de cambios y alertas

📄 Documentación detallada:

```
attacks/A3-file-integrity.md
```

---

### 🔴 A4 — Reconocimiento Interno

* Ejecución de comandos de reconocimiento del sistema
* Identificación de comportamiento sospechoso
* Detección como actividad potencialmente maliciosa

📄 Documentación detallada:

```
attacks/A4-internal-recon.md
```

---

## 🖼️ Evidencias

Las capturas de pantalla de cada escenario se encuentran organizadas por tipo de ataque:

```
screenshots/
├── ssh/
├── sudo/
├── fim/
└── recon/
```

Incluyen:

* Comandos ejecutados
* Alertas en Wazuh Dashboard
* Detalles de eventos

---

## 🧠 Análisis SOC

El análisis de los eventos detectados, su clasificación y conclusiones se documentan en:

```
notes/soc-analysis.md
```

Incluye:

* Evaluación de severidad
* Impacto potencial
* Acciones recomendadas
* Escalamiento teórico

---

## 🧰 Tecnologías Utilizadas

* Wazuh
* OpenSearch
* Linux (Ubuntu Server, Kali Linux)
* SSH
* rsyslog
* File Integrity Monitoring (FIM)
* VirtualBox / VMware

---

## 💼 Valor Profesional

Este laboratorio demuestra habilidades clave para un **SOC Analyst Nivel 1**:

* Pensamiento defensivo
* Comprensión de logs
* Análisis inicial de incidentes
* Documentación clara
* Uso real de SIEM

📌 No se utilizaron exploits, Metasploit ni técnicas ofensivas avanzadas, ya que el enfoque es **detección y análisis**, no explotación.

---

## 👤 Autor

**Jesús Eduardo Machuca Quintero**
SOC Analyst L1 (en formación)

---

## 📎 Nota Final

Este laboratorio fue construido con fines educativos y profesionales, simulando escenarios reales de un entorno SOC.


