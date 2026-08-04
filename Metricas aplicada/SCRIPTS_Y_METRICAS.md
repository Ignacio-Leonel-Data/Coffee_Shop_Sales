# 📊 Scripts y Análisis EDA – Tablero Coffee Shop Sales

Este documento reúne el flujo completo de exploración, limpieza, preparación de datos, cálculo de métricas y visualizaciones desarrollado en **Python (Google Colab)**, organizados según la estructura del proyecto.

---
📁 Configuración y Entorno
🔹 Importación de Librerías
Python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import data_profiling
from data_profiling import ProfileReport
📁 Limpieza y Preparación de Datos
🔹 Carga del Dataset
Python
df = pd.read_excel('/content/Coffee Shop Sales.xlsx')
🔹 Exploración Estructural y Control de Nulos
Python
# Verificación de valores faltantes
missing_values = df.isnull().sum()
print(missing_values)

# Información general del conjunto de datos
df.info()
🔹 Ingeniería de Funciones (Feature Engineering)
Python
# Conversión y formato de tiempo
df['transaction_time'] = df['transaction_time'].astype(str)
df['transaction_time'] = pd.to_timedelta(df['transaction_time'])

# Creación del campo Datetime consolidado
df['datetime'] = df['transaction_date'] + df['transaction_time']

# Cálculo de la facturación total
df['sales'] = df['transaction_qty'] * df['unit_price']

# Extracción de variables temporales
df['day_of_week'] = df['datetime'].dt.day_name()
df['month'] = df['datetime'].dt.to_period('M')
df['hour'] = df['datetime'].dt.hour
📁 Análisis por Sucursal (Store Location)
🔹 Facturación y Transacciones por Ubicación
Python
df_location = df.groupby('store_location').agg({
    'sales': 'sum',
    'transaction_id': 'count'
})
🔹 Evolución de Ventas Diarias por Ubicación
Python
daily_sales_by_location = df.groupby(['transaction_date', 'store_location'])['sales'].sum().unstack()

# Gráfico de líneas
daily_sales_by_location.plot(figsize=(14, 8), title='Daily Sales by Location')
plt.xlabel('Date')
plt.ylabel('Total Sales ($)')
plt.legend(title='Store Location')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Gráfico de área acumulada
plt.figure(figsize=(14, 8))
plt.stackplot(daily_sales_by_location.index, daily_sales_by_location.T, labels=daily_sales_by_location.columns)
plt.title('Daily Sales by Store Location (Stacked Area Chart)')
plt.xlabel('Date')
plt.ylabel('Total Sales ($)')
plt.legend(title='Store Location', loc='upper left')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
📁 Análisis Temporal
🔹 Comparativo Semanal por Ubicación
Python
weekly_sales = df.groupby(['day_of_week', 'store_location'])['sales'].sum().unstack()

# Ordenamiento cronológico de los días
days_order = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
weekly_sales = weekly_sales.reindex(days_order)

# Visualización en barras
weekly_sales[["Astoria", "Hell's Kitchen", "Lower Manhattan"]].plot(kind='bar', figsize=(14, 8))
plt.xlabel('Day of the Week', fontweight='bold')
plt.ylabel('Total Sales ($)', fontweight='bold')
plt.title('Weekly Sales by Store Location')
plt.legend(title='Store Location', loc='upper left')
plt.tight_layout()
plt.show()
🔹 Comportamiento Mensual
Python
monthly_sales = df.groupby('month')['sales'].sum().reset_index()

monthly_sales.plot(figsize=(14, 8), title='Monthly Sales')
plt.xlabel('Month')
plt.ylabel('Total Sales ($)')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
📁 Comportamiento de Producto
🔹 Ticket Promedio y Facturación por Categoría
Python
df_category = df.groupby('product_category').agg({
    'sales': 'sum',
    'transaction_id': 'count'
}).sort_values('sales', ascending=False)

# Cálculo de Venta Promedio por Transacción
df_category['avg_sales'] = df_category['sales'] / df_category['transaction_id']
🔹 Desglose por Tipo de Producto en cada Categoría
Python
product_sales_df = df.groupby(['product_category', 'product_type'])['sales'].sum().reset_index()

categories = product_sales_df['product_category'].unique()

for category in categories:
    plt.figure(figsize=(5, 5))
    category_data = product_sales_df[product_sales_df['product_category'] == category]
    sns.barplot(data=category_data, x='product_type', y='sales')

    plt.title(f'Sales by Product Type in {category}')
    plt.xlabel('Product Type')
    plt.ylabel('Total Sales ($)')
    plt.xticks(rotation=45)
    plt.tight_layout()
    plt.show()
📁 Análisis Horario (Horas Pico)
🔹 Distribución de Ventas por Hora y Ubicación
Python
hourly_sales_by_location = df.groupby(['store_location', 'hour'])['sales'].sum().reset_index()

plt.figure(figsize=(14, 8))
sns.barplot(data=hourly_sales_by_location, x='hour', y='sales', hue='store_location')

plt.title('Hourly Sales by Store Location')
plt.xlabel('Hour of the Day')
plt.ylabel('Total Sales ($)')
plt.legend(title='Store Location', loc='upper right')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
