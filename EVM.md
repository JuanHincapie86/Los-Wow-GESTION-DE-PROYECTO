# Codelab: Gestión del Valor Ganado (EVM) y Curva S

**Proyecto:** Báscula Digital Inteligente con ESP32, Conectividad BLE y Sistema de Recomendaciones por IA  
**Materia:** Gestión de Proyectos / Proyecto Integrador — Universidad del Valle  
**Equipo:** Juan David García Arroyave, Juan José Hincapié Tascón, Alejandro Luna Hoyos, Joseph Gabriel Lerma Delgado, Sebastián Zácipa  
**Duración:** 10 Semanas (40 días de trabajo)  
**Presupuesto total (BAC):** $10,000,000 COP  

---

## 1. Paso 1 — Nuestro Presupuesto Base (BAC) y Pesos de la EDT

Para poder medir el avance real del proyecto usando EVM, primero necesitamos fijar el **BAC (Budget at Completion)**: el presupuesto total planificado. 

En nuestro caso, el cronograma suma **282 horas de esfuerzo** repartidas entre los 5 integrantes. Si valoramos esas horas a una tarifa estándar de trabajo estudiantil/junior de ~$32,000 COP/hora, más los componentes físicos que compramos (ESP32, módulo HX711, 4 celdas de carga, acrílico y cables por ~$280,000 COP) y un margen de contingencia, redondeamos el proyecto en **$10,000,000 COP**. Esto además nos facilita mucho las cuentas: **cada 1% del proyecto equivale exactamente a $100,000 COP**.

Tomando los paquetes de trabajo de nuestra EDT y los porcentajes que definimos en el documento de alcance, el presupuesto queda distribuido así:

| Código | Entregable (EDT) | Responsable | Peso (%) | Presupuesto asignado |
| :---: | :--- | :--- | :---: | :---: |
| **1.1** | Prototipo Físico y Ensamblado de Hardware | Joseph Gabriel Lerma | 10 % | $1,000,000 COP |
| **1.2** | Firmware ESP32 de Lectura y Calibración | Sebastián Zácipa | 15 % | $1,500,000 COP |
| **2.1** | Servidor BLE en Firmware ESP32 | Alejandro Luna Hoyos | 10 % | $1,000,000 COP |
| **2.2** | Aplicación Móvil Cliente y Receptor BLE | Juan José Hincapié | 15 % | $1,500,000 COP |
| **3.1** | Gestor de Perfil y Prompts de Salud | Juan David García | 8 % | $800,000 COP |
| **3.2** | Cliente API de IA y Generador de Reportes | Juan David García | 12 % | $1,200,000 COP |
| **4.1** | Base de Datos Local de Mediciones | Juan José Hincapié | 7 % | $700,000 COP |
| **4.2** | Interfaz Gráfica de Tendencias y Registros | Sebastián Zácipa | 8 % | $800,000 COP |
| **5.1** | Documentación y Artefactos de Gestión | Juan David García | 8 % | $800,000 COP |
| **5.2** | Suite de Pruebas End-to-End y Sustentación | Alejandro Luna Hoyos | 7 % | $700,000 COP |
| **Total**| **Proyecto Completo** | **Equipo Los-Wow** | **100 %** | **$10,000,000 COP** |

---

## 2. Paso 2 — Las Tres Variables Clave de EVM

EVM funciona comparando tres valores a una fecha de corte determinada:

* **PV (Planned Value):** ¿Cuánto trabajo debíamos tener listo para hoy según el plan?
* **EV (Earned Value):** ¿Cuánto trabajo terminamos y nos aceptaron de verdad?
* **AC (Actual Cost):** ¿Cuánto nos hemos gastado en plata y horas hasta hoy?

---

### Variable 1: PV (Valor Planificado)

Es simplemente lo que dice el cronograma. Si dijimos que para cierta semana debíamos tener listos tales entregables, sumamos sus presupuestos y ese es nuestro PV.

$$\text{PV} = \% \text{ planificado acumulado} \times \text{BAC}$$

#### Nuestro caso en la Semana 5:
Para la semana 5, según el cronograma ya debían estar terminados:
* 1.1 Prototipo físico (10%)
* 1.2 Firmware de calibración (15%)
* 2.1 Servidor BLE en el ESP32 (10%)
* 2.2 App móvil con recepción BLE (15%)
* 5.1 Documentación de gestión (la mitad hecha: 4%)

Sumando esos porcentajes tenemos el $54\%$ del proyecto:

$$\text{PV}_{\text{Semana 5}} = 54\% \times \$10,000,000 = \mathbf{\$5,400,000\text{ COP}}$$

Esto significa: *"Para la semana 5, el plan decía que debíamos haber entregado $5,400,000 COP en trabajo terminado."*

---

### Variable 2: EV (Valor Ganado)

Aquí no cuenta lo que "casi terminamos", sino lo que está **terminado y aceptado** según los criterios de aceptación de la EDT. 

