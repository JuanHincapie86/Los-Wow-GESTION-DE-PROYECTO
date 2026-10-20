# Acta de Constitución del Proyecto

## 1. Información General del Proyecto

| Campo | Detalle | Campo | Detalle |
| :--- | :--- | :--- | :--- |
| **Nombre del proyecto:** | Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA | **Gerente del proyecto:** | — |
| **Patrocinador:** | — | **Responsable:** | Equipo de Desarrollo de Software |
| **Cliente:** | Público general (personas adultas, personas en proceso de control de peso o salud corporal), deportistas y profesionales de la nutrición | | |
| **Fecha de inicio esperada:** | Septiembre de 2026 | **Fecha de finalización esperada:** | 8 de Noviembre de 2026 (10 semanas) |

---

## 2. Definición del Problema

Las básculas digitales convencionales únicamente muestran el peso en kg/lb sin entregar contexto sobre la salud de la persona. Por su parte, las básculas "inteligentes" comerciales arrojan valores cuantitativos (como porcentaje de grasa corporal, agua o masa muscular), pero no explican qué significan ni cómo actuar al respecto. Para el público general interpretar estos números aislados resulta difícil e ineficaz. Existe una falta de herramientas accesibles que combinen hardware de medición con la potencia de la Inteligencia Artificial para transformar métricas crudas en recomendaciones claras, empáticas y personalizadas sobre hidratación, nutrición y hábitos saludables en el día a día.

---

## 3. Definición de los Objetivos

| Objetivos | Criterios de evaluación de los objetivos |
| :--- | :--- |
| **O1:** Diseñar y ensamblar un prototipo físico de báscula digital utilizando un microcontrolador ESP32, celda de carga con módulo HX711 y estimación de parámetros corporales. | Calibración precisa del peso (margen de error menor al 1%) y lectura estable de parámetros corporales en menos de 3 segundos por medición. |
| **O2:** Implementar el módulo de comunicación inalámbrica Bluetooth Low Energy (BLE) en el ESP32 para la transmisión de lecturas a la aplicación cliente. | Transferencia exitosa de paquetes de datos (peso, % de líquidos, % de grasa) al dispositivo receptor en menos de 2 segundos tras completar la medición. |
| **O3:** Integrar un modelo de Inteligencia Artificial (LLM/API de IA) que analice el perfil y métricas del usuario para generar recomendaciones personalizadas y comprensibles. | Generación automática de reportes contextualizados con sugerencias de consumo de agua, nutrición básica y hábitos de salud adaptados a las necesidades del usuario en menos de 5 segundos. |
| **O4:** Cumplir estrictamente con el cronograma académico de 10 semanas de desarrollo, pruebas e integración. | Entrega formal de los hitos estipulados semana a semana sin exceder la fecha límite de finalización del proyecto. |

---

## 4. Alcance del Proyecto

| Dentro del alcance | Fuera del alcance |
| :--- | :--- |
| • Entrega formal de los hitos estipulados semana a semana sin exceder la fecha límite de finalización del proyecto. | • Fabricación o moldeo industrial en masa de carcasa metálica/plástica (se usará prototipo en acrílico/impresión 3D). |
| • Firmware en el ESP32 para lectura de sensores, calibración de peso y servidor BLE. | • Certificación oficial de grado médico regulatorio (FDA, INVIMA, etc.). |
| • Aplicación / interfaz cliente móvil o web para recepción de datos vía BLE. | • Despliegue comercial masivo en tiendas de aplicaciones pagas. |
| • Integración del modelo de IA con prompts adaptados según el perfil del usuario (mantenimiento, pérdida de peso, hidratación, etc.). | • Mantenimiento de servidor en la nube con altos costos de infraestructura comercial. |
| • Dashboard de usuario con historial de mediciones, gráficas de tendencia e historial de recomendaciones de la IA. | |

---

## 5. Suposiciones

1. Se contará con acceso continuo a los componentes de hardware (ESP32, celdas de carga, amplificador HX711 y componentes de prototipado) durante las 10 semanas.
2. La transmisión inalámbrica Bluetooth Low Energy (BLE) mantendrá estabilidad y alcance adecuado en el entorno de pruebas.
3. Las APIs o servicios del modelo de Inteligencia Artificial seleccionado (p. ej. OpenAI, Google Gemini u Ollama local) estarán disponibles y responderán con latencia baja.
4. El desarrollador asignará entre 15 y 20 horas semanales dedicadas a la integración de hardware y software.

---

## 6. Restricciones

* **Plazo temporal:** Estrictamente 10 semanas por el calendario académico.
* **Presupuesto:** Bajo presupuesto
* **Recursos humanos:** Desarrollado por un único equipo
* **Infraestructura:** Limitaciones físicas y de memoria RAM/Flash nativas del microcontrolador ESP32.

---

## 7. Factores Generales de Riesgo

| Factor de riesgo | Impacto / Consecuencia | Dueño del plan de respuesta |
| :--- | :--- | :--- |
| **1. Descalibración o ruido en la celda de carga / módulo HX711.** | Lecturas erróneas de peso y métricas corporales. | Equipo de desarrollo |
| **2. Inestabilidad o desconexión en el enlace BLE entre ESP32 y la App.** | Interrupción o pérdida de paquetes de datos de medición. | Equipo de desarrollo |
| **3. Recomendaciones inadecuadas o "alucinaciones" del modelo de IA.** | Sugerencias imprecisas o poco pertinentes sobre ingesta de líquidos/salud. | Equipo de desarrollo |
| **4. Retrasos en adquisición o daño en componentes electrónicos.** | Bloqueo temporal en las pruebas del prototipo físico. | Equipo de desarrollo |
| **5. Desbordamiento de memoria o reinicios inesperados en el ESP32.** | Fallas durante la ejecución sostenida del firmware. | Equipo de desarrollo |

---

## 8. Interesados (Mínimo 10)

1. **Equipo de desarrollo:** Desarrolladores principales.
2. **Profesor de Proyecto Integrador:** Evaluador de arquitectura y software.
3. **Profesor de Gestión de Proyectos:** Evaluador de documentación, EDT y métricas ágiles.
4. **Compañeros de la Universidad:** Usuarios beta y auditores de usabilidad.
5. **Directores del Programa de Ingeniería de Sistemas (Univalle):** Interesados en la calidad académica.
6. **Población General / Usuarios Finales (adultos, personas en control de peso, personas sedentarias):** Beneficiarios principales de las recomendaciones claras sobre salud e hidratación.
7. **Nutricionistas / Consultores de Salud (Rol simulado):** Validadores de la lógica de hidratación y composición corporal.
8. **Comunidad Open Source (ESP32 / Arduino / MicroPython):** Proveedores de librerías para HX711 y stacks BLE.
9. **Proveedores de Modelos de IA (OpenAI / Google / Ollama):** Motores de procesamiento para las recomendaciones.
10. **Futuros Reclutadores Técnicos:** Interesados en el proyecto como caso de éxito profesional.

---

## 9. Hitos Principales

| Hitos principales | Plazo Estimado |
| :--- | :---: |
| **Hito 1:** Aprobación de Planificación, Arquitectura de Hardware e IA | Semana 2 |
| **Hito 2:** Calibración de Sensores y Firmware Base en ESP32 | Semana 4 |
| **Hito 3:** Comunicación BLE Funcional y App/Cliente Receptor | Semana 6 |
| **Hito 4:** Integración de la IA y Generación de Recomendaciones de Salud/Líquidos | Semana 8 |
| **Hito 5:** Pruebas Integradas End-to-End, Cierre y Sustentación | Semana 10 |
