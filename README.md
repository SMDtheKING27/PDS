# PDS
LABORATORIO 1 - ESTADISTICA
# Análisis Estadístico de Señales Fisiológicas

Este proyecto realiza un análisis estadístico y de ruido sobre una señal fisiológica (ECG) utilizando Python. A continuación, se detalla cada sección del código con explicaciones detalladas y fórmulas utilizadas.

## Requisitos
- **Python 3.9**
- Bibliotecas necesarias:
  - `wfdb`
  - `numpy`
  - `matplotlib`
  - `seaborn`

Instalar dependencias:
```bash
pip install wfdb numpy matplotlib seaborn
```

## Estructura del Código

### 1. Lectura de Datos
```python
import wfdb
import numpy as np

datos = wfdb.rdrecord('rec_2')
t = 900
señal = datos.p_signal[:t, 0]
```
Se utiliza `wfdb.rdrecord` para cargar la señal desde un archivo externo. En este caso, se toman los primeros 900 puntos de la señal fisiológica (ECG). Esta metodología permite trabajar con señales medidas en entornos reales y procesarlas para obtener información útil.

---

### 2. Histograma de la Señal
```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.histplot(señal, kde=True, bins=30, color='red')
plt.hist(señal, bins=30, edgecolor='blue')
plt.title('Histograma de Datos')
plt.xlabel('Datos')
plt.ylabel('Frecuencia')
plt.show()
```
Se generan dos histogramas:
1. **Con Seaborn (`sns.histplot`)**: Incluye ajuste KDE para visualizar la densidad de probabilidad.
2. **Con Matplotlib (`plt.hist`)**: Representa la frecuencia de valores en intervalos definidos.

---
