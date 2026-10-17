# Codelab: Cronograma, Red CPM, Ruta Crítica y Nivelación de Recursos

**Proyecto:** Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA

---

## 1. Paso 1 — Conversión de Esfuerzo a Duración

Para transformar el esfuerzo de cada paquete de trabajo de la EDT en la duración real en días de trabajo, aplicamos la fórmula de conversión considerando una jornada laboral efectiva de **6 horas útiles por día** y la asignación de **1 persona por tarea**.

**Fórmula de conversión:**

> **Duración (días)** = Esfuerzo (horas) / (Personas × Horas útiles por día)

| Código | Nombre del Paquete | Esfuerzo (h) | Responsable (OBS) | Cálculo de Duración | Duración (Días) |
| :--- | :--- | :---: | :--- | :---: | :---: |
| **1.1** | Prototipo Físico y Ensamblado de Hardware | 30 h | Joseph Gabriel Lerma | 30 / (1 × 6) | **5 días** |
| **1.2** | Firmware ESP32 de Lectura y Calibración | 42 h | Sebastián Zácipa | 42 / (1 × 6) | **7 días** |
| **2.1** | Servidor BLE en Firmware ESP32 | 24 h | Alejandro Luna Hoyos | 24 / (1 × 6) | **4 días** |
| **2.2** | Aplicación Móvil Cliente y Receptor BLE | 42 h | Juan José Hincapié | 42 / (1 × 6) | **7 días** |
| **3.1** | Gestor de Perfil y Prompts de Salud | 24 h | Juan David García | 24 / (1 × 6) | **4 días** |
| **3.2** | Cliente API de IA y Generador de Reportes | 36 h | Juan David García | 36 / (1 × 6) | **6 días** |
| **4.1** | Base de Datos Local de Mediciones | 18 h | Juan José Hincapié | 18 / (1 × 6) | **3 días** |
| **4.2** | Interfaz Gráfica de Tendencias y Registros | 24 h | Sebastián Zácipa | 24 / (1 × 6) | **4 días** |
| **5.1** | Documentación y Artefactos de Gestión | 24 h | Juan David García | 24 / (1 × 6) | **4 días** |
| **5.2** | Suite de Pruebas End-to-End y Sustentación | 18 h | Alejandro Luna Hoyos | 18 / (1 × 6) | **3 días** |

---

## 2. Paso 2 — Matriz de Dependencias Justificadas

Todas las dependencias definidas son de tipo **Fin a Comienzo (FS)** y están justificadas por razones estrictamente técnicas o de lógica de desarrollo:

| Código | Tarea del Cronograma | Predecesoras | Tipo | Justificación Técnica de la Dependencia |
| :--- | :--- | :---: | :---: | :--- |
| **1.1** | Prototipo Físico y Ensamblado de Hardware | Ninguna | — | Inicio de la ruta de hardware. |
| **1.2** | Firmware ESP32 de Lectura y Calibración | **1.1** | FS | Se requiere el circuito físico montado (ESP32 y HX711) para leer señales analógicas y calibrar la tara con masas patrón[cite: 2, 7]. |
| **2.1** | Servidor BLE en Firmware ESP32 | **1.2** | FS | El servidor BLE requiere la rutina de lectura de peso funcional en el firmware para empaquetar y notificar las métricas[cite: 2, 7]. |
| **2.2** | Aplicación Móvil Cliente y Receptor BLE | **2.1** | FS | La App móvil requiere el servidor GATT emitiendo señal BLE para verificar la sincronización y recepción de cargas útiles[cite: 3, 7]. |
| **3.1** | Gestor de Perfil y Prompts de Salud | **2.2** | FS | Requiere la interfaz móvil lista para capturar el perfil del usuario (edad, metas) y construir la estructura JSON del prompt[cite: 3, 7]. |
| **3.2** | Cliente API de IA y Generador de Reportes | **3.1** | FS | La solicitud a la API del LLM depende directamente de la plantilla de prompt contextualizada generada en el módulo 3.1[cite: 3, 7]. |
| **4.1** | Base de Datos Local de Mediciones | **2.2** | FS | El módulo de persistencia local SQLite/Room requiere que la App reciba las lecturas vía BLE para almacenarlas en el historial[cite: 7]. |
| **4.2** | Interfaz Gráfica de Tendencias y Registros | **3.2, 4.1** | FS | El Dashboard interactivo requiere los datos persistidos localmente (4.1) y la respuesta del modelo de IA (3.2) para renderizar gráficas y recomendaciones[cite: 3, 7]. |
| **5.1** | Documentación y Artefactos de Gestión | Ninguna | — | Tarea transversal iniciada en paralelo desde el comienzo del proyecto. |
| **5.2** | Suite de Pruebas End-to-End y Sustentación | **4.2, 5.1** | FS | Requiere el sistema completamente integrado en UI (4.2) y los artefactos de gestión cerrados (5.1) para la sustentación académica final[cite: 1, 6]. |

