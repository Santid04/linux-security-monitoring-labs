# Linux Security Monitoring Labs (Wazuh)

## Descripción

Repositorio de laboratorios prácticos orientados al monitoreo de seguridad en sistemas Linux utilizando Wazuh.  
Incluye escenarios de análisis de intentos de fuerza bruta SSH y File Integrity Monitoring (FIM).

---

## Tecnologías utilizadas

- Wazuh 4.7.5
- Linux (Ubuntu Server)
- Fail2ban
- VirtualBox
- Networking local (Host-only)

---

## Laboratorio 1 – Análisis de fuerza bruta SSH

### Objetivo

Analizar intentos de autenticación fallidos por SSH y comprender el flujo de detección y respuesta ante ataques de fuerza bruta en sistemas Linux.

### Escenario

- Sistema Linux con servicio SSH expuesto.
- Máquina atacante generando múltiples intentos de autenticación fallidos.
- Fail2ban configurado para aplicar bloqueos automáticos tras superar un umbral.
- Wazuh configurado para el análisis de eventos de autenticación.

### Análisis realizado

- Se generaron múltiples intentos de autenticación fallidos contra el servicio SSH.
- Se verificó el bloqueo automático de la IP atacante mediante Fail2ban.
- Se analizó el alcance del monitoreo del SIEM en función de la ubicación de los agentes.

### Alcance y limitaciones

- La detección de intentos de autenticación fallida fue analizada a nivel de logs del sistema.
- La respuesta automática de Fail2ban fue validada desde el sistema operativo.
- No se visualizaron alertas de fuerza bruta SSH en el dashboard de Wazuh debido a limitaciones de arquitectura y recursos (no se recolectaron evidencias en el SIEM para este escenario).

---

## Laboratorio 2 – File Integrity Monitoring (FIM)

### Objetivo

Implementar File Integrity Monitoring (FIM) con Wazuh para detectar cambios no autorizados en archivos críticos del sistema.

### Eventos detectados

- **Integrity checksum changed**: detección de modificaciones en archivos existentes.
- **File added to the system**: detección de creación de nuevos archivos.

### Resultados

- Wazuh detectó correctamente modificaciones y creación de archivos en rutas monitoreadas (por ejemplo, `/etc`).
- Las alertas de integridad fueron visualizadas y analizadas desde el dashboard.

---

## Evidencias

Las evidencias disponibles corresponden al laboratorio de File Integrity Monitoring (FIM) y se encuentran en el directorio `/evidencias`:

- Alertas por modificación de archivos (Integrity checksum changed).
- Alertas por creación de archivos (File added to the system).

---

## Aprendizajes

- Funcionamiento general de un SIEM y sus componentes.
- Importancia de la arquitectura de agentes para la visibilidad de eventos.
- Análisis de intentos de fuerza bruta SSH y mecanismos de respuesta automática.
- Implementación de File Integrity Monitoring para la detección de cambios no autorizados.
