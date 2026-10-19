# 📊Proyecto RappiPlus De datos a decisiones de negocio (Bootcamp Tripleten)

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es realizar un diagnóstico del servicio de suscripción de RappiPlus dentro del ecosistema de Rappi para evaluar su rentabilidad real, analizar el comportamiento y retención de los usuarios, y medir el impacto de cambios en el producto mediante experimentación basada en datos.

---

## 🛠️ Tecnologías y Librerías Utilizadas
* **Lenguaje:** Python 3.x / SQL (PostgreSQL)
* **Entorno:** JupyterLab / Jupyter Notebook
* **Visualización y BI:** Power BI / Tableau
* **Librerías principales:**
    * `pandas & numpy` — Carga, limpieza, validación de calidad de datos y modelado financiero (Revenue, COGS, Profit).
    * `matplotlib & seaborn` — Visualizaciones de distribuciones y gráficos analíticos.
    * `scipy.stats — Pruebas` estadísticas (chi2_contingency) para evaluación de experimentos A/B.

---

##📂 Estructura de la Base de Datos
El proyecto integra información de múltiples fuentes relacionales y transaccionales:
1. `rappiplus_orders_raw.csv:` Registro histórico de pedidos, precios, descuentos y montos totales.
2. `rappiplus_catalog.csv:` Catálogo de productos, costos unitarios, categorías y proveedores.
3. `rappiplus_marketing_spend.csv:` Inversión publicitaria desglosada por fecha, país, canal y campaña.
4. `Base de datos relacional (SQL):` Tablas de eventos de navegación de usuarios (events), registros de usuarios (users) y actividad de recurrencia (user_activity).
5. `experiment_checkout_ui.csv:` Datos de participación y conversión de un experimento A/B en el flujo de pago.

---

## 📊 Pasos del Análisis y Hallazgos Clave

### 1. Limpieza y Calidad de Datos
* **Duplicados:** Se identificaron y eliminaron 100 duplicados en la tabla orders.
* **Estandarización:** Tambien en orders, los campos de pais, dispositivo, fuente_referencia, nombre_producto y categoria_producto se rellenaron con la etiqueta desconocido.
* **Nulos:** en marketing_spend los nulos de en la columna canal se imputaron como Desconocidos.
* **Fechas inconsistentes:** las filas sin fecha de pedido como es un porcentaje menor al 0.5 se descartan.

### 2. 

* **Salud Financiera General:** El negocio demuestra ser rentable con un Revenue Total de [9.66] millones USD y un Profit Neto de [2.94] millones USD, lo que representa un Margen de Ganancia del 30.46%.
* **Estructura de Costos:** Del ingreso total, el costo de mercancía/productos (COGS) representa el 39.8% [3.85M] y la inversión en marketing representa el 29.7% [2.87M].
* **El Ticket Promedio (AOV):** por orden se ubica en $385.81 USD con un volumen promedio de 1.50 unidades por pedido.
* **Mayoer vendido:** El producto con mayor volumen de ventas es Vacuum-Pro-Black (6,317 unidades).

### 3. Funnel y Retencion

1. Punto de Mayor Caída (Drop-off): Se identifica un cuello de botella importante en la transición de begin_checkout a add_payment_info y de ahí a purchase, donde la conversión cae de un ~90% en el inicio de pago a un ~77% - 79% en la compra final según el país.
2. Recomendación: Optimizar la experiencia de usuario (UI/UX) en la pantalla de métodos de pago y revisar la transparencia de costos adicionales o tarifas ocultas al momento de finalizar la compra.
3. La retención inicial a los 7 días es alta (~85% - 87%).
4. Muestra una caída gradual hacia los 14 días (~77% - 79%).21 días (~63% - 65%).
5. Hacia el día 28, la retención se estabiliza cerca del 40% - 41%, lo que indica que aproximadamente 4 de cada 10 usuarios nuevos se convierten en clientes recurrentes activos en la plataforma.

### 4. Experimentos y Hallazgos 

1. Evaluación del A/B Test (UI Checkout): La tasa de conversión del grupo Control fue de 15.69% (779 conversiones / 4,965 usuarios).
2. La tasa de conversión del grupo Tratamiento fue de 16.29% (820 conversiones / 5,035 usuarios).
3. Al realizar la prueba chi-cuadrado No se cuenta con evidencia estadística suficiente para afirmar que la nueva interfaz del checkout mejore la conversión. Se sugiere no desplegar la nueva UI de forma masiva sin antes testear variaciones iterativas en la experiencia de pago.

---

## 💡 Se plantearon Recomendaciones Comerciales

1. **Optimización de UI/UX en Checkout:** Revisar la fricción en la pantalla de métodos de pago y asegurar total transparencia en los precios finales desde el inicio para reducir el abandono en la última milla.
2. **Estrategia de Retención:** Aprovechar la base estables de clientes recurrentes al día 28 mediante beneficios de fidelización para mantener el margen operativo del servicio.
3. **Toma de Decisiones Informada:** Frenar el despliegue masivo de la nueva variante de UI evaluada en el experimento hasta rediseñar iterativamente la experiencia de pago con base en los puntos de fricción detectados en el funnel.

## Link para presentacion en PowerBi 
- https://drive.google.com/file/d/1p2KhEIQEgBmr4kv_VnhHTAOT-ueKTSRw/view?usp=drive_link

