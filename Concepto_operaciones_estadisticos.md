# Concepto de Operaciones Estadísticas

Este documento explica de forma práctica los conceptos y medidas estadísticas que arroja un resumen de datos a partir de los resultados obtenidos:

| Métrica | Valor Numérico | Significado Breve |
| :--- | :--- | :--- |
| **count** | 4.000000 | Número total de observaciones registradas |
| **mean** | 22.750000 | Promedio aritmético general |
| **std** | 1.707825 | Desviación estándar (dispersión respecto a la media) |
| **min** | 21.000000 | Valor más bajo del conjunto |
| **25% (Q1)** | 21.750000 | Primer cuartil (corte del 25% inferior) |
| **50% (Q2)** | 22.500000 | Segundo cuartil o Mediana (centro exacto) |
| **75% (Q3)** | 23.500000 | Tercer cuartil (corte del 75% inferior) |
| **max** | 25.000000 | Valor más alto del conjunto |

---

## 1. Conteo de observaciones (`count = 4.000000`)

### Contexto
Representa el tamaño de la muestra ($N$), es decir, la cantidad total de datos recopilados y válidos. En nuestro conjunto ordenado `[21, 22, 23, 25]`, nos confirma que tenemos exactamente 4 registros con los cuales trabajar.

### Código en Python
```python
import numpy as np

# Datos del ejercicio
datos = [21, 22, 23, 25]
count = float(np.size(datos))

print("count", count)
# Devuelve: count 4.0
```

---

## 2. Media aritmética (`mean = 22.750000`)

### Contexto
Es la medida de tendencia central más común. Suma todos los valores de la lista y los divide equitativamente entre el total de elementos. En nuestro caso, la suma total es 91, dando un promedio de **22.75**.

### Código en Python
```python
import numpy as np

# Datos ordenados del ejercicio
datos = [21, 22, 23, 25]
mean = np.mean(datos)

print("mean", mean)
# Devuelve: mean 22.75
```

---

## 3. Desviación estándar (`std = 1.707825`)

### Contexto
Mide qué tan dispersos o separados están los datos respecto al promedio ($22.75$). Al utilizar `ddof=1` indicamos que se trata de una muestra ($N - 1 = 3$), coincidiendo con el método `.describe()`. Un valor de **1.71** refleja que los datos son homogéneos y están muy agrupados.

### Código en Python
```python
import numpy as np

# Datos ordenados del ejercicio
datos = [21, 22, 23, 25]
std = np.std(datos, ddof=1)

print("std", std)
# Devuelve: std 1.707825127659933
```

---

## 4. Valor mínimo (`min = 21.000000`)

### Contexto
Indica el piso o límite inferior de la distribución. Al estar la lista ordenada de menor a mayor, corresponde al primer elemento de la serie (**21.0**).

### Código en Python
```python
import numpy as np

# Datos ordenados
datos = [21, 22, 23, 25]
min_val = float(np.min(datos))

print("min", min_val)
# Devuelve: min 21.0
```

---

## 5. Primer cuartil (`25% = 21.750000`)

### Contexto
Marca la frontera del 25% de los datos con valores más bajos. El 25% de las observaciones es menor o igual a **21.75**, dejando al 75% restante por encima de este umbral.

### Código en Python
```python
import pandas as pd

serie = pd.Series([21, 22, 23, 25])
q1 = serie.quantile(0.25)

print("25%", q1)
# Devuelve: 25% 21.75
```

---

## 6. Segundo cuartil / Mediana (`50% = 22.500000`)

### Contexto
Es el centro exacto de la serie de datos. Divide a la muestra en dos mitades iguales: el 50% de las observaciones es menor o igual a **22.5** y el otro 50% es mayor. Al ser casi idéntica a la media ($22.75$), demuestra que los datos están equilibrados.

### Código en Python
```python
import pandas as pd

# Serie de datos
serie = pd.Series([21, 22, 23, 25])

q2 = serie.quantile(0.50)
print("50%", q2)
# Devuelve: 50% 22.5
```

---

## 7. Tercer cuartil (`75% = 23.500000`)

### Contexto
Representa el corte donde se acumula el 75% de los datos. Indica que las tres cuartas partes de la muestra tienen un valor de **23.5** o menor, separando únicamente al 25% más alto.

### Código en Python
```python
import numpy as np

# Datos ordenados
datos = [21, 22, 23, 25]
q3 = np.percentile(datos, 75)

print("75%", q3)
# Devuelve: 75% 23.5
```

---

## 8. Valor máximo (`max = 25.000000`)

### Contexto
Representa el techo o límite superior registrado. Al estar la lista ordenada, corresponde al último elemento de la serie (**25.0**).

### Código en Python
```python
import pandas as pd

# Serie de datos
serie = pd.Series([21, 22, 23, 25])
max_val = serie.max()

print("max", float(max_val))
# Devuelve: max 25.0
```