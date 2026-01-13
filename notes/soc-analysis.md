📊 Análisis SOC — Laboratorio SOC Nivel 1 (Wazuh)

**Autor:** Jesús Eduardo Machuca Quintero  
**Fecha:** 12/01/2026  
**Objetivo:** Documentar el análisis defensivo de incidentes detectados en el laboratorio SOC L1.

---

## 🧩 Resumen del Laboratorio

El laboratorio consistió en:

* **SOC Server:** Ubuntu Server 22.04 con Wazuh Manager y Dashboard  
* **Endpoint monitoreado:** Kali Linux con Wazuh Agent  
* **Escenarios analizados:** A1–A4  
* **Flujo de logs:** Autenticación, sudo, integridad de archivos y actividad de red  
* **Separación de roles:**
  * SOC: análisis y monitorización
  * Endpoint: generador de eventos simulando actividad maliciosa

![Arquitectura SOC](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/architecture/soc-architecture.png)

---

## ⚡ Escenarios y Observaciones

1. **[A1 – Fuerza Bruta SSH](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/attacks/A1-ssh-bruteforce.md)**  
   - IP interna intentando múltiples accesos SSH fallidos.  
   - Alerta generada en Wazuh Dashboard (severidad media/alta).  
   - Evidencias: [screenshots/ssh](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/SSH)  
   - Acción recomendada: Monitoreo continuo, posible bloqueo de IP, revisión de políticas SSH.

2. **[A2 – Abuso de privilegios (sudo)](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/attacks/A2-sudo-abuse.md)**  
   - Usuario intentando escalar privilegios sin éxito.  
   - Alerta generada (severidad media).  
   - Evidencias: [screenshots/sudo](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/sudo)  
   - Acción recomendada: Revisar sudoers, monitoreo del usuario, escalamiento si persiste.

3. **[A3 – Integridad de archivos (FIM)](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/attacks/A3-file-integrity.md)**  
   - Cambios no autorizados en archivos críticos detectados.  
   - Alerta alta.  
   - Evidencias: [screenshots/fim](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/fim)  
   - Acción recomendada: Validar cambios, notificar al administrador, incrementar monitoreo.

4. **[A4 – Reconocimiento interno](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/attacks/A4-internal-recon.md)**  
   - Escaneo interno y enumeración de servicios detectados.  
   - Alerta media.  
   - Evidencias: [screenshots/recon](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots/recon)  
   - Acción recomendada: Registrar IP y patrón, monitoreo continuo, ajustar alertas.

---

## 🧠 Conclusiones SOC (Nivel 1)

Este laboratorio enfatiza el **rol defensivo del analista SOC**, enfocándose en:

* Identificación temprana de amenazas  
* Análisis contextual de eventos  
* Diferenciación entre actividad legítima y maliciosa  
* Propuesta de acciones de mitigación y escalamiento  

El análisis consolidado se encuentra documentado en:

* [Volver al README principal](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/README.md)

---

## 📁 Referencias y Evidencias

* Escenarios A1–A4: [Directorio attacks](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/attacks)  
* Capturas de evidencia: [Directorio screenshots](https://github.com/jesusmq21/soc-lab-wazuh-l1/tree/main/screenshots)  
* Arquitectura SOC: [soc-architecture.png](https://github.com/jesusmq21/soc-lab-wazuh-l1/blob/main/architecture/soc-architecture.png)

