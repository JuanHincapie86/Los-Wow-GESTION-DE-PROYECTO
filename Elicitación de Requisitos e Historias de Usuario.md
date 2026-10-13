## 10.1 — Identifica tus stakeholders

| Stakeholder | Rol | Lo que puede aportar |
| :--- | :--- | :--- |
| **Población General / Usuarios Finales** | Cliente / Usuario final | Retroalimentación de usabilidad, hábitos diarios, validación del valor percibido de las recomendaciones de IA. |
| **Nutricionistas / Consultores de Salud** | Asesor de Dominio / Experto | Criterios técnicos para las reglas de hidratación, rangos saludables y validación de prompts nutricionales. |
| **Profesor de Gestión de Proyectos** | Evaluador y Sponsor Académico | Validación de la metodología de gestión, estructura WBS/EDT, cronograma de 10 semanas y entregables. |
| **Profesor de Proyecto Integrador** | Evaluador Técnico | Retroalimentación y validación de la arquitectura de hardware (ESP32/HX711), conectividad BLE y modelo de IA. |
| **Equipo de Desarrollo de Software** | Equipo Ejecutor | Capacidad técnica para programar el firmware, construir la App móvil e integrar las APIs de Inteligencia Artificial. |
| **Proveedores de Modelos de IA (OpenAI / Google / Ollama)** | Proveedor Tecnológico | Infraestructura y API del LLM para el procesamiento del lenguaje natural y generación de sugerencias. |

---

## 10.2 — Define los roles del equipo

| Rol | Persona(s) | Responsabilidad principal en este proyecto |
| :--- | :--- | :--- |
| **Project Manager** | Integrante 1 | Elicitación de requisitos, redacción de actas, estructuración del cronograma de 10 semanas y control de hitos. |
| **Product Owner** | Integrante 2 | Gestión y depuración del Product Backlog, priorización MoSCoW, definición de Criterios de Aceptación e interacción con el cliente. |
| **Scrum Master** | Integrante 3 | Facilitación de ceremonias ágiles, eliminación de bloqueos técnicos/de hardware y gestión de la velocidad del equipo. |
| **Development Team** | Integrantes 1, 2 y 3 | Desarrollo del firmware ESP32, integración de celda HX711, configuración del servidor BLE, desarrollo de App móvil e integración con la API de IA. |

---

## 10.3 — Prepara tu guía de entrevista

**Entrevistado objetivo:** Nutricionista / Asesor de Salud (Experto de Dominio)

### Preguntas sobre el proceso actual (cómo funciona HOY)
1. ¿Cómo realizan actualmente los usuarios el seguimiento de su peso y composición corporal en casa antes de asistir a una consulta?
2. ¿Qué herramientas o aplicaciones suelen utilizar los pacientes hoy en día para registrar sus datos de salud diarios?

### Preguntas sobre los puntos de dolor (qué problemas tiene HOY)
3. ¿Cuál es la principal dificultad que enfrentan las personas al interpretar datos como el peso o el porcentaje de grasa en básculas comerciales?
4. ¿Por qué las recomendaciones nutricionales o de hidratación genéricas suelen fallar en mantener la adherencia del usuario?

### Preguntas sobre la visión (qué espera que cambie)
5. ¿Qué tipo de información o consejo personalizado en tiempo real motivaría a una persona a mantener hábitos de vida saludables?
6. ¿Cómo se imagina que la Inteligencia Artificial pueda transformar una lectura de peso convencional en un plan de acción diario?

### Preguntas sobre casos borde (¿qué pasa cuando...?)
7. ¿Qué debe responder o hacer el sistema si la báscula registra una variación drástica e inusual de peso (por ejemplo, ±3 kg de un día a otro)?
8. ¿Qué comportamiento o advertencia debe tener la aplicación si las métricas del usuario sugieren un riesgo de deshidratación severa o hábitos no saludables?

### Pregunta de cierre
9. ¿Hay algún aspecto clave del comportamiento de los usuarios o del análisis de datos de salud que no te haya preguntado y consideres vital incluir?

---

## 10.4 — Conduce la entrevista y escribe el acta

### ACTA DE ELICITACIÓN
* **Proyecto:** Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA
* **Entrevistado:** Dr. Alejandro Martínez (Nutricionista / Consultor de Salud)
* **Fecha:** 15 de Septiembre de 2026

#### PUNTOS DE DOLOR ACTUALES:
* Las básculas digitales convencionales entregan datos cuantitativos aislados sin explicar su significado ni ofrecer un contexto de acción.
* Falta de educación nutricional básica en tiempo real sobre consumo de líquidos y hábitos diarios al momento de pesarse.
* Alta tasa de abandono en el monitoreo personal debido a la rigidez y falta de empatía en las herramientas actuales.

#### VISIÓN DEL NEGOCIO:
* Transformar las mediciones corporales cuantitativas en recomendaciones comprensibles, empáticas y personalizadas generadas por IA en menos de 5 segundos.
* Fomentar el autocuidado adaptado a las metas específicas del usuario (control de peso, hidratación, mantenimiento o deportistas).

#### ACTORES IDENTIFICADOS:
* Usuario Final (personas adultas, deportistas, personas en control de peso).
* Agente de Inteligencia Artificial (LLM/API).
* Dispositivo Físico / Báscula (ESP32).