---
## 3. Pasos 3 y 4 — Recorrido Hacia Adelante, Recorrido Hacia Atrás y Holgura

Con base en el método de la ruta crítica (CPM), se calculan los tiempos tempranos (**ES**, **EF**), los tiempos tardíos (**LS**, **LF**) y la **Holgura (H = LS - ES = LF - EF)**:

* **Recorrido Hacia Adelante:** `ES = máx(EF de predecesoras)`, `EF = ES + Duración`.
* **Recorrido Hacia Atrás:** `LF = mín(LS de sucesoras)`, `LS = LF - Duración`.

| Código | Tarea del Cronograma | Dur. (d) | Predecesoras | ES | EF | LS | LF | Holgura (H) | ¿Crítica? |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1.1** | Prototipo Físico y Ensamblado | 5 | — | 0 | 5 | 0 | 5 | **0** | **Sí** |
| **1.2** | Firmware Lectura y Calibración | 7 | 1.1 | 5 | 12 | 5 | 12 | **0** | **Sí** |
| **2.1** | Servidor BLE en ESP32 | 4 | 1.2 | 12 | 16 | 12 | 16 | **0** | **Sí** |
| **2.2** | App Móvil Cliente y BLE | 7 | 2.1 | 16 | 23 | 16 | 23 | **0** | **Sí** |
| **3.1** | Gestor de Perfil y Prompts | 4 | 2.2 | 23 | 27 | 23 | 27 | **0** | **Sí** |
| **3.2** | Cliente API de IA y Reportes | 6 | 3.1 | 27 | 33 | 27 | 33 | **0** | **Sí** |
| **4.1** | Base de Datos Local | 3 | 2.2 | 23 | 26 | 30 | 33 | **7** | No |
| **4.2** | Interfaz Gráfica de Tendencias | 4 | 3.2, 4.1 | 33 | 37 | 33 | 37 | **0** | **Sí** |
| **5.1** | Documentación y Gestión | 4 | — | 0 | 4 | 33 | 37 | **33** | No |
| **5.2** | Suite Pruebas E2E y Sustentación | 3 | 4.2, 5.1 | 37 | 40 | 37 | 40 | **0** | **Sí** |

---

> **Duración Total del Proyecto:** 40 días hábiles (equivalente a 8 semanas lectivas de trabajo efectivo).

---
## 4. Paso 5 — Ruta Crítica del Proyecto

La **Ruta Crítica** corresponde a la secuencia continua de tareas cuya holgura es igual a **0**:

> **Ruta Crítica:** 1.1 ➔ 1.2 ➔ 2.1 ➔ 2.2 ➔ 3.1 ➔ 3.2 ➔ 4.2 ➔ 5.2

```
   [1.1] 5d ➔ [1.2] 7d ➔ [2.1] 4d ➔ [2.2] 7d ➔ [3.1] 4d ➔ [3.2] 6d ➔ [4.2] 4d ➔ [5.2] 3d
                                      │                               ▲
                                      └─────► [4.1] 3d (H=7) ─────────┘
   [5.1] 4d (H=33) ───────────────────────────────────────────────────┘
```

