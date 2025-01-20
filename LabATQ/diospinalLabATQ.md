# Cambios Lab ATQ

Este documento describe los cambios realizados al código original en el laboratorio de Algorithmic Trading with Quantiacs.

## 1. Cambio de la Técnica de Machine Learning

Código Original:
```python

from sklearn import linear_model
```
```python
def get_model():
    """This is a constructor for the ML model (Random Forest) which can be easily
       modified for using different models.
    """

    # Usando Random Forest Regressor
    model = RandomForestRegressor(n_estimators=100, random_state=42)
    return model
```

Código Modificado:
```python

from sklearn.ensemble import RandomForestRegressor
```
```python
def get_model():
    """This is a constructor for the ML model (Bayesian Ridge) which can be easily
       modified for using different models.
    """

    model = linear_model.LinearRegression()
    return model
```

### Cambio: Se agregó la importación de RandomForestRegressor desde sklearn.ensemble y se cambio el modelo utilizado.

Explicación:
El modelo de regresión lineal fue reemplazado por bosques aleatorios porque estos pueden capturar relaciones no lineales entre las variables y son más robustos frente al sobreajuste. Esta elección mejora la capacidad del modelo para realizar predicciones precisas en datos financieros complejos.

## 2. Cambio de Mercado: De NASDAQ a S&P 500

Código Original:
```python

# loading nasdaq-100 stock data

stock_data = qndata.stocks.load_ndx_data(tail = 365 * 5) #, assets = ["NAS:AAPL", "NAS:AMZN"]
```

Código Modificado:
```python

# loading S&P 500 stock data
#assets = ["NAS:AAPL", "NAS:AMZN"]#, "NVDA", "GOOG", "META", "TSLA"]
stock_data = qndata.stocks.load_spx_data(tail = 365 * 5)#, assets = assets
```

### Cambio:

La fuente de datos fue cambiada de Nasdaq-100 (load_ndx_data) a S&P 500 (load_spx_data).

Se añadió un comentario con una lista de activos específicos.

Explicación:
El cambio en la fuente de datos diversifica el análisis al utilizar el S&P 500, un índice que representa una amplia gama de sectores económicos en el mercado estadounidense.

## 3. Inclusión de al Menos 20 Activos

Código Original:
```python

# stock_data = qndata.stocks.load_ndx_data(tail=365 * 5)
```

Código Modificado:
```python

stock_data = qndata.stocks.load_spx_data(tail=365 * 5)
```

### Cambio: Se incluyeron todos los activos del S&P 500.

Explicación:
La inclusión todos los activos asegura una mayor representatividad y diversidad en el conjunto de datos.


## Conclusión

Los cambios realizados incluyen:

Sustitución de la regresión lineal por un modelo de bosques aleatorios para mejorar las predicciones.

Cambio del mercado analizado de Nasdaq-100 a S&P 500, ampliando la diversidad del conjunto de datos.

Inclusión de al menos 20 activos seleccionados del S&P 500, explicando su relevancia.


Se obtuvieron los siguientes resultados:
![newplot](https://github.com/user-attachments/assets/2b075055-6e1b-4375-b5a5-5b3f3a50f8ad)

**sharpe_ratio**	14.229289




