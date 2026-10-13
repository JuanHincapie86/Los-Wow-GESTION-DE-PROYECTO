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
| **Project Manager** | Integrante  | Elicitación de requisitos, redacción de actas, estructuración del cronograma de 10 semanas y control de hitos. |
| **Product Owner** | Integrante  | Gestión y depuración del Product Backlog, priorización MoSCoW, definición de Criterios de Aceptación e interacción con el cliente. |
| **Scrum Master** | Alejandro Luna Hoyos | Facilitación de ceremonias ágiles, eliminación de bloqueos técnicos/de hardware y gestión de la velocidad del equipo. |
| **Development Team** | Juan David Garcia, Juan Jose Hincapie, Joseph Lerma, Alejandro Luna, Sebastian Zacipa | Desarrollo del firmware ESP32, integración de celda HX711, configuración del servidor BLE, desarrollo de App móvil e integración con la API de IA. |

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
* **Entrevistado:** 
* **Fecha:** 

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

#### RESTRICCIONES EXPLÍCITAS:
* Plazo temporal de desarrollo limitado estrictamente a 10 semanas académicas.
* Prototipado físico en acrílico/impresión 3D, excluyendo fabricación o moldeo industrial.
* Sin certificación médica regulatoria (FDA, INVIMA, etc.).
* Limitaciones de memoria RAM/Flash y procesamiento nativas del microcontrolador ESP32.

#### REQUISITOS LATENTES DESCUBIERTOS:
* Necesidad de almacenar un historial local de lecturas en la App para no perder información si falla temporalmente la conexión a Internet o BLE.
* Inclusión de avisos de descargo de responsabilidad (*disclaimers*) legales informando que el sistema no sustituye un diagnóstico médico profesional.

---

## 10.5 — Escribe tus Historias de Usuario

### HU-01: Captura de peso y transmisión BLE
**Como** usuario final,  
**quiero** pesarme en la báscula física y que el valor se envíe automáticamente a mi aplicación móvil por Bluetooth,  
**para** tener mi registro de peso actualizado de forma rápida y sin tener que anotarlo manualmente.

**Criterios de aceptación:**
* **Dado que** la báscula está encendida y la aplicación móvil tiene el Bluetooth activo,
* **Cuando** el usuario se sube a la báscula y la lectura del peso se estabiliza en menos de 3 segundos,
* **Entonces** la báscula debe transmitir los datos por BLE y la App debe mostrarlos en pantalla en menos de 2 segundos.

---

### HU-02: Generación de recomendaciones personalizadas por IA
**Como** usuario final,  
**quiero** recibir un análisis comprensible y recomendaciones de hábitos al momento de pesarme,  
**para** comprender mis métricas y saber qué acciones tomar sobre mi hidratación y nutrición diaria.

**Criterios de aceptación:**
* **Dado que** la App recibió los datos de peso y métricas del usuario vía BLE,
* **Cuando** la App envía las métricas al módulo de IA (API de LLM),
* **Entonces** el sistema debe presentar en menos de 5 segundos un reporte claro con consejos empáticos sobre consumo de agua y nutrición adaptados a su perfil.

---

### HU-03: Configuración del perfil de usuario y objetivos
**Como** usuario registrado,  
**quiero** definir mis datos básicos (edad, altura, nivel de actividad) y mi objetivo de salud (perder peso, mantener, ganar masa),  
**para** que el modelo de IA adapte sus recomendaciones a mi situación particular.

**Criterios de aceptación:**
* **Dado que** el usuario abre la sección de perfil en la aplicación,
* **Cuando** ingresa sus datos, selecciona su objetivo de salud y presiona "Guardar",
* **Entonces** la aplicación debe almacenar la configuración y utilizarla como contexto (*prompt*) en las futuras consultas con la IA.

---

### HU-04: Consulta de historial y gráficas de tendencia
**Como** usuario en control de peso,  
**quiero** visualizar un dashboard con mi historial de mediciones y gráficas de tendencia temporal,  
**para** evaluar el progreso de mis hábitos a lo largo de las semanas.

**Criterios de aceptación:**
* **Dado que** el usuario ha realizado múltiples mediciones en días o semanas anteriores,
* **Cuando** accede a la sección "Dashboard / Historial",
* **Entonces** la interfaz debe desplegar una gráfica de líneas interactiva con la evolución de su peso y un listado de las recomendaciones previas recibidas.

---

### HU-05: Calibración y tara de la celda de carga en firmware
**Como** desarrollador/administrador del sistema,  
**quiero** ejecutar una rutina de calibración del sensor HX711 en el firmware del ESP32,  
**para** garantizar que las mediciones de peso tengan un margen de error menor al 1%.

**Criterios de aceptación:**
* **Dado que** la báscula está conectada al entorno de pruebas de firmware,
* **Cuando** se coloca una masa patrón conocida sobre la celda de carga y se ejecuta la rutina de calibración,
* **Entonces** el firmware calcula y guarda el factor de escala en la memoria Flash del ESP32, registrando un margen de error inferior al 1% en mediciones posteriores.

---

## 10.6 — Construye tu Product Backlog priorizado

| ID | Historia de Usuario | Prioridad (MoSCoW) | Justificación |
| :--- | :--- | :--- | :--- |
| **HU-05** | Calibración y tara de la celda de carga en firmware | **Must Have** | Sin una lectura precisa de peso en la celda de carga (margen de error < 1%), la báscula pierde su función esencial de hardware. |
| **HU-01** | Captura de peso y transmisión BLE | **Must Have** | La comunicación inalámbrica ESP32-App es la columna vertebral de la arquitectura de la solución. |
| **HU-02** | Generación de recomendaciones personalizadas por IA | **Must Have** | Es la propuesta de valor diferenciadora principal del proyecto para resolver el problema central planteado. |
| **HU-03** | Configuración del perfil de usuario y objetivos | **Should Have** | Necesario para alimentar el contexto del modelo de IA y ofrecer recomendaciones realmente personalizadas. |
| **HU-04** | Consulta de historial y gráficas de tendencia | **Should Have** | Aporta un valor significativo para el seguimiento a largo plazo del usuario, estando dentro del alcance del dashboard. |
| **HU-06** | Modo offline con caché local de mediciones | **Could Have** | Permite guardar registros cuando no hay conexión a internet para consultar la IA, pero no bloquea la funcionalidad MVP del prototipo. |
| **HU-07** | Exportación de reportes PDF para nutricionistas | **Won't Have (este release)** | Se encuentra fuera del alcance del cronograma académico de 10 semanas y no es crítico para el uso básico del prototipo. |
