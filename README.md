# Clasificación de tumores de mama: regresión logística, Naive Bayes, SVM y MLP

Proyecto final de Ciencia de Datos. Se comparan tres modelos (Naive Bayes
gaussiano, SVM y perceptrón multicapa) contra una regresión logística de
referencia sobre el dataset Breast Cancer Wisconsin (Diagnostic) de UCI.

*Autor:* Rivera Briones Cristian Jesus

## Datos
- Fuente: UCI Machine Learning Repository, Breast Cancer Wisconsin (Diagnostic).
- Archivos incluidos en data/: wdbc.data y wdbc.names.
- 569 muestras, 30 variables numéricas, clases: benigno (357) y maligno (212).

## Estructura

data/                datos originales
notebooks/
  01_eda.ipynb       análisis exploratorio
  02_modelos.ipynb   división, modelos, evaluación y análisis de errores
reports/figures/     figuras usadas en el reporte
requirements.txt     dependencias con versiones fijas


## Cómo ejecutarlo (Windows, PowerShell)
Versión de Python usada: 3.13.12.

powershell
git clone https://github.com/riveric980-glitch/proyecto-final-cancer.git
cd proyecto-final-cancer
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt


Abrir los notebooks con el kernel .venv y ejecutar todas las celdas en
orden: primero 01_eda.ipynb y después 02_modelos.ipynb.
La celda de variabilidad con 5 semillas tarda unos 6 minutos.

Instalación probada en dos equipos con Windows: Python 3.13.12 y Python 3.15.
El reporte en formato IEEE se encuentra en reports/reporte_final.pdf

## Observacion
Se ejecuto desde otra pc con la version de python 3.15.2 y se observo una leve cambio en los rsultados, a causa de la version de python y de las librerias que de adaptan a dicha version.


## Reproducibilidad
- Semilla principal: 42 (división 60/20/20 estratificada, validación
  cruzada de 5 folds y modelos).
- Variabilidad: semillas 0, 1, 2, 3 y 4.
- Todo el preprocesamiento (escalado) está dentro de un Pipeline y se
  ajusta solo con los datos de entrenamiento.
- El conjunto de prueba se usa una sola vez para la evaluación final.

## Resultados (conjunto de prueba, semilla 42)
| Modelo | Exactitud | Recall | F1 | AUC |
|---|---|---|---|---|
| Regresión logística (ref.) | 0.9825 | 0.9524 | 0.9756 | 0.9977 |
| Naive Bayes | 0.9211 | 0.8571 | 0.8889 | 0.9897 |
| SVM (RBF) | 0.9825 | 0.9524 | 0.9756 | 0.9957 |
| MLP | 0.9561 | 0.9048 | 0.9383 | 0.9954 |

Con 5 semillas, la regresión logística y el SVM no difieren de forma
significativa; Naive Bayes es consistentemente el más bajo.

## Referencias
- W. H. Wolberg, W. N. Street y O. L. Mangasarian, Breast Cancer Wisconsin
  (Diagnostic), UCI Machine Learning Repository.
- F. Pedregosa et al., "Scikit-learn: Machine Learning in Python", JMLR, 2011.