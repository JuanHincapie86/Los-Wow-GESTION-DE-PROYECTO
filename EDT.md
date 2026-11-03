# EDT (Estructura de Desglose del Trabajo)

**Proyecto:** Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA
**Materia:** Gestión de Proyectos / Proyecto Integrador, Universidad del Valle
**Equipo:** Juan David García (Project Manager), Juan José Hincapié (Product Owner), Alejandro Luna (Scrum Master), Sebastián Zácipa (Desarrollador)
**Fuente de alcance:** Acta de constitución (septiembre a 8 de noviembre de 2026, 10 semanas)

---

## 1. Convenciones

- **Nivel 1:** proyecto completo (`1.0`).
- **Nivel 2:** entregables principales (`1.1` a `1.7`).
- **Nivel 3:** paquetes de trabajo, el nivel más bajo (`1.1.1`, `1.2.1`, …). Son estimables, asignables y verificables.
- Todos los nodos están redactados como **sustantivos** (entregables), no como actividades.
- El **% de peso** de cada nodo es una estimación del esfuerzo respecto a su padre. En cada nivel, los hijos suman **100 %** del padre.

---

## 2. Jerarquía del EDT

- **1.0 Báscula Digital Inteligente con IA** (100 %)
  - **1.1 Gestión del proyecto** (15 %)
    - 1.1.1 Acta de constitución (10 %)
    - 1.1.2 EDT y diccionario del EDT (15 %)
    - 1.1.3 Cronograma CPM con nivelación de recursos (20 %)
    - 1.1.4 Presupuesto y estimación de esfuerzo (15 %)
    - 1.1.5 Registros de riesgos e interesados (15 %)
    - 1.1.6 Informes de seguimiento e hitos (15 %)
    - 1.1.7 Repositorio Git versionado (10 %)
  - **1.2 Prototipo físico de hardware** (15 %)
    - 1.2.1 Esquema electrónico (25 %)
    - 1.2.2 Estructura mecánica en acrílico o impresión 3D (30 %)
    - 1.2.3 Circuito ensamblado (ESP32, HX711, 4 celdas de carga, batería) (45 %)
  - **1.3 Firmware del ESP32** (20 %)
    - 1.3.1 Módulo de lectura y filtrado de señal (25 %)
    - 1.3.2 Módulo de calibración y tara automática (25 %)
    - 1.3.3 Módulo de estimación de parámetros corporales (20 %)
    - 1.3.4 Servidor BLE GATT (30 %)
  - **1.4 Aplicación cliente** (20 %)
    - 1.4.1 Módulo de recepción BLE (25 %)
    - 1.4.2 Gestor de perfil de usuario (20 %)
    - 1.4.3 Base de datos local de mediciones y recomendaciones (20 %)
    - 1.4.4 Dashboard de historial y tendencias (35 %)
  - **1.5 Módulo de inteligencia artificial** (15 %)
    - 1.5.1 Plantillas de prompts por perfil de usuario (30 %)
    - 1.5.2 Cliente de la API del modelo de IA (30 %)
    - 1.5.3 Generador de reportes de recomendaciones (25 %)
    - 1.5.4 Salvaguardas de contenido (avisos legales y validación de respuestas) (15 %)
  - **1.6 Pruebas e integración** (10 %)
    - 1.6.1 Plan y casos de prueba (15 %)
    - 1.6.2 Informe de pruebas de hardware (20 %)
    - 1.6.3 Informe de pruebas de comunicación BLE (15 %)
    - 1.6.4 Informe de pruebas del módulo de IA (15 %)
    - 1.6.5 Informe de pruebas end-to-end (35 %)
  - **1.7 Documentación y cierre** (5 %)
    - 1.7.1 Documentación técnica y manual de usuario (50 %)
    - 1.7.2 Presentación y video de sustentación (35 %)
    - 1.7.3 Informe de cierre y lecciones aprendidas (15 %)

---

## 3. Verificación de la regla del 100 %

| Padre | Hijos | Suma |
|---|---|---|
| 1.0 | 1.1 (15) + 1.2 (15) + 1.3 (20) + 1.4 (20) + 1.5 (15) + 1.6 (10) + 1.7 (5) | **100 %** |
| 1.1 | 10 + 15 + 20 + 15 + 15 + 15 + 10 | **100 %** |
| 1.2 | 25 + 30 + 45 | **100 %** |
| 1.3 | 25 + 25 + 20 + 30 | **100 %** |
| 1.4 | 25 + 20 + 20 + 35 | **100 %** |
| 1.5 | 30 + 30 + 25 + 15 | **100 %** |
| 1.6 | 15 + 20 + 15 + 15 + 35 | **100 %** |
| 1.7 | 50 + 35 + 15 | **100 %** |

