## 10.1 — Identifica tus stakeholders

| Stakeholder | Rol | Lo que puede aportar |
| :--- | :--- | :--- |
| **Población General / Usuarios Finales** | Cliente / Usuario final[cite: 1, 5] | Retroalimentación de usabilidad, hábitos diarios, validación del valor percibido de las recomendaciones de IA[cite: 1, 5]. |
| **Nutricionistas / Consultores de Salud** | Asesor de Dominio / Experto[cite: 5] | Criterios técnicos para las reglas de hidratación, rangos saludables y validación de prompts nutricionales[cite: 3, 5]. |
| **Profesor de Gestión de Proyectos** | Evaluador y Sponsor Académico[cite: 5] | Validación de la metodología de gestión, estructura WBS/EDT, cronograma de 10 semanas y entregables[cite: 1, 5]. |
| **Profesor de Proyecto Integrador** | Evaluador Técnico[cite: 5] | Retroalimentación y validación de la arquitectura de hardware (ESP32/HX711), conectividad BLE y modelo de IA[cite: 2, 5]. |
| **Equipo de Desarrollo de Software** | Equipo Ejecutor[cite: 1, 5] | Capacidad técnica para programar el firmware, construir la App móvil e integrar las APIs de Inteligencia Artificial[cite: 3, 5]. |
| **Proveedores de Modelos de IA (OpenAI / Google / Ollama)** | Proveedor Tecnológico[cite: 5] | Infraestructura y API del LLM para el procesamiento del lenguaje natural y generación de sugerencias[cite: 2, 5]. |

---

## 10.2 — Define los roles del equipo

| Rol | Persona(s) | Responsabilidad principal en este proyecto |
| :--- | :--- | :--- |
| **Project Manager** | Integrante 1 | Elicitación de requisitos, redacción de actas, estructuración del cronograma de 10 semanas y control de hitos[cite: 1, 2]. |
| **Product Owner** | Integrante 2 | Gestión y depuración del Product Backlog, priorización MoSCoW, definición de Criterios de Aceptación e interacción con el cliente[cite: 1]. |
| **Scrum Master** | Integrante 3 | Facilitación de ceremonias ágiles, eliminación de bloqueos técnicos/de hardware y gestión de la velocidad del equipo. |
| **Development Team** | Integrantes 1, 2 y 3 | Desarrollo del firmware ESP32, integración de celda HX711, configuración del servidor BLE, desarrollo de App móvil e integración con la API de IA[cite: 2, 3]. |

---

## 10.3 — Prepara tu guía de entrevista

**Entrevistado objetivo:** Nutricionista / Asesor de Salud (Experto de Dominio)[cite: 5]

### Preguntas sobre el proceso actual (cómo funciona HOY)
1. ¿Cómo realizan actualmente los usuarios el seguimiento de su peso y composición corporal en casa antes de asistir a una consulta?
2. ¿Qué herramientas o aplicaciones suelen utilizar los pacientes hoy en día para registrar sus datos de salud diarios?

### Preguntas sobre los puntos de dolor (qué problemas tiene HOY)
3. ¿Cuál es la principal dificultad que enfrentan las personas al interpretar datos como el peso o el porcentaje de grasa en básculas comerciales[cite: 1]?
4. ¿Por qué las recomendaciones nutricionales o de hidratación genéricas suelen fallar en mantener la adherencia del usuario[cite: 1]?

### Preguntas sobre la visión (qué espera que cambie)
5. ¿Qué tipo de información o consejo personalizado en tiempo real motivaría a una persona a mantener hábitos de vida saludables[cite: 1]?
6. ¿Cómo se imagina que la Inteligencia Artificial pueda transformar una lectura de peso convencional en un plan de acción diario[cite: 1, 2]?

### Preguntas sobre casos borde (¿qué pasa cuando...?)
7. ¿Qué debe responder o hacer el sistema si la báscula registra una variación drástica e inusual de peso (por ejemplo, ±3 kg de un día a otro)?
8. ¿Qué comportamiento o advertencia debe tener la aplicación si las métricas del usuario sugieren un riesgo de deshidratación severa o hábitos no saludables?

