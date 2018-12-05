# Aliasing

Cuando una señal periódica se muestrea con una frecuencia menor al doble de la frecuencia máxima de la señal a muestrear (también conocida como frecuencia de Nyquist), no se puede reconstruir unívocamente la señal original. Este fenómeno se conoce como *aliasing* y una vez producido no se puede corregir. 

>Esquema aliasing

Siendo un fenómeno que se suele dar en la conversión de señales analógico-digital, hemos tenido que prevenirlo y detectarlo. Los hologramas son aliasados con suma facilidad -propagamos señales con frecuencias muy altas, la FZP también puede llegar a tener frecuencias altas con respecto a la densidad de píxeles con que se muestrea la imagen-, y un holograma aliasado no sólo es erróneo, no se puede reconstruir con fidelidad.

En concreto en las simulaciones realizadas hay que controlar no sólo que no se produzca en el muestreo del holograma, si no en todas y cada una de las fases de la simulación.

## Prevención

>Análisis máxima frecuencia permitida

>Fine tuning de parámetros de simulación

>Parámetros ajustables y no ajustables. Limitaciones prácticas

Puesto que FINCH está orientado a ser aplicado en sistemas reales conviene introducir los mismos constraints que aplican en la vida real en la simulación. Esto implica que algunos parámetros no podremos ajustarlos arbitrariamente, a saber:

* La frecuencia de la luz
* Los tamaños de la FZP y la imagen
* La resolución de la FZP y la imagen
* Las distancias de propagación



## Detección

No es trivial detectar que un holograma está aliasado, así que se hace necesario desarrollar una herramienta que permita descartar imágenes aliasadas para no hacer reconstrucciones a partir de ellas y atribuir a otros tipos de errores los que son puramente de aliasing. 

Para ello se ha diseñado un kernel de convolución para detectar altas frecuencias en la imagen:

### Matrices de convolución para detección de aliasing en una imagen

En nuestro contexto hablamos de la convolución de una matriz kernel (generalmente de 3x3) con una matriz imagen. Para cada elemento de la matriz imagen tomamos una submatriz centrada en éste y del tamaño del kernel. Asignaremos a este elemento la suma de las multiplicaciones elemento a elemento de la submatriz y el kernel, es decir, si $R_{ij}$ es el elemento $i,j$ de la matriz resultante de la convolución, $I$ es la matriz imagen, $S$ la submatriz del tamaño del kernel centrada en $I_{ij}$ y $K$ la matriz kernel:

$$R_{ij}=\sum_{i,j} K_{i,j}*S_{i,j}$$

Al ser una operación que modifica el valor de un elemento en función de los valores de los elementos adyacentes (en un menor o mayor radio) es una buena candidata para el caso que nos ocupa, en el que queremos detectar variaciones altas de valores en píxeles adjuntos, indicadoras de aliasing. 

Existen muchos kernels indicados para diferentes propósitos, para el caso que nos ocupa diseñamos el siguiente, que ofrece resultados consistentes y precisos:

$$
\begin{bmatrix}
    0 & -1 & 0 \\
    -1 & 4 & -1 \\
    0 & -1 & 0
\end{bmatrix}
$$

La convolución de este kernel con una imagen realza los patrones "de ajedrez" indicadores de aliasing (variaciones de muy alta frecuencia píxel a píxel) y promedia a ~0 las variaciones de baja frecuencia entre píxeles adyacentes. Contando la proporción de píxeles con valores por encima de un cierto umbral con respecto al número total de píxeles podemos determinar con un alto grado de fiabilidad si la imagen está aliasada o no.

>Demo aliasing detection

