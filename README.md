# Proyecto: Análisis de Movilidad y Patrones de Uso en Sistemas de Bicicletas Compartidas (Capital Bikeshare)

**Asignatura:** EIN092B Visualización de Datos  
**Profesor:** Jesús A. Parra  
**Institución:** Universidad Técnica Federico Santa María (UTFSM)  
**Semestre:** 2026-II  
**Entregable:** Avance 1 - Formulación del Proyecto  

---

## 📋 Diapositiva 1: Proyecto, Problema y Motivación

* **Nombre del Proyecto:** Análisis de Movilidad y Patrones de Uso en Sistemas de Bicicletas Compartidas (*Capital Bikeshare*).
* **Integrantes:** Martin Lobos *(y equipo)*.
* **Contexto:** Las zonas urbanas enfrentan serios desafíos de congestión vehicular y contaminación. Los sistemas de micro-movilidad urbana, como las bicicletas compartidas, han emergido como una solución ecológica, flexible y sustentable para el transporte diario.
* **Problemática General:** Para que el sistema sea eficiente y rentable, los operadores necesitan entender las marcadas diferencias de comportamiento entre usuarios registrados (de uso diario/rutinario) y casuales (de uso turístico/recreativo). Esto afecta directamente la logística de redistribución de bicicletas entre estaciones (*rebalancing*), la disponibilidad de flotas y el mantenimiento preventivo.
* **¿Por qué vale la pena estudiar este problema?:** Permite optimizar la toma de decisiones operativas y logísticas del sistema de transporte. Al comprender los patrones de demanda temporal y geográfica de cada perfil de usuario, es posible prevenir estaciones desabastecidas o colapsadas, mejorar la experiencia de viaje urbana y promover una movilidad sostenible fundamentada en datos.

---

## 🎯 Diapositiva 2: Pregunta y Alcance

* **Pregunta Principal:**  
  > ¿De qué manera varían la demanda, la duración de los trayectos y los patrones temporales de uso del sistema de bicicletas compartidas entre usuarios registrados y casuales según la hora, el día de la semana y las estaciones de origen/destino?
* **Fenómeno Específico a Estudiar:** Patrones de comportamiento, dinámica de viajes y diferencias en el uso del servicio según el tipo de usuario (suscritos vs. casuales).
* **Población, Región o Contexto:** Usuarios del sistema de micro-movilidad e infraestructura de estaciones de bicicletas compartidas (*Capital Bikeshare*).
* **Período de Análisis:** Ciclo diario por horas (0 a 23 hrs) y diferenciación entre días laborales (*weekdays*) y fines de semana (*weekends*) dentro del registro histórico del dataset.
* **Límites Iniciales del Proyecto:**
  - Se analizarán exclusivamente los viajes válidos con una duración igual o superior a 60 segundos.
  - Quedan fuera del alcance las rutas de mantenimiento técnico/inspección de personal y los trayectos hacia o desde bodegas/estaciones de prueba.
  - En esta etapa no se contemplan variables meteorológicas externas ni modelos predictivos en tiempo real.

---

## 📐 Diapositiva 3: Estructura X, Y y T

### Identificación de Componentes
* **$X$ (Variables Explicativas / Información Disponible):**
  - Tipo de usuario (`Member Type`: Registrado vs. Casual).
  - Estación de origen y estación de destino (`Start Station`, `End Station`).
  - Identificador del vehículo (`Bike Number`).
  - Componentes de tiempo extraídos (Hora del día y día de la semana).
* **$Y$ (Objetivo / Fenómeno de Interés):**
  - Demanda total y volumen de viajes por intervalo.
  - Duración de los trayectos (`Duration`).
  - Flujos y concentración de viajes entre pares de estaciones.
* **$T$ (Contexto Temporal):**
  - Distribución por horas del día (0 a 23 hrs) y comparativa entre días hábiles y fines de semana dentro del período cubierto por el dataset.

### Integración en la Pregunta del Proyecto
La estructura conecta los datos de entrada **($X$)** con el fenómeno analizado **($Y$)** en un período acotado **($T$)**: explica de qué forma las características del usuario, ubicación e identificación de bicicletas **($X$)** influyen en la demanda y duración del trayecto **($Y$)** a lo largo del ciclo diario y semanal **($T$)**.

---

## 📊 Diapositiva 4: Dataset y Narrativa Inicial

