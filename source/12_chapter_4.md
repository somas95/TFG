# Aliasing

Cuando una señal periódica se muestrea con una frecuencia menor al doble de la frecuencia máxima de la señal a muestrear (también conocida como frecuencia de Nyquist), no se puede reconstruir unívocamente la señal original. Este fenómeno se conoce como *aliasing* y una vez producido no se puede corregir. 

>Esquema aliasing

Siendo un fenómeno que se suele dar en la conversión de señales analógico-digital, hemos tenido que prevenirlo y detectarlo. Los hologramas son aliasados con suma facilidad -propagamos señales con frecuencias muy altas, la FZP también puede llegar a tener frecuencias altas con respecto a la densidad de píxeles con que se muestrea la imagen-, y un holograma aliasado no sólo es erróneo, no se puede reconstruir con fidelidad.

## Prevención

>Análisis máxima frecuencia permitida
>Fine tuning de parámetros de simulación

## Detección

No es trivial detectar que un holograma está aliasado, así que se hace necesario desarrollar una herramienta que permita descartar imágenes aliasadas para no hacer reconstrucciones a partir de ellas y atribuir a otros tipos de errores los que son puramente de aliasing. 

Para ello se ha diseñado un kernel de convolución para detectar altas frecuencias en la imagen:

## Matrices de convolución para detección de features en una imagen