### Consecuencias Prácticas
1. **Control Foco:** Las tareas de la ruta crítica representan un total de **40 días**. Cualquier retraso de 1 día en `1.2` o `3.2` retrasa la entrega final del proyecto exactamente en 1 día.
2. **Tareas con Margen:** La tarea **4.1 (Base de Datos Local)** posee **7 días de holgura**, permitiendo iniciarla hasta el día 30 sin afectar la entrega. La tarea **5.1 (Documentación)** posee **33 días de holgura**.

---

## 5. Paso 6 — Nivelación de Recursos (Cronograma Real)

Al cruzar la red CPM con la disponibilidad real de los integrantes (OBS/RACI), se verifica que no existan sobreasignaciones paralelas:

```
Días:    0    5   12   16   23   26   27   33   37  40
         ├────┼────┼────┼────┼────┼────┼────┼────┼────┤
Joseph : [1.1]
Sebas  :      [1.2]                     [4.2]
Alejo  :           [2.1]                         [5.2]
Juan J :                [2.2][4.1]
Juan D : [5.1]               [3.1][3.2]
```

### Análisis de Asignaciones y Nivelación
* **Juan José Hincapié:** Ejecuta `2.2` (Días 16 al 23). En lugar de ejecutar `4.1` en paralelo, aprovecha su holgura de 7 días para realizarla secuencialmente entre los Días 23 y 26. Conflicto resuelto sin alterar la ruta crítica.
* **Juan David García:** Ejecuta `5.1` (Documentación) entre los Días 0 y 4 utilizando su holgura de 33 días, quedando totalmente disponible para desarrollar `3.1` y `3.2` secuencialmente entre los Días 23 y 33.
* **Sebastián Zácipa:** Ejecuta `1.2` (Días 5 al 12) y `4.2` (Días 33 al 37) de forma completamente desacoplada.

---

## 6. Paso 7 — Estrategias de Compresión del Cronograma

Si la entrega final debiera adelantarse de la semana 8 a la semana 6 (reducir 10 días útiles):

1. **Intensificación (Crashing):** Asignar a Sebastián Zácipa como apoyo en la tarea `2.2` (App Móvil) para reducir su duración de 7 a 4 días, e intensificar `1.2` (Firmware) reduciendo de 7 a 5 días mediante librerías Open Source probadas.
2. **Ejecución Rápida (Fast-Tracking):** Iniciar la tarea `3.1` (Gestor de Prompts) 2 días antes de que finalice `2.2` (solapamiento parcial mediante un contrato de interfaz JSON prefijado).

---

## 7. Paso 8 — Hitos del Proyecto y Línea Base

Los hitos marcan los puntos de control clave con **duración 0**:

| Código Hito | Nombre del Hito | Día Programado | Criterio de Verificación de la Línea Base |
| :---: | :--- | :---: | :--- |
| **HITO-1** | Calibración y Firmware Base Aprobado | Día 12 | Lectura de peso en celda HX711 estabilizada con error < 1 %[cite: 2, 7]. |
| **HITO-2** | Enlace BLE y App Móvil Sincronizada | Día 23 | Transferencia BLE de peso visible en pantalla móvil < 2 s[cite: 2, 7]. |
| **HITO-3** | Módulo de IA Integrado y Generador de Consejos | Día 33 | Reporte de recomendaciones de salud retornado por la API < 5 s[cite: 2, 7]. |
| **HITO-4** | Cierre de Pruebas End-to-End y Sustentación | Día 40 | Prototipo físico e interfaz operando sin fallas ante evaluadores[cite: 2, 6]. |

---
## 8. Checklist de Validación

- [x] **Conversión homogénea:** Todas las tareas expresadas en días útiles (6 h/día).
- [x] **Matriz de dependencias explícita:** Cada flecha tiene su justificación técnica documentada.
- [x] **Recorridos CPM completos:** Tiempos tempranos, tardíos y holgura calculados rigurosamente.
- [x] **Continuidad de Ruta Crítica:** Formada por tareas con holgura **0**, sumando exactamente 40 días de proyecto.
- [x] **Sin sobreasignaciones:** Integrantes asignados a tareas consecutivas sin solapamiento de horario.
- [x] **Línea Base e Hitos:** 4 hitos verificables definidos en el cronograma.
- [x] **Versionable:** Formato Markdown y texto plano listo para incluir en la rama principal de Git.
