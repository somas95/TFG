# Sistemas formadores de imágenes

## Sistemas fotográficos convencionales

En un sistema óptico ideal $M$ existen un conjunto infinito de pares de planos llamados *planos conjugados*, para los que a cada punto en un plano objeto le corresponde unívocamente un punto en su plano conjugado imagen. Las figuras que conforman un plano objeto y la correspondiente figura de su plano conjugado imagen están directamente relacionadas por una transformación de escala.

Un sistema fotográfico es un sistema óptico en el que se sitúa un medio fotosensible (sales de plata para fotografía analógica, un CCD para fotografía digital) en un plano imagen, registrando la intensidad que llega a su correspondiente plano objeto. Variando el sistema $M$ podemos ajustar dónde deseamos que esté el plano objeto para captarlo con fidelidad, ya que todos los planos que no sean el conjugado -fuera de foco- son registrados, pero desenfocados.

![Planos conjugados del mismo color](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/planos_conjugados.png)

## Holografía convencional

Para registrar información de la fase -en vez de simplemente la intensidad- se registra en un medio fotosensible el patrón de interferencia producido por un haz de referencia con el haz que ilumina el objeto en cuestión. Ambos haces provienen de una fuente de luz altamente coherente -generalmente LASER- que es dividida en dos mediante un beam splitter

![](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/holograma.svg)

El patrón registrado no es inteligible por si mismo, es necesario reconstruir la imagen iluminando el holograma con -a ser posible- un haz idéntico al haz de referencia usado para producir el holograma. Si la luz usada para reconstruir el holograma no es idéntica a dicho haz de referencia se pierde exactitud en la reproducción.


## Sistema FINCH

El sistema FINCH busca generar un patrón holográfico como el anterior pero sin el uso de láseres en el proceso. Para ello, en FINCH a cada punto del objeto le corresponde la proyección de una placa zonal de Fresnel (FZP o placa zonal en adelante) en el plano imagen. Una placa zonal es una figura descrita por una fórmula del tipo $$\dfrac{1\pm \cos{kr^2}}{2}$$ donde $k$ es una constante y $r$ es la distancia desde el centro de la placa a un punto dado. De esta manera, la posición de la FZP proyectada en el plano imagen determina la posición transversal del punto objeto, y la escala de la FZP, su posición axial:

![Esquema de funcionamiento de FINCH](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/esquema_finch.png)

Como en la holografía, y a diferencia de la fotografía convencional, donde el medio de registro proporciona directamente la imagen (o un negativo en fotografía analógica), para FINCH es necesario realizar una reconstrucción (de nuevo, analógica o digital) para recuperar la imagen deseada. Para ello se ilumina el holograma con una fuente de luz plana y coherente. La propia propagación reconstruye la imagen principal plano a plano:

![Sección transversal de la propagación del holograma FINCH de un punto](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/propagacion.png)