Usamos la **regla 0/100**:
* Si el entregable está completo y funciona según lo pactado: ganas el **100%**.
* Si está a medias (así sea al 80% o 90%) o falla en las pruebas: ganas el **0%**.

Esto evita engañarnos con la típica frase de *"ya casi está listo"* cuando en realidad todavía no funciona.

#### Qué pasó realmente en la Semana 5:
Revisamos entregable por entregable:
* **1.1 Prototipo físico:** El circuito quedó soldado en la estructura acrílica y no se desconecta. **Aceptado (100%)** $\rightarrow \$1,000,000$.
* **1.2 Firmware ESP32:** Se calibró con pesas patrón y el error fue menor al 1%. **Aceptado (100%)** $\rightarrow \$1,500,000$.
* **2.1 Servidor BLE:** El ESP32 emite la señal Bluetooth y los servicios GATT correctamente. **Aceptado (100%)** $\rightarrow \$1,000,000$.
* **2.2 App móvil:** Juan José ya tenía armada la interfaz en Flutter/Android, pero la app perdía paquetes al conectarse con el ESP32. Como el criterio de aceptación exigía *transmisión estable sin pérdidas*, **no se pudo aceptar**. Con regla 0/100, **EV = $0**.
* **5.1 Documentación:** Se validaron los entregables del repositorio hasta la fecha: **Aceptado** $\rightarrow \$400,000$.

$$\text{EV}_{\text{Semana 5}} = \$1,000,000 + \$1,500,000 + \$1,000,000 + \$0 + \$400,000 = \mathbf{\$3,900,000\text{ COP}}\text{ (39\%)}$$

El equipo solo logró $39\%$ de valor real frente al $54\%$ que teníamos planeado.

---

### Variable 3: AC (Costo Real)

Es la plata que de verdad se gastó, sin importar si las cosas salieron bien o mal a la primera. Incluye las horas que le metimos al proyecto más las compras físicas.

#### Lo que gastamos hasta la Semana 5:
* Entre los 5 integrantes le dedicamos **160 horas** de trabajo durante esas 5 semanas (incluyendo noches enteras tratando de arreglar el bug del Bluetooth). A $32,000 COP/hora $= \$5,120,000\text{ COP}$.
* Compra de hardware (ESP32, celdas de carga, HX711, acrílico y cables): $\$280,000\text{ COP}$.
* Pruebas preliminares con la API de OpenAI/Gemini: $\$50,000\text{ COP}$.

$$\text{AC}_{\text{Semana 5}} = \$5,120,000 + \$280,000 + \$50,000 = \mathbf{\$5,450,000\text{ COP}}$$

---

### Comparando las tres variables en la Semana 5

| Variable | Valor | ¿Qué significa en palabras sencillas? |
| :--- | :---: | :--- |
| **PV** (Plan) | **$5,400,000 COP** | Lo que debíamos haber alcanzado según el cronograma. |
| **EV** (Logro real) | **$3,900,000 COP** | Lo que de verdad quedó terminado y aceptado. |
| **AC** (Lo gastado) | **$5,450,000 COP** | Lo que nos costó en horas y componentes llegar hasta aquí. |

**Conclusión del equipo:**
* **Estamos atrasados ($EV < PV$):** Nos faltan $\$1,500,000$ en entregables atrasados. El problema con la App móvil nos frenó la ruta crítica y no podemos conectar la IA ni la base de datos hasta que el Bluetooth funcione bien.
* **Estamos gastando más de la cuenta ($AC > EV$):** Gastamos $\$5,450,000$ para conseguir apenas $\$3,900,000$ de valor aceptado. Ese retrabajo en el código del Bluetooth nos costó tiempo y esfuerzo extra.

---

## 3. Paso 3 — La Curva S: Viendo el Proyecto en el Tiempo

La Curva S es la gráfica que muestra cómo van subiendo el **PV**, el **EV** y el **AC** semana a semana. 

En nuestro proyecto de la báscula se ve claramente la forma de "S":
1. **Al principio vamos despacio (Semanas 1–2):** Mientras armamos el repositorio, compramos los sensores y armamos la estructura física ($10\%$ del proyecto).
2. **En la mitad le metemos el acelerador (Semanas 3–7):** Es la parte más pesada: programar el firmware del ESP32, la app móvil, conectar la IA y guardar datos en SQLite ($75\%$ del proyecto).
3. **Al final volvemos a desacelerar (Semanas 8–10):** Quedan los retoques de la interfaz, probar todo junto de punta a punta y preparar la sustentación ($15\%$ del proyecto).

---

### Cómo construimos las tablas

#### Paso A: Lo de cada semana por separado (valores periódicos)

Tomando como corte actual la **Semana 7** (las semanas 8 a 10 son lo que tenemos proyectado a futuro):