### Pregunta de cierre
9. ¿Hay algún aspecto clave del comportamiento de los usuarios o del análisis de datos de salud que no te haya preguntado y consideres vital incluir?

---

## 10.4 — Conduce la entrevista y escribe el acta

### ACTA DE ELICITACIÓN
* **Proyecto:** Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA[cite: 1]
* **Entrevistado:** Dr. Alejandro Martínez (Nutricionista / Consultor de Salud)[cite: 5]
* **Fecha:** 15 de Septiembre de 2026[cite: 1]

#### PUNTOS DE DOLOR ACTUALES:
* Las básculas digitales convencionales entregan datos cuantitativos aislados sin explicar su significado ni ofrecer un contexto de acción[cite: 1].
* Falta de educación nutricional básica en tiempo real sobre consumo de líquidos y hábitos diarios al momento de pesarse[cite: 1].
* Alta tasa de abandono en el monitoreo personal debido a la rigidez y falta de empatía en las herramientas actuales[cite: 1].

#### VISIÓN DEL NEGOCIO:
* Transformar las mediciones corporales cuantitativas en recomendaciones comprensibles, empáticas y personalizadas generadas por IA en menos de 5 segundos[cite: 1, 2].
* Fomentar el autocuidado adaptado a las metas específicas del usuario (control de peso, hidratación, mantenimiento o deportistas)[cite: 1, 3].

#### ACTORES IDENTIFICADOS:
* Usuario Final (personas adultas, deportistas, personas en control de peso)[cite: 1, 5].
* Agente de Inteligencia Artificial (LLM/API)[cite: 2, 5].
* Dispositivo Físico / Báscula (ESP32)[cite: 1, 2].

#### RESTRICCIONES EXPLÍCITAS:
* Plazo temporal de desarrollo limitado estrictamente a 10 semanas académicas[cite: 1, 4].
* Prototipado físico en acrílico/impresión 3D, excluyendo fabricación o moldeo industrial[cite: 3].
* Sin certificación médica regulatoria (FDA, INVIMA, etc.)[cite: 3].
* Limitaciones de memoria RAM/Flash y procesamiento nativas del microcontrolador ESP32[cite: 4].

#### REQUISITOS LATENTES DESCUBIERTOS:
* Necesidad de almacenar un historial local de lecturas en la App para no perder información si falla temporalmente la conexión a Internet o BLE[cite: 3, 4].
* Inclusión de avisos de descargo de responsabilidad (*disclaimers*) legales informando que el sistema no sustituye un diagnóstico médico profesional[cite: 3].

---

## 10.5 — Escribe tus Historias de Usuario

### HU-01: Captura de peso y transmisión BLE
**Como** usuario final,  
**quiero** pesarme en la báscula física y que el valor se envíe automáticamente a mi aplicación móvil por Bluetooth,  
**para** tener mi registro de peso actualizado de forma rápida y sin tener que anotarlo manualmente[cite: 1, 2].

**Criterios de aceptación:**
* **Dado que** la báscula está encendida y la aplicación móvil tiene el Bluetooth activo,
* **Cuando** el usuario se sube a la báscula y la lectura del peso se estabiliza en menos de 3 segundos[cite: 2],
* **Entonces** la báscula debe transmitir los datos por BLE y la App debe mostrarlos en pantalla en menos de 2 segundos[cite: 2].

---

### HU-02: Generación de recomendaciones personalizadas por IA
**Como** usuario final,  
**quiero** recibir un análisis comprensible y recomendaciones de hábitos al momento de pesarme,  
**para** comprender mis métricas y saber qué acciones tomar sobre mi hidratación y nutrición diaria[cite: 1, 2].

**Criterios de aceptación:**
* **Dado que** la App recibió los datos de peso y métricas del usuario vía BLE[cite: 2],
* **Cuando** la App envía las métricas al módulo de IA (API de LLM)[cite: 2, 3],
* **Entonces** el sistema debe presentar en menos de 5 segundos un reporte claro con consejos empáticos sobre consumo de agua y nutrición adaptados a su perfil[cite: 1, 2].

