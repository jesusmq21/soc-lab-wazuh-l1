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

```bash
ssh admin@192.168.0.122