* **Fuente de los Datos:** Registro histórico procesado del sistema *Capital Bikeshare* (Washington D.C.).
* **Cantidad Aproximada de Registros:** ~650.000 filas / trayectos registrados.
* **Unidad de Observación:** Un viaje individual realizado en el sistema con una duración $\ge 60$ segundos.
* **Cobertura Temporal y Espacial:** Cobertura espacial urbana basada en la red de estaciones del sistema; cobertura temporal continua por horas y días según los registros del dataset.
* **Principales Variables:**
  - `Duration`: Duración del trayecto (en segundos).
  - `Start Date` / `End Date`: Timestamp de inicio y término del viaje.
  - `Start Station` / `End Station`: Nombre e ID de las estaciones de origen y destino.
  - `Bike Number`: Identificador único de la bicicleta.
  - `Member Type`: Tipo de usuario (*Registered* vs. *Casual*).

### Muestra Representativa del Dataset
| Duration | Start Date | End Date | Start Station | End Station | Bike Number | Member Type |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 623 | 2026-07-01 08:15:00 | 2026-07-01 08:25:23 | 31101 - 14th & V St NW | 31200 - Massachusetts Ave | W00124 | Registered |
| 1450 | 2026-07-01 14:30:10 | 2026-07-01 14:54:20 | 31201 - Smithsonian Metro | 31202 - Lincoln Memorial | W00892 | Casual |

### Narrative Inicial
* Los datos capturan la **"respiración urbana"** de la ciudad a través del transporte sobre ruedas.
* La historia esperada revelará dos comportamientos urbanos opuestos: por un lado, la rutina eficiente y acelerada del trabajador/estudiante (*Registered*) enfocado en horas punta de desplazamiento laboral; por otro lado, el ritmo pausado del visitante o ciclista de fin de semana (*Casual*) enfocado en rutas turísticas o recreativas de mayor duración.

---

## 🎨 Diapositiva 5: Pregunta, Datos y Potencial Visual

### Coherencia entre Pregunta y Datos
* **Variables $X$ (Explicativas):** `Member Type` (segmentación del perfil), `Start Station` / `End Station` (origen-destino espacial) y `Bike Number`.
* **Variable $Y$ (Fenómeno de Interés):** `Duration` (duración continua de trayectos) y el conteo agrupado de registros (demanda acumulada y flujos).
* **Dimensión $T$ (Contexto Temporal):** Horas extraídas de `Start Date` / `End Date` (0–23 hrs) y diferenciación entre días hábiles y fines de semana.

### Posibles Limitaciones de los Datos
* **Falta de datos meteorológicos:** El dataset original no incluye variables ambientales como lluvia o temperatura, lo cual impide correlacionar caídas de demanda con el clima.
* **Ausencia de trayecto exacto (GPS):** Se conoce la estación de origen y destino, pero no la ruta geográfica precisa seguida por el ciclista durante el trayecto.
* **Sesgo por duración acotada:** Se excluyen viajes menores a 60 segundos, perdiendo visibilidad sobre re-acoples fallidos por fallas en anclajes de estaciones.

### Primeras Ideas sobre Dimensiones a Visualizar
* **Matriz de Calor / Heatmap (Hora vs. Día de la semana):** Para visibilizar picos de demanda según el tipo de usuario (horas punta vs. fin de semana).
* **Histograma / Boxplot Comparativo:** Distribución de la duración del viaje (`Duration`) según la membresía (`Registered` vs. `Casual`).
* **Matriz Origen-Destino / Gráfico de Flujo:** Top estaciones con mayor volumen de salida y llegada para identificar rutas frecuentes y patrones espaciales.

---

## 📁 Estructura del Repositorio GitHub

```text
proyecto-visualizacion-bicicletas/
│
├── data/
│   ├── raw/              # Archivos de datos originales sin modificar
│   └── processed/        # Datasets transformados, limpios y resumidos
│
├── notebooks/
│   └── 01_exploracion.ipynb   # Exploración inicial, limpieza de datos y EDA preliminar
│
├── src/                  # Funciones auxiliares, scripts de procesamiento y lógica Python
│
├── figures/              # Gráficos generados, exportaciones estáticas y diagramas
│
├── app/                  # Aplicación interactiva final (Streamlit / Plotly Dashboard)
│
├── README.md             # Documentación principal del proyecto (este archivo)
└── .gitignore            # Archivos excluidos del control de versiones
