# 📊 Análisis Exploratorio de Datos — Superstore Sales

Limpieza, transformación, análisis descriptivo y dashboard de ventas de una cadena de retail (2015-2018), construido **íntegramente en Microsoft Excel** con fórmulas nativas (sin macros, sin Power Query, sin programas externos).

> Proyecto final del Bootcamp de Data & Analytics — Módulo *Dashboard & Análisis de Datos*.

---

## 📝 Descripción del proyecto

El objetivo es realizar un análisis exploratorio completo (EDA) de un conjunto de datos libre, cubriendo las cuatro fases exigidas por el enunciado:

1. **Transformación y limpieza de los datos**
2. **Análisis descriptivo**
3. **Dashboard**
4. **Informe explicativo**

Todo el proceso se ha resuelto usando **exclusivamente Excel**: las hojas de limpieza y de resumen no contienen valores pegados, sino fórmulas vivas (`TRIM`, `PROPER`, `DATE`, `IF`, `SUMIFS`, `AVERAGEIFS`, `COUNTIFS`...) que recalculan automáticamente si cambian los datos de origen. Esto permite auditar cada número del dashboard hasta su fórmula y, en última instancia, hasta la fila original del CSV.

**Dataset:** [Superstore Dataset (Kaggle)](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) — pedidos de una cadena de retail estadounidense ficticia, 2015-2018. Es uno de los datasets de referencia más usados en formación de análisis de datos (Tableau / Kaggle).

- **Origen del archivo:** la descarga directa desde Kaggle requiere una cuenta autenticada (API key), por lo que el CSV se obtuvo a través de un espejo público en GitHub que replica el mismo contenido de pedidos: [`leonism/sample-superstore`](https://github.com/leonism/sample-superstore) (`data/superstore.csv`).
- **Tamaño original:** 10.800 filas × 21 columnas (supera ampliamente el mínimo exigido de 2.000 filas y 10 columnas).
- **Tamaño tras la limpieza:** 9.993 filas × 32 columnas (17 columnas originales + 15 columnas de auditoría/transformación).

---

## 🗂️ Estructura del proyecto

```
├── README.md                                   <- este archivo
├── Master_Analisis_Exploratorio_Superstore.xlsx <- archivo Excel único con todo el proceso
└── superstore_original_raw.csv                 <- datos originales, sin ninguna modificación
```

### Hojas del archivo Excel

| Hoja | Contenido |
|---|---|
| `00_Guia` | Resumen de los pasos seguidos en el proyecto |
| `01_Datos_Originales` | Los 10.800 registros del CSV descargado, **sin tocar** |
| `02_Diagnostico_Calidad` | Fórmulas de auditoría (`COUNTBLANK`, `COUNTIF`, `COUNTA`) que cuantifican los problemas del archivo original antes de limpiar nada |
| `03_Datos_Limpios` | 9.993 filas limpias; cada campo es una fórmula que referencia `01_Datos_Originales` (texto normalizado, fechas reales, código postal corregido) + 11 columnas nuevas calculadas (margen, días de envío, año, mes, trimestre, estado de beneficio, banda de descuento...) |
| `04_Resumen_Mensual` … `10_Resumen_Envio` | Tablas resumen con `SUMIFS` / `AVERAGEIFS` / `COUNTIFS` por mes, región, categoría, subcategoría, segmento, descuento y modo de envío |
| `Dashboard` | 8 KPIs y 4 gráficos (líneas, barras, circular, barras horizontales), todos vinculados a fórmulas |
| `11_Informe` | Informe explicativo: objetivo, dataset, metodología, resultados, limitaciones y trazabilidad |

---

## ⚙️ Instalación y requisitos

No se necesita instalar nada especial: basta con **Microsoft Excel 2016 o superior** (o Google Sheets, aunque algunas funciones de texto pueden requerir pequeños ajustes de sintaxis al importar).

Para abrir el proyecto:

1. Descargar o clonar este repositorio.
2. Abrir `Master_Analisis_Exploratorio_Superstore.xlsx`.
3. Si Excel muestra un aviso de cálculo, pulsar **F9** (o Fórmulas → Calcular ahora) para forzar el recálculo — el archivo ya se entrega con los valores calculados, pero es buena práctica verificarlo.
4. Empezar por la hoja `00_Guia` para seguir el orden del análisis.

---

## 📈 Resultados y conclusiones

*(ver detalle completo en la hoja `Dashboard` y `11_Informe` del Excel)*

- **Ventas netas:** 2.296.919 € · **Beneficio:** 286.409 € · **Margen medio:** 12,5 %
- **Unidades vendidas:** 37.871 · **Ticket medio por línea de pedido:** 229,85 € · **Nº de pedidos únicos:** 5.009
- **Plazo de envío medio:** 4,0 días · **% de líneas con pérdida:** 18,7 %
- La región **West** genera más beneficio; **Technology** es la categoría más rentable.
- A nivel de subcategoría aparece el hallazgo más relevante del dataset: **Tables** (-17.725 €), **Bookcases** (-3.473 €) y **Supplies** (-1.189 €) generan pérdidas netas pese a tener ventas, normalmente asociado a descuentos elevados — una alerta clara para revisar la política de descuentos en esas líneas de producto.

**Valor práctico:** el dashboard permite detectar en segundos qué categorías, regiones o modos de envío erosionan el margen, y sirve de base para decisiones sobre política de descuentos y logística.

---

## 🔭 Próximos pasos

- Incorporar un análisis de cohortes o recurrencia de clientes (no incluido por no formar parte del alcance del ejercicio).
- Cruzar la banda de descuento con la subcategoría para cuantificar el efecto exacto del descuento sobre el beneficio de `Tables`.
- Migrar los resúmenes SUMIFS/COUNTIFS a Tablas Dinámicas nativas si el archivo se sigue manteniendo a largo plazo.

---

## 🤝 Contribuciones

Este es un proyecto académico individual y no está abierto a contribuciones externas. Cualquier comentario o sugerencia puede indicarse abriendo un *issue* en el repositorio.

---

## 👤 Autoría y agradecimientos

- **Autora:** María — Bootcamp Data & Analytics.
- **Dataset:** Superstore Dataset, publicado en [Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final).

