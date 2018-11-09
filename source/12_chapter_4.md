# Aliasing

Cuando una señal periódica se muestrea con una frecuencia menor al doble de la frecuencia máxima de la señal a muestrear (también conocida como frecuencia de Nyquist), no se puede reconstruir unívocamente la señal original. Este fenómeno se conoce como *aliasing* y una vez producido no se puede corregir. 

>Esquema aliasing

Siendo un fenómeno que se suele dar en la conversión de señales analógico-digital, hemos tenido que prevenirlo y detectarlo. Los hologramas son aliasados con suma facilidad -propagamos señales con frecuencias muy altas, la FZP también puede llegar a tener frecuencias altas con respecto a la densidad de píxeles con que se muestrea la imagen-, y un holograma aliasado no sólo es erróneo, no se puede reconstruir con fidelidad.

## Prevención

>Análisis máxima frecuencia permitida

>Fine tuning de parámetros de simulación

>Parámetros ajustables y no ajustables. Limitaciones prácticas

## Detección

No es trivial detectar que un holograma está aliasado, así que se hace necesario desarrollar una herramienta que permita descartar imágenes aliasadas para no hacer reconstrucciones a partir de ellas y atribuir a otros tipos de errores los que son puramente de aliasing. 

Para ello se ha diseñado un kernel de convolución para detectar altas frecuencias en la imagen:

## Matrices de convolución para detección de features en una imagen

En nuestro contexto hablamos de la convolución de una matriz kernel (generalmente de 3x3) con la matriz imagen. A cada elemento de la matriz imagen corresponde el resultado de la multiplicación matricial (o variantes según la definición de la convolución) de la submatriz centrada en ella del tamaño del kernel por el propio kernel. Esto permite realizar operaciones "context-aware", para las que la transformación de un píxel depende de los valores de los píxeles que le rodean. Ésto la hace una buena candidata para el caso que nos ocupa, en el que queremos detectar variaciones altas de valores en píxeles adjunto, indicadoras de aliasing. 

Después de un proceso iterativo llegamos al siguiente kernel, que nos ofrece unos resultados satisfactorios y permite detectar automáticamente aliasing en nuestras imágenes:
