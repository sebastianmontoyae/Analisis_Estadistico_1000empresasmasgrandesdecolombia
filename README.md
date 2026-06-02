# 📊 Análisis Estadístico — 1.000 Empresas más grandes de Colombia
### Statistical Analysis — 1,000 Largest Companies in Colombia

> **Fuente de datos / Data Source:** Superintendencia de Sociedades (Supersociedades) · Período / Period: 2017–2018  
> **Autor / Author:** Sebastian Montoya Echeverry — BI Analyst & Data Science Consultant  
> **Herramientas / Tools:** Python · SciPy · Pandas · Plotly · R

---


### Descripción del proyecto

Análisis estadístico exploratorio y descriptivo sobre las **1.000 empresas más grandes de Colombia**, con datos oficiales de la Superintendencia de Sociedades para el período 2017–2018. El objetivo fue determinar cuáles son los sectores económicos más sólidos del país, identificar si hubo crecimiento empresarial real entre ambos años y establecer si existen diferencias estructurales significativas entre los 6 macrosectores evaluados.

### Objetivo

Responder tres preguntas de negocio con evidencia estadística:

1. ¿Las empresas más grandes de Colombia crecieron entre 2017 y 2018?
2. ¿Existen diferencias significativas entre los sectores económicos?
3. ¿Qué sectores son estructuralmente distintos entre sí y en qué variables financieras?

### Sectores evaluados

| Macrosector | Empresas |
|---|---|
| Minero-Hidrocarburos
| Manufactura
| Comercio
| Servicios
| Construcción 
| Agropecuario 

### Variables financieras analizadas

- Activos totales (2017 – 2018)
- Pasivos totales (2017 – 2018)
- Patrimonio neto (2017 – 2018)
- Ingresos operacionales (2017 – 2018)
- Ganancia / Pérdida del período

### Metodología — Pasos del análisis

```
Paso 1 → Carga y estandarización de columnas
Paso 2 → Auditoría de calidad de datos
Paso 3 → Estadística descriptiva
Paso 4 → Pruebas de normalidad (Shapiro-Wilk + Kolmogorov-Smirnov + Sesgo/Curtosis)
Paso 5 → Detección de outliers (IQR) + Transformación logarítmica
Paso 6 → Correlación de Spearman + Covarianza
Paso 7 → Pruebas de hipótesis (Wilcoxon + Kruskal-Wallis)
Paso 8 → Análisis Post-Hoc Mann-Whitney + Corrección de Bonferroni
Paso 9 → Conclusiones y hallazgos ejecutivos
```

### Decisiones metodológicas clave

- Se usó **Spearman** en lugar de Pearson porque ninguna variable financiera siguió distribución normal.
- Se usó **Wilcoxon** en lugar de t-test para comparar los dos períodos por ser muestras relacionadas no normales.
- Se usó **Kruskal-Wallis** como alternativa no paramétrica al ANOVA para comparar los 6 sectores.
- Se aplicó **corrección de Bonferroni** (α = 0.00333) en el análisis Post-Hoc para controlar el error tipo I al comparar 15 pares de sectores.
- Los outliers (Ecopetrol, EPM, Grupo Sura) se conservaron por representar realidad económica y no errores de datos.

### Hallazgos principales

- ✅ Las 1.000 empresas más grandes de Colombia **sí crecieron** entre 2017 y 2018 en activos, patrimonio e ingresos (Wilcoxon, p < 0.05).
- ✅ Los 6 sectores económicos son **estructuralmente diferentes** entre sí (Kruskal-Wallis, p < 0.001).
- ✅ **Minero-Hidrocarburos** concentra la mayor riqueza en activos y patrimonio.
- ✅ **Manufactura** es el sector más capitalizado en patrimonio neto propio.
- ✅ En **ingresos operacionales** las diferencias entre sectores son mínimas — la desigualdad está en el balance, no en el estado de resultados.
- ⚠️ 48 empresas con patrimonio negativo y 193 con pérdidas operativas — realidad del tejido empresarial colombiano, no errores del dataset.

### Estructura del repositorio

```
analisis-estadistico-empresas-colombia/
│
├── README.md
├── data/
│   └── 1000_Empresas_mas_grandes_del_pais.csv
├── notebooks/
│   └── AnalisisEstadistico_1000_empresas.ipynb
├── scripts/
│   └── script_1000_empresas.R
└── outputs/
    └── (visualizaciones exportadas)
```

