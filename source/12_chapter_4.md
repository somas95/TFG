## Aliasing

Cuando una señal periódica se muestrea con una frecuencia menor al doble de la frecuencia máxima de la señal a muestrear (también conocida como frecuencia de Nyquist), no se puede reconstruir unívocamente la señal original. Este fenómeno se conoce como *aliasing* (figura \ref{h}) y una vez producido no se puede corregir. 

![\label{h}Si la señal original (roja) no se muestrea correctamente (los puntos negros), la reconstrucción es incorrecta (línea de puntos)](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/aliasing.svg){ width=75% }

Siendo un fenómeno que se suele dar en la conversión de señales analógico-digitales, hemos tenido que prevenirlo y detectarlo. Los hologramas son *aliasados* con suma facilidad -propagamos señales con frecuencias muy altas, y la FZP también puede llegar a tener frecuencias altas con respecto a la densidad de píxeles con que se muestrea la imagen-, y un holograma *aliasado* no sólo es erróneo, no se puede reconstruir.

En concreto en las simulaciones realizadas hay que controlar no sólo que no se produzca *aliasing* en el muestreo del holograma, si no en todas y cada una de las fases de la simulación.

### Prevención{.unnumbered}

Puesto que FINCH está orientado a ser aplicado en sistemas reales conviene introducir en la simulación las mismas restricciones que aplicarían en la vida real. Esto implica que algunos parámetros no podremos ajustarlos arbitrariamente, a saber:

* La frecuencia de la luz
* Los tamaños de la FZP y la imagen
* La resolución de la FZP y la imagen
* Las distancias de propagación

El hecho de estar haciendo simulaciones por ordenador también introduce sus propias limitaciones en este aspecto, principalmente debido a los límites de precisión que tiene una variable en coma flotante.  


### Detección{.unnumbered}

No es trivial detectar que un holograma está *aliasado*, y si bien mediante inspección ocular se pueden identificar los artefactos típicos de *aliasing*, deja de ser práctico en el momento en el que se simulan cientos de propagaciones de forma sistemática. Así que se hace muy conveniente desarrollar una herramienta que permita descartar imágenes *aliasadas* automáticamente

Para ello se ha diseñado un kernel de convolución para detectar altas frecuencias en la imagen.

#### Matrices de convolución para detección de aliasing en una imagen{.unnumbered}

En nuestro contexto hablamos de la convolución de una matriz kernel (generalmente de 3x3) con una matriz imagen. Para cada elemento de la matriz imagen tomamos una submatriz centrada en éste y del tamaño del kernel. Asignaremos a este elemento la suma de las multiplicaciones elemento a elemento de la submatriz y el kernel.

Al ser una operación que modifica el valor de un elemento en función de los valores de los elementos adyacentes (en un menor o mayor radio) es una buena candidata para el caso que nos ocupa, en el que queremos detectar variaciones altas de valores en píxeles adjuntos, indicadoras de aliasing. 

Existen muchos kernels indicados para diferentes propósitos, para el caso que nos ocupa diseñamos el siguiente, que ofrece resultados consistentes y precisos:

$$
\begin{bmatrix}
    0 & -1 & 0 \\
    -1 & 4 & -1 \\
    0 & -1 & 0
\end{bmatrix}
$$

La convolución de este kernel con una imagen realza los patrones "de ajedrez" indicadores de *aliasing* (variaciones de muy alta frecuencia píxel a píxel) y promedia a ~0 las variaciones de baja frecuencia entre píxeles adyacentes, como se puede apreciar en la figura \ref{i}.

![\label{i} Ejemplos de imagen *aliasada* (a) y no *aliasada* (c). A la derecha, los resultados de aplicar el kernel de convolución: mientras que en la imagen no *aliasada* no hay apenas píxeles blancos (d), en la *aliasada* se ponen de manifiesto con claridad (b)](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/aliasing detection3.png){ width=75% }

 Contando la proporción de píxeles con valores por encima de un cierto umbral con respecto al número total de píxeles podemos determinar con un alto grado de fiabilidad si la imagen está *aliasada* o no.


