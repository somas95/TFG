# Estudio por etapas de la propagación de la luz


## Aproximaciones para la propagación de la luz

>A desarrollar:

>Angular Spectrum method
>Conveniencia del uso de transformadas discretas rápidas de Fourier en nuestro usecase


## Esquema operativo

Las simulaciones realizadas han seguido el siguiente esquema general:

![](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/esquema_propagacion.svg)

Se han considerado muestras emisoras de luz bidimensionales y tridimensionales, propagando la luz emitida por esas muestras hasta la FZP, y volviendo a propagar desde la FZP hasta el objetivo geométricamente y mediante la FFT mencionada.

### Propagación de la fuente a la FZP

Tenemos una serie de fuentes puntuales e incoherentes entre sí. Cada fuente puntual es una fuente esférica:

$$u(r)=\frac{A}{r} e^{\pm i kr}$$

Al ser incoherentes entre sí podemos propagarlas independientemente hasta la FZP.

### Convolución con la FZP

La FZP utilizada fue definida como

$$real\left[\exp(-i \frac{\pi}{a}(x^2 + y^2))\right]$$

Para evitar problemas de frontera se convoluciona con un perfil gaussiano:

>¿Y si ponemos una máscara circular en vez de cuadrada?

![Fresnel Zone Plate](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/FZP2.png)

### Propagación de la FZP al CCD

Puesto que el frente de ondas a propagar no es trrivial no podemos resolver analíticamente la integral de difracción de Rayleigh-Sommerfeld Fraunhofer: 

$$U(x,y,z)=\frac{-i}{\lambda}\int U(x',y',0)\frac{z}{l^2}exp(ikl)\partial x'\partial y'$$

Utilizamos el método numérico desarrollado por Sheng-Wang[x](XXXXX); "Angular Spectrum propagation":

$$X=\mathscr{F}_{shift}(\mathscr{F}_2(\mathscr{F}(x)))$$
$$G=\exp(iZ\sqrt{\left(\frac{2\pi}{\lambda}\right)^2-x^2-y^2})$$
$$U=\mathscr{F}_{shift}(\mathscr{F}^{-1}_2(\mathscr{F}(XG)))$$

Permite calcular mediante transformadas rápidas de Fourier la propagación a una distancia z si

>Condición!

Sumamos las intensidades de cada frente de onda -por cada fuente puntual del objeto- propagado; obteniendo así el holograma FINCH

>Holograma

### Reconstrucción

Usamos de nuevo el método de propagación por espectro angular para reconstruir el holograma