### Trazabilidad con el Acta

| Elemento del Acta | Cubierto en el EDT |
|---|---|
| O1: prototipo físico, calibración < 1 %, lectura < 3 s, estimación de parámetros corporales | 1.2, 1.3.1, 1.3.2, 1.3.3, 1.6.2 |
| O2: comunicación BLE, entrega < 2 s | 1.3.4, 1.4.1, 1.6.3 |
| O3: IA con recomendaciones personalizadas, < 5 s, riesgo de alucinaciones | 1.4.2, 1.5, 1.6.4 |
| O4: cronograma de 10 semanas, hitos semanales | 1.1.3, 1.1.6 |
| Alcance: firmware, app cliente, prompts por perfil, dashboard con historial de mediciones y recomendaciones | 1.3, 1.4, 1.5 |
| Alcance: prototipo en acrílico o impresión 3D | 1.2.2 |
| Riesgos e interesados (mínimo 10) | 1.1.5 |
| Hito 5: pruebas E2E, cierre y sustentación | 1.6.5, 1.7 |
| **Fuera de alcance:** fabricación en masa, certificación médica (FDA, INVIMA), despliegue comercial en tiendas, servidor cloud de alto costo | No incluido en el EDT |

### Mutua exclusividad (fronteras entre paquetes sensibles)

- **1.3.4 vs 1.4.1:** el servidor BLE (ESP32) y el receptor BLE (app) son paquetes distintos, cada uno en su lado del enlace.
- **1.4.2 vs 1.5.1:** el perfil de usuario (captura y almacenamiento de datos) es independiente de las plantillas de prompts (texto que consume ese perfil).
- **1.4.3 vs 1.4.4:** la base de datos solo persiste datos; el dashboard solo los visualiza.
- **1.6.x vs 1.2 a 1.5:** las pruebas formales y sus informes están solo en 1.6. Las verificaciones de cada módulo durante su construcción se incluyen en el paquete que lo produce.
- **1.1.6 vs 1.1.3:** el cronograma es la línea base (planificación) y los informes miden su cumplimiento (control).

---

## 4. Diccionario del EDT (paquetes de trabajo del nivel más bajo)