| Semana | Qué se trabajó esa semana | PV semanal | EV semanal | AC semanal |
| :---: | :--- | :---: | :---: | :---: |
| **1** | Compra de materiales y setup inicial | $500,000 | $500,000 | $480,000 |
| **2** | Ensamble del prototipo físico (1.1) | $500,000 | $500,000 | $540,000 |
| **3** | Firmware de lectura y calibración (1.2) | $1,500,000 | $1,500,000 | $1,580,000 |
| **4** | Servidor BLE en el ESP32 (2.1) | $1,000,000 | $1,000,000 | $1,100,000 |
| **5** | App móvil (2.2) y documentación (5.1) | $1,900,000 | $400,000 | $1,750,000 |
| **6** | Arreglo del BLE en la App (2.2) y Prompts (3.1) | $1,500,000 | $1,500,000 | $1,650,000 |
| **7** | Integración API de IA (3.2) y BD local (4.1) | $1,600,000 | $1,900,000 | $1,700,000 |
| **8** | Dashboard final (4.2) y cierre de doc (5.1) | $800,000 | — | — |
| **9** | Pruebas integradas de todo el sistema (5.2) | $400,000 | — | — |
| **10**| Sustentación final y cierre (5.2) | $300,000 | — | — |

*Fíjate en la Semana 5:* Gastamos \$1,750,000 en horas, pero como la App no quedó lista, solo pudimos sumar \$400,000 de EV por la documentación. Ya en la Semana 6 se arregló el problema y ahí sí pudimos sumar el valor de la App.

---

#### Paso B: Valores acumulados (los que van en la gráfica)

Para cada semana sumamos lo de esa semana más lo que ya traíamos acumulado de la anterior:

| Semana | PV Acumulado (Plan) | EV Acumulado (Real) | AC Acumulado (Gastado) | Estado |
| :---: | :---: | :---: | :---: | :--- |
| **0** | $0 | $0 | $0 | Punto de partida |
| **1** | $500,000 | $500,000 | $480,000 | Hecho |
| **2** | $1,000,000 | $1,000,000 | $1,020,000 | Hecho |
| **3** | $2,500,000 | $2,500,000 | $2,600,000 | Hecho |
| **4** | $3,500,000 | $3,500,000 | $3,700,000 | Hecho |
| **5** | $5,400,000 | $3,900,000 | $5,450,000 | Bache por problema en la App |
| **6** | $6,900,000 | $5,400,000 | $7,100,000 | Recuperando ritmo |
| **7** | **$8,500,000** | **$7,300,000** | **$8,800,000** | **Fecha de corte de hoy** |
| **8** | $9,300,000 | — | — | Plan a futuro |
| **9** | $9,700,000 | — | — | Plan a futuro |
| **10**| $10,000,000 | — | — | Meta final ($BAC) |

---

### Paso C: Cómo se ve la Curva S

Si dibujamos esto en un plano (semanas abajo y millones en el eje vertical):

```text
 $10.0M |                                                    ●  PV (Meta final: $10.0M)
        |                                               ●
        |                                          ●
  $8.5M |                                     ● (PV planificado: $8.5M)
        |                                   ▲
        |                                  ●  AC (Plata gastada: $8.8M)
  $7.0M |                             ●
        |                            ▲      ●  EV (Avance real aceptado: $7.3M)
        |                           ●  ▲
  $5.0M |                       ●     ●
        |                    ▲    ▲
        |                 ●     ●
  $3.5M |            ●    ●
        |          ●   ●
  $1.0M |     ●  ●
   $0   |  ●
        +──────────────────────────────────────────────────────────
         Sem 0   1   2   3   4   5    6    7    8    9   10
                                      ▲
                                Corte actual (S7)
```

* **Línea azul (PV):** Va completa desde el día cero hasta la semana 10 porque es nuestro plan original.
* **Línea verde (EV):** Llega hasta la semana 7. Se ve claramente cómo en la semana 5 se queda rezagada por debajo del plan.
* **Línea roja (AC):** Llega hasta la semana 7 y va por encima del valor ganado porque tuvimos que meterle más horas de las previstas al desarrollo.

---

### ¿Qué nos dice la gráfica sobre nuestro proyecto?

1. **EV por debajo de PV:** Hay una brecha de $\$1,200,000$ entre lo que deberíamos llevar y lo que tenemos aceptado. El bache de la semana 5 todavía nos pasa factura y estamos atrasados con respecto al cronograma.
2. **AC por encima de EV:** Gastamos $\$8,800,000$ para conseguir $\$7,300,000$ de avance real. El retraso nos salió caro en horas de trabajo.
3. **Alerta de presupuesto:** Como ya gastamos $\$8.8\text{M}$ y el presupuesto total es de $\$10\text{M}$, solo nos quedan $\$1,200,000$ para las últimas 3 semanas. Hay que cuidar mucho el tiempo en las pruebas finales para no pasarnos del límite.

---



---

