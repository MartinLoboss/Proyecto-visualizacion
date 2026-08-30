# BikeFlow: Análisis de Dinámicas de Movilidad Urbana y Demanda de Transporte Sustentable

## 1. Integrantes
* **Martín Lobos**
* **Iván Papic**

---

## 2. Descripción del Problema
En las ciudades modernas, el uso de sistemas de bicicletas públicas compartidas ha crecido aceleradamente como una alternativa limpia, eficiente y saludable frente al transporte tradicional. Sin embargo, los operadores enfrentan desafíos constantes debido a la variabilidad de la demanda: existen estaciones que sufren desabastecimiento en horas pico mientras otras quedan sobrepobladas.

Este fenómeno depende fuertemente de variables como las condiciones meteorológicas (temperatura, lluvia, humedad), el horario y la distinción entre días laborables y fines de semana.

---

## 3. Motivación
Estudiar los patrones de uso de las bicicletas públicas permite comprender cómo se desplazan los ciudadanos y cómo factores externos alteran sus patrones de movilidad. Los hallazgos derivados de este análisis facilitan:
* La toma de decisiones en la planificación urbana y redistribución logística.
* La optimización del servicio para los usuarios finales.
* La promoción de estrategias sustentables alineadas con el concepto de *Smart Cities*.

---

## 4. Pregunta del Proyecto y Estructura X, Y, T

### Pregunta Principal
¿Cómo influyen las condiciones meteorológicas, el momento del día y el tipo de jornada (**$X$**) en el volumen de demanda de bicicletas públicas (**$Y$**) a lo largo de las distintas franjas horarias y días de la semana (**$T$**)?

### Componentes de la Pregunta:
* **$X$ (Variables Explicativas / Disponibles)**: 
  * Condiciones meteorológicas (temperatura, sensación térmica, humedad, velocidad del viento, clima general).
  * Tipo de jornada (día laboral, fin de semana, festivo).
  * Estación de origen y destino.
  * Tipo de usuario (casual o registrado).
* **$Y$ (Objetivo / Fenómeno de Interés)**: 
  * Demanda total de viajes en bicicleta (volumen de uso).
* **$T$ (Contexto Temporal)**: 
  * Distribución horaria durante el día y evolución mensual/anual de los datos recopilados.

---

## 5. Alcance e Identificación de Límites

### Dentro del Alcance
* Análisis de patrones de uso según horarios pico y tipo de día (hábiles vs. fines de semana).
* Evaluación del impacto del clima y la temperatura en el volumen de trayectos.
* Identificación de diferencias de comportamiento entre usuarios casuales y miembros registrados.
* Visualización espacial de las estaciones con mayor concentración de inicio de viajes.

### Fuera del Alcance
* Modelos predictivos de mantenimiento técnico o desgaste de la flota.
* Optimización de rutas de camiones para el rebalanceo de bicicletas en tiempo real.
* Análisis financiero de costos, tarifas o renting de las bicicletas.

---

## 6. Fuente y Descripción del Dataset

* **Fuente**: Dataset oficial de *Capital Bikeshare* (Washington D.C., EE. UU.) / [Kaggle Bikeshare Dataset](https://www.capitalbikeshare.com/system-data).
* **Unidad de Observación**: Cada fila representa un **viaje individual** registrado por el sistema.
* **Cobertura Temporal/Espacial**: Registros históricos de viajes en la red urbana de Capital Bikeshare.
* **Principales Variables**:
  * `started_at` / `ended_at`: Timestamp de inicio y término del trayecto.
  * `start_station_name` / `end_station_name`: Nombre e identificador de las estaciones.
  * `member_casual`: Categoría del usuario (`member` o `casual`).
  * `rideable_type`: Tipo de bicicleta (clásica o eléctrica).

> **Nota sobre los datos**: Debido a restricciones de tamaño de GitHub, el archivo de datos sin procesar (`202607-capitalbikeshare-tripdata.csv`) no está almacenado directamente en este repositorio. Los datos deben ser descargados de la fuente oficial y ubicarse dentro de la carpeta `data/raw/`.

---

## 7. Estructura del Repositorio

```text
Proyecto-Visualizacion/
├── app/                  # Aplicación interactiva (Streamlit / Dash)
├── data/
│   ├── raw/              # Datos originales sin modificar (no rastreados por Git)
│   └── processed/        # Datos procesados y limpios para análisis
├── figures/              # Gráficos, diagramas y exportaciones visuales
├── notebooks/            # Notebooks Jupyter para EDA y pruebas
│   └── 01_exploracion.ipynb
├── src/                  # Scripts en Python y funciones reutilizables
├── .gitignore            # Exclusión de archivos pesados (*.csv) y temporales
└── README.md             # Documentación general del proyecto
