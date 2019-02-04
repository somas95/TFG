# Desarrollo teórico y experimental

## Sistemas formadores de imágenes

### Sistemas fotográficos convencionales{.unnumbered}

En un sistema óptico ideal $M$ existen un conjunto infinito de pares de planos llamados *planos conjugados*, para los que a cada punto en un plano objeto le corresponde unívocamente un punto en su plano conjugado imagen. Esto implica que a un punto que esté fuera del plano objeto le corresponden múltiples puntos en el plano imagen: se registra desenfocado.

![El punto azul (en el plano objeto) queda focalizado en el plano imagen, el punto naranja, fuera del plano objeto queda focalizado detrás del plano imagen, y desenfocado en éste\label{a}](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/planos_conjugados.svg)

Un sistema fotográfico es un sistema óptico en el que se sitúa un medio fotosensible (sales de plata para fotografía analógica, un CCD o CMOS para fotografía digital) en un plano imagen, registrando la intensidad que llega de su correspondiente plano objeto. Variando el sistema $M$ podemos ajustar dónde deseamos que esté el plano objeto para captarlo con fidelidad, ya que todos los planos que no sean el conjugado -fuera de foco- son registrados, pero desenfocados.[^1]

[^1]: Si se introducen otros elementos, como diafragmas, esto deja de ser del todo cierto y se hace necesario de hablar de conceptos como la profundidad de campo (de tener un único plano que queda focalizado pasamos a tener un rango de planos). En todo caso se pierde la información 3D de la imagen, y una vez tomada la fotografía es imposible cambiar la distancia focal.

### Holografía convencional{.unnumbered}

Para registrar información de la fase -en vez de simplemente la intensidad- se registra en un medio fotosensible el patrón de interferencia producido por un haz de referencia con el haz que ilumina el objeto en cuestión. Ambos haces provienen de una fuente de luz altamente coherente -generalmente láser- que es dividida en dos mediante un beam splitter (figura \ref{b})

![\label{b} Creación de un holograma: el CCD registra las diferencias de camino óptico entre la luz que viene del objeto y un haz de referencia, idéntico al usado para iluminar el objeto a registrar](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/holograma.svg)

El patrón registrado no es inteligible por si mismo, es necesario reconstruir la imagen iluminando el holograma con -a ser posible- un haz idéntico al usado para producir el holograma. Si la luz usada para reconstruir el holograma no es idéntica a dicho haz de referencia la reconstrucción se ve alterada.


### Sistema FINCH{.unnumbered}

El sistema FINCH busca generar un patrón holográfico como el anterior pero sin el uso de láseres en el proceso. Para ello se usan proyecciones de placas zonales de Fresnel (FZP o placas zonales en adelante), una figura descrita por una fórmula del tipo $$\dfrac{1\pm \cos{kr^2}}{2}$$ donde $k$ es una constante y $r$ es la distancia desde el centro de la placa a un punto dado. Tienen la propiedad de focalizar la luz como si de un lente se tratase, pero en vez de por medio de refracción, lo hacen mediante difracción; en el punto focal[^2] las interferencias son constructivas y en el resto del espacio, destructivas, como se puede apreciar en la figura \ref{c}

 ![\label{c} FZP y corte transversal de la propagación del frente de ondas. La luz converge por medio de difracción en un punto](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/fzp_convergence.png){ width=65% }

De esta manera, la posición de la FZP proyectada en el plano imagen determina la posición transversal del punto objeto, y la escala de la FZP, su posición axial (figura \ref{d}):

![\label{d}La posición de la fuente objeto queda codificada en la posición y tamaño de la FZP en el holograma FINCH](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/esquema_finch_1.png)

Como en la holografía, y a diferencia de la fotografía convencional, donde el medio de registro proporciona directamente la imagen (o un negativo en fotografía analógica), para FINCH es necesario realizar una reconstrucción (de nuevo, analógica o digital) para recuperar la imagen deseada. Para ello se ilumina el holograma con una fuente de luz plana y coherente. La propia propagación reconstruye la imagen principal plano a plano:

[^2]: Según la construcción de la FZP puede tener un foco o infinitos, separados periódicamente en el eje perpendicular a la placa zonal.

