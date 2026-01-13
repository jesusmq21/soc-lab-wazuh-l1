# 📊 Laboratorio SOC Nivel 1 — Wazuh

**Autor:** Jesús Eduardo Machuca Quintero  
**Fecha:** 12/01/2026  
**Objetivo:** Demostrar habilidades de monitoreo, detección y análisis de incidentes desde un SOC L1 usando Wazuh.

---

## 🏛️ Arquitectura del Laboratorio

El laboratorio consta de:

* **SOC Server:** Ubuntu Server 22.04 con Wazuh Manager y Dashboard  
* **Endpoint monitoreado:** Kali Linux con Wazuh Agent  
* **Flujo de logs:** Autenticación, sudo, integridad de archivos y actividad de red  
* **Separación de roles:**
  * SOC: análisis y monitorización
  * Endpoint: generador de eventos simulando actividad maliciosa

👉 [Ver arquitectura SOC](architecture/soc-architecture.png)

---

## ⚡ Ataques Simulados (Escenarios A1–A4)

* [**A1 – Fuerza Bruta SSH**](attacks/A1-ssh-bruteforce.md)  
* [**A2 – Abuso de privilegios (sudo)**](attacks/A2-sudo-abuse.md)  
* [**A3 – Integridad de archivos (FIM)**](attacks/A3-file-integrity.md)  
* [**A4 – Reconocimiento interno**](attacks/A4-internal-recon.md)

---

### **A1 – Fuerza Bruta SSH**

* **Objetivo:** Detectar múltiples intentos fallidos de autenticación SSH  
* **Evidencia:** [screenshots/ssh](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/SSH)  
* **Análisis SOC:** IP interna intentando acceso repetido, alerta media/alta  
* **Acciones recomendadas:** Monitoreo continuo, posible bloqueo de IP, revisión de políticas SSH  

**Documentación completa del ataque:** [A1 – Fuerza Bruta SSH](attacks/A1-ssh-bruteforce.md)

---

### **A2 – Abuso de privilegios (sudo)**

* **Objetivo:** Detectar uso indebido de privilegios  
* **Evidencia:** [screenshots/sudo](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/sudo)  
* **Análisis SOC:** Usuario intentando escalar privilegios sin éxito, alerta media  
* **Acciones recomendadas:** Revisar sudoers, monitoreo de usuario, escalamiento si persiste  

**Documentación completa del ataque:** [A2 – Abuso de privilegios](attacks/A2-sudo-abuse.md)

---

### **A3 – Integridad de archivos (FIM)**

* **Objetivo:** Detectar cambios no autorizados en archivos críticos  
* **Evidencia:** [screenshots/fim](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/fim)  
* **Análisis SOC:** Archivos críticos modificados, alerta alta  
* **Acciones recomendadas:** Validar cambios, notificar admin, incrementar monitoreo  

**Documentación completa del ataque:** [A3 – Integridad de archivos](attacks/A3-file-integrity.md)

---

### **A4 – Reconocimiento interno**

* **Objetivo:** Detectar escaneo de puertos y reconocimiento interno  
* **Evidencia:** [screenshots/recon](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/recon)  
* **Análisis SOC:** Actividad de descubrimiento de red, alerta media  
* **Acciones recomendadas:** Registrar IP y patrón, monitoreo continuo, ajustar alertas  

**Documentación completa del ataque:** [A4 – Reconocimiento interno](attacks/A4-internal-recon.md)

---

## 🧠 Análisis SOC (Nivel 1)

Este laboratorio enfatiza el **rol defensivo del analista SOC**, enfocándose en:

* Identificación temprana de amenazas  
* Análisis contextual de eventos  
* Diferenciación entre actividad legítima y maliciosa  
* Propuesta de acciones de mitigación y escalamiento  

El análisis consolidado se encuentra documentado en: [soc-analysis.md](notes/soc-analysis.md)

---

## 🗂️ Evidencias

Capturas y registros de cada escenario:

* [ssh/](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/SSH) — Fuerza Bruta SSH (A1)  
* [sudo/](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/sudo) — Abuso de privilegios (A2)  
* [fim/](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/fim) — Integridad de archivos (A3)  
* [recon/](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/recon) — Reconocimiento interno (A4)

---

## ✅ Conclusiones

* Todas las alertas fueron detectadas y documentadas correctamente.  
* No se realizaron acciones ofensivas, manteniendo enfoque SOC defensivo.  
* Este laboratorio **demuestra competencia para un SOC Analyst L1**, incluyendo:  
  * Configuración de Wazuh  
  * Monitoreo y análisis de eventos  
  * Documentación profesional de incidentes  
