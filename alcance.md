Codelab: Estructura de Desglose del Trabajo (EDT / WBS), OBS y Matriz RACI
Proyecto: Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA

1. Nivel 1 de la EDT y Ponderación del Esfuerzo
El proyecto se descompone en 5 entregables de Nivel 1 utilizando un enfoque mixto (componentes del producto más el bloque de gestión del proyecto). Los porcentajes asignados respetan estrictamente la Regla del 100 %:

1. Hardware y Firmware de Medición (25 %): Incluye la infraestructura física, sensorica de peso con celda HX711 y lógica de calibración.

2. Módulo BLE y Aplicación Cliente (25 %): Abarca el servidor GATT en el ESP32 y la aplicación móvil receptora.

3. Módulo de Integración con IA y Recomendaciones (20 %): Comprende el procesador de contextos/prompts y la integración con la API del LLM.

4. Dashboard e Historial de Usuario (15 %): Incluye la persistencia local de datos y la interfaz gráfica de tendencias.

5. Gestión e Integración del Proyecto (15 %): Contempla la documentación de gestión, pruebas integradas end-to-end y la sustentación académica.

Suma Total: 25 % + 25 % + 20 % + 15 % + 15 % = 100 %
## 2. Estructura de Desglose del Trabajo (EDT) 

Todos los nodos de la estructura están definidos mediante **sustantivos** (entregables verificables y no actividades con verbos) y cuentan con códigos jerárquicos únicos.


* **Báscula Digital Inteligente con IA (100 %)**
  * **1. Hardware y Firmware de Medición (25 %)**
    * 1.1 Prototipo Físico y Ensamblado de Hardware (10 %)
    * 1.2 Firmware ESP32 de Lectura y Calibración (15 %)
  * **2. Módulo BLE y Aplicación Cliente (25 %)**
    * 2.1 Servidor BLE en Firmware ESP32 (10 %)
    * 2.2 Aplicación Móvil Cliente y Receptor BLE (15 %)
  * **3. Módulo de Integración con IA y Recomendaciones (20 %)**
    * 3.1 Gestor de Perfil y Prompts de Salud (8 %)
    * 3.2 Cliente API de IA y Generador de Reportes (12 %)
  * **4. Dashboard e Historial de Usuario (15 %)**
    * 4.1 Base de Datos Local de Mediciones (7 %)
    * 4.2 Interfaz Gráfica de Tendencias y Registros (8 %)
  * **5. Gestión e Integración del Proyecto (15 %)**
    * 5.1 Documentación y Artefactos de Gestión (8 %)
    * 5.2 Suite de Pruebas End-to-End y Sustentación (7 %)
---

## 3. Diccionario de la EDT

Cada paquete de trabajo cumple con la **regla 8/80 horas** (estimaciones entre 20 y 42 horas de esfuerzo) y cuenta con un criterio de aceptación medible ("está listo cuando...").

| Código | Nombre del Paquete | Descripción | Criterio de Aceptación | Responsable | Esfuerzo (h) | Depende de |
| :--- | :--- | :--- | :--- | :--- | :---: | :---: |
| **1.1** | Prototipo Físico y Ensamblado de Hardware | Montaje del circuito eléctrico (ESP32, HX711 y celdas de carga) en la estructura mecánica en acrílico/impresión 3D[cite: 2, 3]. | Está listo cuando la estructura física sostiene la carga sin desconexiones y envía señales de voltaje estables al ESP32 en 10 mediciones seguidas. | Joseph Gabriel Lerma | 28 h | Ninguno |
| **1.2** | Firmware ESP32 de Lectura y Calibración | Código en C++/MicroPython para lectura del HX711, ejecución de tara y conversión de señal a peso en kg[cite: 3, 7]. | Está listo cuando la lectura de peso se estabiliza en menos de 3 segundos con un margen de error menor al 1 % ante masas patrón[cite: 2, 7]. | Sebastián Zácipa | 42 h | 1.1 |
| **2.1** | Servidor BLE en Firmware ESP32 | Configuración del stack BLE en el ESP32 como servidor GATT con servicios para publicar lecturas de peso[cite: 2, 3]. | Está listo cuando el servidor BLE transmite los paquetes de datos a la App en menos de 2 segundos tras estabilizar la medición[cite: 2, 7]. | Alejandro Luna Hoyos | 28 h | 1.2 |
| **2.2** | Aplicación Móvil Cliente y Receptor BLE | Interfaz cliente móvil para escaneo, conexión BLE y recepción de cargas útiles (*payloads*) de datos[cite: 3, 7]. | Está listo cuando la App se conecta al ESP32 vía BLE y despliega el peso medido en pantalla sin pérdidas de conexión[cite: 7]. | Juan José Hincapié | 42 h | 2.1 |
| **3.1** | Gestor de Perfil y Prompts de Salud | Módulo de captura de datos del usuario (edad, altura, metas) y construcción del prompt contextual para el LLM[cite: 3, 7]. | Está listo cuando la App almacena la configuración de usuario y genera la estructura JSON del prompt con disclaimers de salud[cite: 7]. | Juan David García | 22 h | 2.2 |
| **3.2** | Cliente API de IA y Generador de Reportes | Integración cliente REST para consumo de API de IA (OpenAI/Gemini/Ollama) y procesamiento del texto de salida[cite: 3, 7]. | Está listo cuando el sistema presenta un reporte con consejos de hidratación y hábitos en menos de 5 segundos tras recibir el peso[cite: 2, 7]. | Juan David García | 34 h | 3.1 |
| **4.1** | Base de Datos Local de Mediciones | Esquema de persistencia local (SQLite/Room) para guardar lecturas de peso, fechas y respuestas históricas[cite: 7]. | Está listo cuando cada nueva lectura se almacena localmente y puede consultarse en modo offline sin perder registros[cite: 7]. | Juan José Hincapié | 20 h | 2.2 |
| **4.2** | Interfaz Gráfica de Tendencias y Registros | Vista de Dashboard en la App con gráficas temporales de evolución de peso e historial de sugerencias[cite: 3, 7]. | Está listo cuando la interfaz renderiza la gráfica de línea por semanas/meses y permite navegar en el historial de consejos[cite: 7]. | Sebastián Zácipa | 22 h | 4.1, 3.2 |
| **5.1** | Documentación y Artefactos de Gestión | Compilado de Acta de Constitución, Requisitos, EDT, RACI y Cronograma versionados en el repositorio Git[cite: 1, 7]. | Está listo cuando todos los documentos están en formato Markdown/PlantUML en la rama principal del repositorio[cite: 7]. | Juan David García | 22 h | Ninguno |
| **5.2** | Suite de Pruebas End-to-End y Sustentación | Protocolo de pruebas integradas (Hardware-BLE-App-IA) y material de presentación académica final[cite: 2, 6]. | Está listo cuando la prueba completa (peso en balanza -> lectura en App -> reporte de IA) funciona en vivo sin fallas en la semana 10[cite: 2, 6]. | Alejandro Luna Hoyos | 20 h | 1.2, 2.2, 3.2, 4.2 |