---

### HU-03: Configuración del perfil de usuario y objetivos
**Como** usuario registrado,  
**quiero** definir mis datos básicos (edad, altura, nivel de actividad) y mi objetivo de salud (perder peso, mantener, ganar masa),  
**para** que el modelo de IA adapte sus recomendaciones a mi situación particular[cite: 1, 3].

**Criterios de aceptación:**
* **Dado que** el usuario abre la sección de perfil en la aplicación,
* **Cuando** ingresa sus datos, selecciona su objetivo de salud y presiona "Guardar",
* **Entonces** la aplicación debe almacenar la configuración y utilizarla como contexto (*prompt*) en las futuras consultas con la IA[cite: 3].

---

### HU-04: Consulta de historial y gráficas de tendencia
**Como** usuario en control de peso,  
**quiero** visualizar un dashboard con mi historial de mediciones y gráficas de tendencia temporal,  
**para** evaluar el progreso de mis hábitos a lo largo de las semanas[cite: 1, 3].

**Criterios de aceptación:**
* **Dado que** el usuario ha realizado múltiples mediciones en días o semanas anteriores,
* **Cuando** accede a la sección "Dashboard / Historial"[cite: 3],
* **Entonces** la interfaz debe desplegar una gráfica de líneas interactiva con la evolución de su peso y un listado de las recomendaciones previas recibidas[cite: 3].

---

### HU-05: Calibración y tara de la celda de carga en firmware
**Como** desarrollador/administrador del sistema,  
**quiero** ejecutar una rutina de calibración del sensor HX711 en el firmware del ESP32,  
**para** garantizar que las mediciones de peso tengan un margen de error menor al 1%[cite: 2, 3].

**Criterios de aceptación:**
* **Dado que** la báscula está conectada al entorno de pruebas de firmware,
* **Cuando** se coloca una masa patrón conocida sobre la celda de carga y se ejecuta la rutina de calibración[cite: 2, 3],
* **Entonces** el firmware calcula y guarda el factor de escala en la memoria Flash del ESP32, registrando un margen de error inferior al 1% en mediciones posteriores[cite: 2, 4].

---

## 10.6 — Construye tu Product Backlog priorizado

| ID | Historia de Usuario | Prioridad (MoSCoW) | Justificación |
| :--- | :--- | :--- | :--- |
| **HU-05** | Calibración y tara de la celda de carga en firmware | **Must Have** | Sin una lectura precisa de peso en la celda de carga (margen de error < 1%), la báscula pierde su función esencial de hardware[cite: 2]. |
| **HU-01** | Captura de peso y transmisión BLE | **Must Have** | La comunicación inalámbrica ESP32-App es la columna vertebral de la arquitectura de la solución[cite: 2]. |
| **HU-02** | Generación de recomendaciones personalizadas por IA | **Must Have** | Es la propuesta de valor diferenciadora principal del proyecto para resolver el problema central planteado[cite: 1, 2]. |
| **HU-03** | Configuración del perfil de usuario y objetivos | **Should Have** | Necesario para alimentar el contexto del modelo de IA y ofrecer recomendaciones realmente personalizadas[cite: 1, 3]. |
| **HU-04** | Consulta de historial y gráficas de tendencia | **Should Have** | Aporta un valor significativo para el seguimiento a largo plazo del usuario, estando dentro del alcance del dashboard[cite: 3]. |
| **HU-06** | Modo offline con caché local de mediciones | **Could Have** | Permite guardar registros cuando no hay conexión a internet para consultar la IA, pero no bloquea la funcionalidad MVP del prototipo. |
| **HU-07** | Exportación de reportes PDF para nutricionistas | **Won't Have (este release)** | Se encuentra fuera del alcance del cronograma académico de 10 semanas y no es crítico para el uso básico del prototipo[cite: 1, 3]. |