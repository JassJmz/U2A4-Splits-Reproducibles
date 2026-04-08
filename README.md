# U2A4 — Splits Reproducibles de un Dataset Abierto

## Descripción

Este proyecto aplica una partición train/test reproducible sobre el dataset Iris,
utilizando una semilla fija para garantizar resultados consistentes entre ejecuciones.
Forma parte de una actividad práctica sobre preparación de datos para modelos de
inteligencia artificial.

---

## Estructura del proyecto

U2A4/
├── iris.csv                  # Dataset original completo
├── splits/
│   ├── iris_train.csv        # Conjunto de entrenamiento (80% — 120 muestras)
│   └── iris_test.csv         # Conjunto de prueba (20% — 30 muestras)
├── splits.ipynb              # Código del proceso de partición
└── README.md                 # Este archivo

---

## Dataset — Créditos y Fuente Original

**Nombre:** Iris Dataset (Fisher's Iris Dataset)  
**Autor original:** Ronald A. Fisher  
**Publicación original:** Fisher, R.A. (1936). *The use of multiple measurements in taxonomic problems.* Annals of Eugenics, 7(2), 179–188.  
**Donado al UCI por:** Michael Marshall (1988)  
**Fuente:** UCI Machine Learning Repository  
**URL:** https://archive.ics.uci.edu/dataset/53/iris  
**Licencia:** Dominio público — libre uso para fines académicos y de investigación  

### Descripción del dataset

| Atributo | Tipo | Descripción |
|---|---|---|
| `sepal_length` | Numérico continuo | Longitud del sépalo (cm) |
| `sepal_width` | Numérico continuo | Ancho del sépalo (cm) |
| `petal_length` | Numérico continuo | Longitud del pétalo (cm) |
| `petal_width` | Numérico continuo | Ancho del pétalo (cm) |
| `species` | Categórico | Especie: Iris-setosa, Iris-versicolor, Iris-virginica |

- **Total de instancias:** 150  
- **Clases:** 3 (50 instancias por clase — dataset balanceado)  
- **Valores faltantes:** Ninguno  

---

## Parámetros de la partición

| Parámetro | Valor |
|---|---|
| Proporción train/test | 80% / 20% |
| Semilla (`random_state`) | 42 |
| Criterio | Estratificado (`stratify=y`) |
| Librería utilizada | `scikit-learn` — `train_test_split` |

---

## Requisitos

```bash
pip install pandas scikit-learn
```

---

## Uso

```python
import pandas as pd
from sklearn.model_selection import train_test_split

df = pd.read_csv('iris.csv', header=None,
     names=['sepal_length','sepal_width','petal_length','petal_width','species'])

X = df.drop('species', axis=1)
y = df['species']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)
```

---

## Autor

**Jassiel** — Instituto Tecnológico Superior de la Región de los Llanos (ITSRLL)  
Materia: Ciberfisica — 8vo Semestre  
Actividad: U2A4 — Práctica de Splits Reproducibles