---

## 4. Estructura de la Organización (OBS) y Matriz RACI

### Estructura del Equipo (OBS)
* **Juan David García Arroyave:** Project Manager / Líder de Integración e IA[cite: 7].
* **Juan José Hincapié Tascón:** Product Owner / Líder de Desarrollo Móvil[cite: 7].
* **Alejandro Luna Hoyos:** Scrum Master / Líder de Conectividad y Calidad[cite: 7].
* **Joseph Gabriel Lerma Delgado:** Desarrollador de Hardware y Estructura[cite: 7].
* **Sebastián Zácipa:** Desarrollador de Firmware y Dashboard UI[cite: 7].
* **Profesor Evaluador / Sponsor Académico:** Evaluador de Entregables y Metodología[cite: 7].

### Matriz RACI
*Regla de control:* Cada columna (paquete de trabajo) contiene **exactamente una 'A'** (Aprobador/Responsable final)[cite: 7].

| Rol / Integrante | 1.1 | 1.2 | 2.1 | 2.2 | 3.1 | 3.2 | 4.1 | 4.2 | 5.1 | 5.2 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Juan David García (PM)** | C | I | I | C | **A** | **A** | I | C | **A** | C |
| **Juan José Hincapié (PO)** | I | I | C | **A** | R | R | **A** | R | C | C |
| **Alejandro Luna (SM)** | C | C | **A** | R | I | I | C | I | C | **A** |
| **Joseph Gabriel Lerma (Dev)** | **A** | R | C | I | I | I | I | I | R | R |
| **Sebastián Zácipa (Dev)** | R | **A** | R | I | I | I | R | **A** | R | R |
| **Profesor Evaluador (Sponsor)** | I | I | I | I | I | I | I | I | C | C |

* **R (Realiza):** Quien ejecuta el desarrollo del paquete.
* **A (Aprueba):** Responsable único por el resultado final del paquete.
* **C (Consulta):** Experto o rol al que se consulta antes o durante la ejecución.
* **I (Informa):** Rol al que se notifica el avance o finalización del entregable.

---

## 5. Lista de Verificación de Calidad

1. **¿Los hijos suman exactamente el padre en todos los niveles?** Sí. En Nivel 1 suman 100 % y cada subclase iguala exactamente el porcentaje de su nodo padre.
2. **¿Todos los nodos son entregables (sustantivos) y no actividades (verbos)?** Sí. Se definieron entidades físicas o de software ("Prototipo Físico", "Servidor BLE", "Base de Datos Local") descartando verbos como "Programar" o "Diseñar".
3. **¿Cada paquete de trabajo cae entre 8 y 80 horas?** Sí. Las cargas de trabajo varían entre 20 y 42 horas estimadas.
4. **¿Cada paquete tiene un criterio de aceptación verificable?** Sí. Se especificaron umbrales de tiempo de respuesta (< 3 s, < 2 s, < 5 s) y márgenes de precisión (< 1 %)[cite: 2, 7].
5. **¿Cada paquete tiene exactamente una 'A' en la matriz RACI?** Sí. Cada columna de la matriz posee un único aprobador directo.
6. **¿Está el bloque de gestión del proyecto?** Sí. Corresponde al entregable **5. Gestión e Integración del Proyecto** (15 % del esfuerzo)[cite: 1, 6].
7. **¿Está en formato versionable?** El diagrama PlantUML y las tablas Markdown están listos para agregarse al repositorio Git del proyecto.

```
