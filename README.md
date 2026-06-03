# Análisis de Servicio Técnico y Ventas — Proyecto Tecnolab

Este proyecto realiza un análisis completo de datos reales de clientes, tickets de reparación, ventas de accesorios, repuestos y encuestas de satisfacción.  
El objetivo es identificar patrones operativos, comerciales y de rentabilidad para mejorar la toma de decisiones.

---

## 1. Preparación y limpieza de datos

Se aplicaron procesos de limpieza y estandarización:

- Normalización de nombres de columnas  
- Conversión de tipos (fechas, numéricos, IDs)  
- Eliminación de duplicados  
- Corrección de valores faltantes  
- Integración de datasets mediante claves comunes  
- Validación de consistencia entre tablas  

---

## 2. Análisis exploratorio (EDA)

El notebook incluye análisis sobre:

- Fallas más frecuentes  
- Modelos más reparados  
- Tiempo promedio de reparación  
- Margen por reparación  
- Rendimiento por técnico  
- Distribución por canal  
- Análisis por ciudad  
- Participación y satisfacción del sorteo  

---

## 3. Principales insights

### Ciudades
- **Godoy Cruz** concentra el mayor volumen de reparaciones.  
- **Guaymallén** presenta el **margen promedio más alto**, siendo la más rentable.

### Técnicos
- Diferencias claras en productividad y tiempos.  
- Algunos técnicos destacan por eficiencia; otros requieren capacitación.

### Canales
- El canal presencial domina, pero los digitales muestran crecimiento.  
- Variación por ciudad → oportunidad para campañas segmentadas.

### Fallas y modelos
- Las fallas se concentran en pocas categorías.  
- Los modelos más reparados coinciden con los más vendidos.

### Margen
- El margen depende de ciudad, técnico y tipo de falla.  
- Las fallas complejas generan mayor margen pero aumentan el tiempo de reparación.

---

## 4. Dashboard en Power BI

El análisis del sorteo y la satisfacción del cliente se visualiza en Power BI:

- Participación por ciudad  
- Edad promedio  
- Tiempo de espera vs calificación  
- Nuevos clientes vs recurrentes  
- Impacto del sorteo en ventas  

---

## 5. Estructura del repositorio
```

📂 servicio-tecnico-analisis
 ├── 📓 EDA_Tecnolab.ipynb
 ├── 📄 README.md
 ├── 📂 data/
 │    ├── clientes.csv
 │    ├── tickets_reparacion.csv
 │    ├── ventas_accesorios.csv
 │    ├── encuesta_sorteo.csv
 │    └── repuestos.csv

```
---

## 6. Conclusión general

El negocio presenta buen volumen, margen saludable y patrones claros que permiten optimizar operaciones, mejorar la experiencia del cliente y aumentar la rentabilidad.

---

## Autor

Danel — Analista de Datos / BI  
Barcelona, España


## Power BI — Análisis del Servicio Técnico

### 1. Preparación de datos (Power Query)

En Power Query se realizó un proceso completo de limpieza y estandarización para asegurar la calidad del modelo:

- Normalización de nombres de columnas
- Eliminación de duplicados en tickets y clientes
- Conversión de tipos de datos (fechas, números, texto)
- Corrección de valores faltantes y registros inconsistentes
- Unificación de categorías de fallas y técnicos
- Creación de columna “Ganancia” = Ingresos – Costos
- Integración de todas las tablas mediante claves comunes
- Creación de tabla Calendario para análisis temporal
- Ajuste de formatos monetarios y de tiempo


### 2. Modelado de datos

El modelo se estructuró siguiendo un enfoque tipo estrella:

- Tabla **Tickets** como tabla de hechos
- Tablas **Clientes**, **Repuestos**, **Accesorios**, **Encuesta**, **Técnicos** como dimensiones
- Tabla **Calendario** generada para análisis temporal
- Relaciones 1:N entre dimensiones y hechos
- Uso de claves limpias y consistentes para evitar ambigüedades
- Modelo optimizado para cálculos de ingresos, costos y tiempos


### 3. Medidas DAX creadas

Se desarrollaron medidas clave para el análisis financiero y operativo:

- **Ingresos Totales**  
  `Ingresos Totales = SUM(Tickets[precio])`

- **Costo Total**  
  `Costo Total = SUM(Tickets[costo])`

- **Ganancia Total**  
  `Ganancia Total = [Ingresos Totales] - [Costo Total]`

- **Ticket Promedio**  
  `Ticket Promedio = AVERAGE(Tickets[precio])`

- **Ganancia Promedio por Ticket**  
  `Ganancia Promedio por Ticket = AVERAGE(Tickets[ganancia])`

- **Tickets por Empleado**  
  `Tickets por Empleado = COUNT(Tickets[id_ticket])`

- **Variación Ingresos %**  
  `Variación Ingresos % = DIVIDE([Ingresos Totales] - CALCULATE([Ingresos Totales], DATEADD(Calendario[Fecha], -1, MONTH)), CALCULATE([Ingresos Totales], DATEADD(Calendario[Fecha], -1, MONTH)))`


### 4. Visualizaciones del dashboard

El informe incluye visualizaciones diseñadas para entender el rendimiento del servicio técnico:

- KPIs principales (Ingresos, Ganancia, Ticket promedio, Variación %)
- Ingresos totales por mes
- Ingresos totales por técnico
- Ganancia total por tipo de falla
- Tabla comparativa por técnico (ingresos, costos, tickets, promedios)
- Segmentadores por técnico y tipo de falla
- Botones de **Reset** y **Borrar filtros**


### 5. Hojas del informe

El dashboard está dividido en tres páginas:

#### **Datos**
- Vista general del negocio
- Ingresos, ganancia, ticket promedio
- Distribución por técnico y por falla

#### **Desempeño**
- Productividad por técnico
- Tiempo promedio de reparación
- Tickets por mes
- Fallas más frecuentes por empleado

#### **Finanza**
- Análisis financiero completo
- Margen por falla
- Ingresos por mes
- Comparativa de técnicos
- Tabla financiera consolidada


### 6. Capturas del dashboard

Las capturas del informe se encuentran en:

/powerbi/capturas/

Incluyen:

- Hoja **Datos**
- Hoja **Desempeño**
- Hoja **Finanza**


### 7. Conclusiones del análisis en Power BI

- El negocio presenta ingresos estables y margen saludable.
- Los técnicos muestran diferencias claras en productividad y rentabilidad.
- Las fallas complejas generan mayor ganancia, pero requieren más tiempo.
- Los meses iniciales del año muestran una ligera caída en ingresos.
- El análisis permite identificar oportunidades de capacitación, optimización de tiempos y mejora de la rentabilidad por tipo de falla.


