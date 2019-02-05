# Simulaciones y resultados

Se buscaron las mejores condiciones experimentales que produjesen resultados claros y que no diesen problemas de muestreo, siendo la configuración mostrada anteriormente en la figura \ref{} la elegida, con aproximadamente dos metros de distancia entre la imagen original y la placa zonal, y uno entre ésta y el sensor, de 25 cm^2 de superficie y con una resolución de 1000 x 1000 píxeles. Se eligió un tamño para la placa zonal de 250 x 250 px, y 6.25 cm^2. Mostramos a continuación algunas de las pruebas realizadas y sus resultados:

## Holograma y reconstrucción de un punto

El holograma finch de un punto es el más sencillo de realizar, y permite detectar rápidamente si el sistema funciona correctamente o no. EL holograma es la proyeción de la FZP, siendo la reconstrucción en el plano focal un punto como es de esperar, aunque no perfecto debido a efectos de la difracción. A la izquierda de la figura \ref{} se puede apreciar el holograma, en el centro su reconstrucción en el plano focal y a la derecha el perfil transversal de dicha reconstrucción:

![\label{}Holograma, reconstrucción, y perfil](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/1_punto_holograma.png)

Si bien los efectos de la difracción son visibles, el perfil muestra que son residuales con respecto a la intensidad de la señal en el foco.

## Pruebas de resolución

Estudiamos también la mínima separación entre dos puntos que podemos resolver en las condiciones descritas (hay demasiadas variables como para poderlo hacer de forma genérica), separando las fuentes en intervalos de 1 píxel (250 $\mum$) hasta que en la reconstrucción podemos observar separación entre los picos. En la figura \ref{} mostramos tres perfiles para tres separaciones diferentes de las fuentes,a XX, XX y XX píxeles de distancia:

![\label{}Perfiles para la reconstrucción de dos puntos a diferentes distancias; sin resolver, en el límite de resolución, y completamente resueltos](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/resolucion.png){ width=75% }

Logramos resolver un mínimo de 0.6 mm de separación a una distancia de 3 m en las condiciones experimentales descritas.


## Pruebas de profundidad

Estudiamos también la capacidad de FINCH para poder reconstruir en cualquier plano después de haber tomado el holograma. Para ello disponemos tres fuentes a diferentes profundidades con respecto al plano de la FZP. Al reconstruir comprobamos que cada uno de los puntos es focalizado en un plano diferente, estando siempre los otros dos puntos desenfocados, como se puede observar en la figura \ref{}.

![\label{}](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/profundidad.png)

Es interesante hacer notar que la capacidad de focalizar de forma efectiva en un punto depende de la distancia a la FZP de la fuente original, siendo los artefactos debidos a difracción en magnitud y tamaño dependientes de ésta.

## Imágenes contínuas

Si bien el método desarrollado está diseñado para hacer hologramas de fuentes puntuales, consideramos la posibilidad de hacer hologramas de figuras contínuas aprovechando la propia discretización que introduce el hecho de simular las fuentes (y el resto del proceso) digitalmente. Así pues, si introducimos una densidad de fuentes igual a la de muestreo podemos realizar de forma efectiva el holograma de una fuente discreta:

## Reconstrucción de una figura 3D

Utilizamos como fuente un conjunto de 335 puntos alineados en 5 de las 12 aristas de un cubo. Podemos reconstruir diferentes planos del cubo con éxito y con considerable rapidez (menos de 1 segundo por plano a la hora de reconstruir), si bien a la hora de generar el holograma alcanzamos rápidamente límites de memoria, teniendo que renunciar a simulaciones más complejas y bien muestreadas. 

![Holograma y tres reconstrucciones de medio cubo](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/cube.png)