### Requisitos para ejecutar el notebook

```bash
pip install pandas scipy numpy plotly matplotlib seaborn
```

### Cómo ejecutar

```bash
git clone https://github.com/tu-usuario/analisis-estadistico-empresas-colombia.git
cd analisis-estadistico-empresas-colombia
jupyter notebook notebooks/AnalisisEstadistico_1000_empresas.ipynb
```

---

## 🇺🇸 English

### Project Description

Exploratory and descriptive statistical analysis of the **1,000 largest companies in Colombia**, using official data from the Superintendencia de Sociedades (Colombia's corporate regulatory body) for the 2017–2018 period. The goal was to determine which economic sectors show the strongest financial structure, whether real business growth occurred between both years, and whether significant structural differences exist across the 6 evaluated macrosectors.

### Objective

Answer three business questions with statistical evidence:

1. Did Colombia's largest companies grow between 2017 and 2018?
2. Are there significant differences across economic sectors?
3. Which sectors are structurally distinct from each other, and across which financial variables?

### Sectors Evaluated

| Macrosector | Included |
|---|---|
| Mining & Hydrocarbons
| Manufacturing
| Commerce
| Services
| Construction
| Agriculture

### Financial Variables Analyzed

- Total assets (2017 – 2018)
- Total liabilities (2017 – 2018)
- Net equity / Patrimony (2017 – 2018)
- Operating revenues (2017 – 2018)
- Net profit / Loss for the period

### Methodology — Analysis Steps

```
Step 1 → Data loading and column standardization
Step 2 → Data quality audit
Step 3 → Descriptive statistics
Step 4 → Normality tests (Shapiro-Wilk + Kolmogorov-Smirnov + Skewness/Kurtosis)
Step 5 → Outlier detection (IQR) + Logarithmic transformation
Step 6 → Spearman correlation + Covariance
Step 7 → Hypothesis testing (Wilcoxon + Kruskal-Wallis)
Step 8 → Post-Hoc Mann-Whitney analysis + Bonferroni correction
Step 9 → Conclusions and executive findings
```

### Key Methodological Decisions

- **Spearman** correlation was used instead of Pearson because no financial variable followed a normal distribution.
- **Wilcoxon signed-rank test** was used instead of a paired t-test to compare the two periods, given non-normal related samples.
- **Kruskal-Wallis** was used as a non-parametric alternative to ANOVA to compare the 6 sectors.
- **Bonferroni correction** (α = 0.00333) was applied in the Post-Hoc analysis to control Type I error when comparing 15 sector pairs.
- Outliers (Ecopetrol, EPM, Grupo Sura) were retained as they represent real economic entities, not data errors.

### Key Findings

- ✅ Colombia's 1,000 largest companies **did grow** between 2017 and 2018 in assets, equity, and revenues (Wilcoxon, p < 0.05).
- ✅ The 6 economic sectors are **structurally different** from one another (Kruskal-Wallis, p < 0.001).
- ✅ **Mining & Hydrocarbons** holds the highest wealth concentration in assets and equity.
- ✅ **Manufacturing** is the most capitalized sector by net equity.
- ✅ In **operating revenues**, sector differences are minimal — inequality lies in the balance sheet, not the income statement.
- ⚠️ 48 companies with negative equity and 193 with operating losses — reflecting real conditions in Colombia's corporate landscape, not dataset errors.

### Repository Structure

```
analisis-estadistico-empresas-colombia/
│
├── README.md
├── data/
│   └── 1000_Empresas_mas_grandes_del_pais.csv
├── notebooks/
│   └── AnalisisEstadistico_1000_empresas.ipynb
├── scripts/
│   └── script_1000_empresas.R
└── outputs/
    └── (exported visualizations)
```

### Requirements

```bash
pip install pandas scipy numpy plotly matplotlib seaborn
```

### How to Run

```bash
git clone https://github.com/tu-usuario/analisis-estadistico-empresas-colombia.git
cd analisis-estadistico-empresas-colombia
jupyter notebook notebooks/AnalisisEstadistico_1000_empresas.ipynb
```

---

## 📌 Topics / Etiquetas sugeridas para GitHub

`python` `r` `statistics` `data-analysis` `exploratory-data-analysis` `scipy` `pandas` `plotly` `colombia` `supersociedades` `nonparametric-statistics` `kruskal-wallis` `mann-whitney` `bonferroni` `business-intelligence`
