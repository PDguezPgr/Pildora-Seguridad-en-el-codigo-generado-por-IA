# 🛡️ Seguridad en el Código Generado por IA: Desafíos, Privacidad y Defensa Activa

Este repositorio contiene la investigación, estructura de despliegue y material didáctico presentados en la exposición académica sobre **Ciberseguridad y Gobernanza de Datos en entornos asistidos por Inteligencia Artificial**.

> 💡 *"La productividad sin controles de seguridad puede aumentar también la velocidad a la que generamos vulnerabilidades."*

---

## 📊 Resumen Ejecutivo del Proyecto

El desarrollo de software asistido por Modelos de Lenguaje (LLMs) como GitHub Copilot o ChatGPT ha disparado la velocidad de entrega de código. Sin embargo, este paradigma introduce riesgos críticos si se adopta bajo una confianza ciega. Esta investigación analiza las amenazas técnicas y legales latentes, el impacto humano de las fugas de información sensible y la arquitectura de defensa necesaria para mitigar estos riesgos en entornos corporativos.

---

## 🗂️ Estructura de la Investigación

La investigación se divide en tres bloques fundamentales de análisis y mitigación:

### 1. El Dilema de la Productividad y Errores Técnicos
* **Heredabilidad del Código:** Explicación de cómo las IA replican patrones inseguros o vulnerabilidades del pasado extraídas de repositorios públicos históricos.
* **El Catálogo de Amenazas:** Análisis de fallos comunes generados por IA, incluyendo inyecciones de código, exposición involuntaria de credenciales (*hardcoded secrets*) y encriptaciones obsoletas.
* **Ataques a la Cadena de Suministro:** Simulación del riesgo de **Typosquatting** provocado por alucinaciones de paquetes en gestores como NPM o PyPI.

### 2. Privacidad de Datos y Cumplimiento Normativo (GDPR)
* **Shadow AI Pipeline:** Casos de estudio del mundo real (como el incidente de Samsung en 2023) donde el uso de prompts públicos derivó en fugas de propiedad intelectual o datos médicos.
* **The Human Cost:** Análisis del impacto directo de las filtraciones en los ciudadanos (fraude financiero, exclusión digital y perfilamiento social).
* **Estrategia de Enmascaramiento:** Tipos de *Data Masking* (Static, Dynamic, On-the-Fly) y despliegue de herramientas de anonimización local offline.

### 3. Pipeline de Defensa: La Doble Aduana de Seguridad
* **Automatización con SAST y SCA:** Implementación de herramientas de análisis estático (SonarQube/Semgrep) y análisis de composición de software (Snyk).
* **Filtro Humano (Peer Review):** El papel crítico de las revisiones de código por pares (*Pull Requests*) y el desarrollo seguro de consultas parametrizadas.

---

## 🛠️ Arquitectura de Prevención Técnica

Para la mitigación de los riesgos analizados, se documenta el uso de las siguientes tecnologías y metodologías de control de datos:

| Componente | Tipo de Solución | Propósito Principal | Software Referenciado |
| :--- | :--- | :--- | :--- |
| **DLP** | Endpoint, Network & Cloud | Bloquear la fuga de información sensible (PII) monitorizando el portapapeles y el perímetro | Microsoft Purview, Forcepoint, Netskope |
| **Data Masking** | Static & Dynamic | Anonimizar bases de datos de producción mediante técnicas de sustitución, barajado (*shuffling*) o tokenización | Microsoft Presidio, ARX, Delphix |
| **SAST** | Código Fuente (Estático) | Escanear las líneas de texto del código en busca de vulnerabilidades antes de compilar (como Inyección SQL) | SonarQube, Semgrep |
| **SCA** | Dependencias de Terceros | Auditar la reputación, licencias y fallos públicos de librerías NPM/PyPI sugeridas por la IA | Snyk, GitHub Dependabot |

---

## ⚙️ Caso de Estudio Práctico: Corrección de Inyección SQL

Un pilar central de este repositorio es demostrar la diferencia entre el código vulnerable autónomo y el código seguro corregido tras el flujo de inspección:

### ❌ Código Inseguro (Generado por IA)
```sql
-- La concatenación directa de entradas permite al atacante inyectar comandos lógicos
SELECT * FROM usuarios WHERE nombre = ' + input_usuario_directo
```

### 🟢 Código Seguro (Aprobado en Peer Review)
```sql
-- El signo de interrogación parametriza la consulta, tratando el input estrictamente como texto, jamás como orden
SELECT * FROM usuarios WHERE nombre = ?
```

---

## 📚 Bibliografía, Fuentes y Herramientas Oficiales

* **Casos de Estudio:** [Análisis del Incidente de Samsung en 2023](https://theregister.com) (The Register).
* **Marcos de Trabajo Gubernamentales:** [Principios de Ciberseguridad para la Integración de IA de la NSA / CISA](https://cyber.gov.au).
* **Salud y Privacidad:** [Investigación Médica sobre el impacto de la IA en los Registros Clínicos](https://nih.gov) (PMC Research).
* **Framework de Anonimización de Datos (PII):** [Repositorio de Microsoft Presidio en GitHub](https://github.com).
* **Motor Offline de Privacidad Diferencial:** [Descargas del Software ARX Data Anonymizer](https://deidentifier.org).

---

## 🎮 Gamificación y Validación de Criterios

Para validar la retención y comprensión de los conceptos técnicos de esta investigación, el proyecto cuenta con un cuestionario interactivo de **15 preguntas** diseñado para la plataforma Kahoot. Los criterios evaluados incluyen vulnerabilidades OWASP comunes, mitigación DLP y normativas bajo el artículo 9 del GDPR. El cuestionario puede ser recreado utilizando el esquema analítico documentado en la sección de recursos didácticos de este repositorio.
