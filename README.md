# Coffee_Shop_Sales

<img width="1376" height="768" alt="1ba05e466c1e7d9473da190bf5777362-Photoroom" src="https://github.com/user-attachments/assets/8407e628-ec3b-47e5-a9da-c4fb37d24bbe" />

Para este proyecto se selecciono el sector de Registros de transacciones de Maven Roasters, una cafetería ficticia que opera en tres sucursales de Nueva York. El conjunto de datos incluye la fecha de la transacción, la marca de tiempo y la ubicación, junto con detalles a nivel de producto.

## 📁 Estructura del Repositorio

| Archivo / Carpeta | Descripción |
|-------------------|-------------|
| [Coffee_Shop_Sales.ipynb](Coffee_Shop_Sales.ipynb) | Cuaderno principal de Google Colab con el código Python y gráficos |
| [Docs/Documentacion_Tecnica.pdf](Docs/Documentacion_Tecnica.pdf) | Documentación técnica del análisis EDA y metodología |
| [Metricas aplicada/SCRIPTS_Y_METRICAS.md](Metricas%20aplicada/SCRIPTS_Y_METRICAS.md) | Desglose completo de scripts, funciones y código de Python |
| [Images/](Images/) | Imagen de portada y capturas del análisis |

---

## 🐍 Análisis y Scripts en Python

Este proyecto incluye el procesamiento completo de datos usando **Pandas**, **NumPy**, **Matplotlib** y **Seaborn**:

- **Limpieza y Preparación:** Tratamiento de fechas, conversiones a Datetime y creación del campo de Facturación (`sales`).
- **Análisis Temporal y Geográfico:** Evolución de ventas diarias, comparativos semanales por sucursal y detección de horas pico.
- **Rendimiento de Productos:** Evaluación de ticket promedio por categoría y desglose de tipos de productos.

👉 **Más detalles de los scripts:** [Ver Scripts y Métricas Aplicadas](Metricas%20aplicada/SCRIPTS_Y_METRICAS.md)

---

## 🤝 Sistema de Soporte a Decisiones (DSS)

El análisis exploratorio de datos (EDA) y las visualizaciones interactivas desarrolladas en Python funcionan como un **Sistema de Soporte a Decisiones (DSS)**, transformando más de 100,000 registros de transacciones en información estratégica.

Este reporte está diseñado para ser consultado por **Gerentes Operativos, Responsables de Sucursal o Equipos de Comercialización**, permitiéndoles:
1. **Identificar las horas pico de demanda** para optimizar la asignación de personal y turnos de trabajo.
2. **Detectar las sucursales con mayor facturación** y analizar patrones de consumo diarios/semanales.
3. **Optimizar el inventario de productos** priorizando las categorías y tipos de bebidas/alimentos con mayor ticket promedio y volumen de venta.

---

## ✅ Conclusión

El análisis desarrollado permite entender con precisión el comportamiento comercial de las sucursales de la cafetería. La combinación de transformaciones de datos eficientes en Python y visualizaciones claras permite a la dirección tomar decisiones basadas en datos reales para maximizar los ingresos y mejorar la eficiencia operativa.

---

## 📄 Documentación Técnica y Recursos

- 📄 [Ver Documentación Técnica (PDF)](Docs/Documentacion_Tecnica.pdf)
- 🐍 [Ver Scripts y Métricas en Python](Metricas%20aplicada/SCRIPTS_Y_METRICAS.md)
- 📓 [Abrir Notebook de Google Colab](Coffee_Shop_Sales.ipynb)