| Código | Paquete de trabajo | Descripción y criterio de terminado |
|---|---|---|
| 1.1.1 | Acta de constitución | Documento con problema, objetivos, alcance, supuestos, restricciones, riesgos, interesados e hitos. Está terminado cuando queda aprobado por el docente. |
| 1.1.2 | EDT y diccionario del EDT | Este documento con jerarquía codificada y descripciones. Está terminado cuando se entrega en el repositorio. |
| 1.1.3 | Cronograma CPM con nivelación de recursos | Red de actividades con duraciones, ruta crítica, holguras y asignación de recursos. Está terminado cuando el cronograma es consistente con el EDT. |
| 1.1.4 | Presupuesto y estimación de esfuerzo | BOM del prototipo en COP, reserva de contingencia y horas por integrante. Está terminado cuando totales y horas están validados. |
| 1.1.5 | Registros de riesgos e interesados | Registro con los 5 riesgos del Acta (impacto, responsable, respuesta) y los 10 interesados identificados. Está terminado cuando se completa y es revisado por el equipo. |
| 1.1.6 | Informes de seguimiento e hitos | Reportes periódicos de avance frente a la línea base y verificación de criterios de aceptación de cada hito. Está terminado cuando existe un informe por hito. |
| 1.1.7 | Repositorio Git versionado | Repositorio con código, documentos de gestión e historial de commits en la rama principal. Está terminado cuando contiene todos los entregables. |
| 1.2.1 | Esquema electrónico | Diagrama de conexiones entre ESP32, HX711, celdas de carga y batería. Está terminado cuando está revisado y listo para ensamblar. |
| 1.2.2 | Estructura mecánica | Base y soporte en acrílico o impresión 3D que aloja las 4 celdas de carga. Está terminado cuando soporta peso sin deformación. |
| 1.2.3 | Circuito ensamblado | Prototipo con componentes cableados y alimentados por batería. Está terminado cuando el ESP32 enciende y el HX711 entrega señal. |
| 1.3.1 | Módulo de lectura y filtrado | Código que adquiere la señal del HX711 y reduce el ruido. Está terminado cuando las lecturas son estables en reposo. |
| 1.3.2 | Módulo de calibración y tara | Código de tara automática y calibración con masas patrón. Está terminado cuando el error es < 1 % y la lectura se estabiliza en < 3 s. |
| 1.3.3 | Módulo de estimación de parámetros corporales | Código que calcula % de líquidos y % de grasa a partir de las métricas disponibles. Está terminado cuando entrega los valores junto al peso en cada medición. |
| 1.3.4 | Servidor BLE GATT | Servicio y características BLE que publican peso, % de líquidos y % de grasa. Está terminado cuando un cliente BLE recibe el paquete completo. |
| 1.4.1 | Módulo de recepción BLE | Componente de la app que escanea, conecta y recibe el paquete de medición. Está terminado cuando el dato llega a pantalla en < 2 s. |
| 1.4.2 | Gestor de perfil de usuario | Pantallas y almacenamiento del perfil (edad, sexo, estatura, meta de salud). Está terminado cuando el perfil se crea, se edita y se usa en las recomendaciones. |
| 1.4.3 | Base de datos local | Esquema SQLite para mediciones y recomendaciones, con modo offline. Está terminado cuando guarda y consulta registros sin conexión. |
| 1.4.4 | Dashboard de historial y tendencias | Vistas con historial de mediciones, gráficas de tendencia e historial de recomendaciones. Está terminado cuando muestra los datos guardados correctamente. |
| 1.5.1 | Plantillas de prompts por perfil | Conjunto de prompts parametrizados (mantenimiento, pérdida de peso, hidratación, etc.). Está terminado cuando cada perfil produce un prompt válido. |
| 1.5.2 | Cliente de la API del modelo de IA | Módulo que envía el prompt a la API (OpenAI, Gemini u Ollama) y recibe la respuesta. Está terminado cuando responde en < 5 s y maneja errores de red. |
| 1.5.3 | Generador de reportes de recomendaciones | Módulo que convierte la respuesta del modelo en un reporte legible sobre hidratación, nutrición y hábitos. Está terminado cuando el reporte se muestra y se guarda en el historial. |
| 1.5.4 | Salvaguardas de contenido | Aviso de que no sustituye un diagnóstico médico y validaciones básicas contra respuestas inadecuadas. Está terminado cuando todo reporte incluye el aviso y las pruebas de validación pasan. |
| 1.6.1 | Plan y casos de prueba | Documento con casos, datos de prueba y criterios de aceptación por indicador. Está terminado cuando cubre los KPIs del Acta. |
| 1.6.2 | Informe de pruebas de hardware | Resultados de precisión de peso (< 1 %) y tiempo de estabilización (< 3 s) con masas patrón. Está terminado cuando se documentan los resultados y se decide si se aprueba. |
| 1.6.3 | Informe de pruebas BLE | Mediciones de latencia (< 2 s), estabilidad de conexión y pérdida de paquetes. Está terminado cuando se documentan los resultados. |
| 1.6.4 | Informe de pruebas de IA | Tiempos de respuesta (< 5 s) y revisión de la pertinencia de las recomendaciones. Está terminado cuando se documentan los resultados. |
| 1.6.5 | Informe de pruebas end-to-end | Ejecución completa (pesaje, BLE, perfil, IA, historial) sin fallas. Está terminado cuando el flujo completo se valida y se documentan los defectos. |
| 1.7.1 | Documentación técnica y manual de usuario | Guía de arquitectura, instalación, calibración y uso. Está terminado cuando un tercero puede reproducir el prototipo con ella. |
| 1.7.2 | Presentación y video de sustentación | Presentación del proyecto y video de demostración de máximo 10 minutos. Está terminado cuando ambos están listos para la entrega. |
| 1.7.3 | Informe de cierre y lecciones aprendidas | Resumen de resultados frente a objetivos, desviaciones y aprendizajes. Está terminado cuando es aprobado por el equipo. |

---

## 5. Correspondencia con el cronograma CPM

| Tarea del cronograma | Paquetes del EDT |
|---|---|
| 1.1 Prototipo físico y ensamblado | 1.2.1, 1.2.2, 1.2.3 |
| 1.2 Firmware de lectura y calibración | 1.3.1, 1.3.2, 1.3.3 |
| 2.1 Servidor BLE | 1.3.4 |
| 2.2 App móvil y receptor BLE | 1.4.1 |
| 3.1 Gestor de perfil y prompts | 1.4.2, 1.5.1 |
| 3.2 Cliente API de IA y reportes | 1.5.2, 1.5.3, 1.5.4 |
| 4.1 Base de datos local | 1.4.3 |
| 4.2 Interfaz de tendencias y registros | 1.4.4 |
| 5.1 Documentación y gestión | 1.1.x, 1.7.1, 1.7.3 |
| 5.2 Pruebas end-to-end y sustentación | 1.6.x, 1.7.2 |
