# PDS
kjj
LABORATORIO 1 - ESTADISTICA
# Análisis Estadístico de Señales Fisiológicas

Este proyecto realiza un análisis estadístico y de ruido sobre una señal fisiológica (ECG) utilizando Python. A continuación, se detalla cada sección del código.

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
Se utiliza `wfdb.rdrecord` para cargar la señal desde un archivo externo. En este caso, se toman los primeros 900 puntos de la señal fisiológica (ECG). Esta metodología permite trabajar con señales medidas en entornos reales y procesarlas para obtener información útil.

**Fórmula utilizada:**
La señal es extraída en formato de matriz donde:
\[
señal = datos.p\_signal[:t, 0]
\]
Esto selecciona los primeros 900 puntos de la primera columna de la señal registrada.

---

### 2. Histograma de la Señal
Se grafica un histograma utilizando Seaborn para observar la distribución de los valores de la señal. Este histograma incluye un ajuste KDE para visualizar la densidad de probabilidad.

**Descripción:**
- Un histograma muestra la frecuencia de los valores de la señal en intervalos definidos.
- El ajuste KDE (Kernel Density Estimate) añade una curva suavizada que representa la densidad de probabilidad de los datos.

---

### 3. Graficado de la Señal (ECG)
Se grafica la señal fisiológica con etiquetas claras de tiempo y voltaje. Esta representación permite analizar el comportamiento de la señal a lo largo del tiempo.

**Propósito:**
- Identificar patrones o irregularidades en la señal original.
- Relacionar los valores de la señal con el tiempo en milisegundos (ms).

---

### 4. Estadísticos Descriptivos

#### 4.1. Cálculo Manual
Se implementan fórmulas programadas manualmente para calcular:
- **Media (\(\mu\))**:
\[
\mu = \frac{1}{n} \sum_{i=1}^{n} x_i
\]
Donde \(x_i\) son los valores de la señal y \(n\) es el número total de puntos.

- **Desviación Estándar (\(\sigma\))**:
\[
\sigma = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \mu)^2}
\]

- **Coeficiente de Variación (CV)**:
\[
CV = \frac{\sigma}{\mu}
\]

#### 4.2. Usando Funciones de NumPy
Se utilizan funciones predefinidas de NumPy como `np.mean` y `np.std` para calcular los mismos valores, optimizando el proceso y reduciendo errores de cálculo manual.

---

### 5. Función de Probabilidad
Se calcula la probabilidad de ocurrencia de cada valor único en la señal.

**Fórmula:**
Para un valor \(v\):
\[
P(v) = \frac{\text{Frecuencia Absoluta de } v}{\text{Total de Valores}}
\]

Esto permite construir una distribución discreta de probabilidad, mostrando la frecuencia relativa de cada valor único.

---

### 6. Ruido Añadido y SNR
Se contaminan las señales con diferentes tipos de ruido para analizar su impacto y calcular la relación señal-ruido (SNR):

#### 6.1. Ruido Gaussiano
Este tipo de ruido sigue una distribución normal con media cero. Se utiliza para simular perturbaciones aleatorias comunes en señales biomédicas.

**Fórmula:**
\[
ruido = \mathcal{N}(0, \sigma^2)
\]
Donde \(\sigma\) es la desviación estándar del ruido.

#### 6.2. Ruido de Impulso
Se añaden impulsos aleatorios para simular eventos bruscos en la señal.

**Fórmula:**
\[
ruido\_impulso = A \cdot I
\]
Donde:
- \(A\) es la amplitud del impulso.
- \(I\) es un vector binario indicando la presencia de impulsos.

#### 6.3. Ruido Tipo Artefacto
Se generan artefactos basados en una desviación estándar elevada para representar anomalías significativas.

#### Cálculo del SNR
La relación señal-ruido (SNR) se calcula para cada tipo de ruido, evaluando la calidad de la señal contaminada.

**Fórmula:**
\[
SNR = 10 \cdot \log_{10} \left(\frac{P_{señal}}{P_{ruido}}\right)
\]
Donde \(P\) representa la potencia promedio de la señal y del ruido.

---

### 7. Visualización
Se grafican las señales originales y contaminadas con ruido para observar visualmente las diferencias y los efectos de cada tipo de perturbación. Las gráficas incluyen etiquetas y leyendas para facilitar la interpretación.

---

## Resultado Esperado
- Histograma de la señal.
- Estadísticos descriptivos calculados manualmente y con NumPy.
- Función de probabilidad.
- Gráficas de señales contaminadas con ruido y sus SNR.

## Instrucciones
1. Descargar la señal desde bases de datos como PhysioNet.
2. Ejecutar el código en un entorno Python.
3. Subir este análisis a GitHub con el archivo `README.md` y las gráficas generadas como soporte visual.

## Resultado Esperado
- Histograma de la señal.
- Estadísticos descriptivos calculados manualmente y con NumPy.
- Función de probabilidad.
- Gráficas de señales contaminadas con ruido y sus SNR.

