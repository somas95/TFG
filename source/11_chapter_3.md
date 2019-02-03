\newpage
## Esquema experimental

Se han generado y reconstruido hologramas FINCH mediante simulaciones numéricas por ordenador. Hemos considerado el sistema descrito en la figura \ref{e}:

![\label{e}](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/esquema_experimental.png){ width=75% }

Detallamos a continuación 

#### Propagación de la fuente a la FZP{.unnumbered}

Partimos de una serie de fuentes puntuales e incoherentes entre sí. Cada fuente puntual es una fuente esférica:

$$u(r)=\frac{A}{r} e^{\pm i kr}$$

Al ser incoherentes entre sí podemos propagarlas independientemente hasta la FZP.

#### Convolución con la FZP{.unnumbered}

La FZP utilizada fue definida como

$$real\left[\exp(-i \frac{\pi}{a}(x^2 + y^2))\right]$$

Para evitar problemas de frontera se convoluciona con una ventana cuadrada a la que se ha aplicado desenfoque gaussiano (figura \ref{f}):

![\label{f}Fresnel Zone Plate](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/FZP2.png)

#### Propagación de la FZP al CCD{.unnumbered}

Puesto que el frente de ondas a propagar no es trivial, no podemos resolver analíticamente la integral de difracción de Rayleigh-Sommerfeld: 

$$U(x,y,z)=-\frac{i}{\lambda}\int U(x',y',0)\frac{z}{l^2}exp(ikl)\partial x'\partial y'$$

Utilizamos el método numérico desarrollado por Sheng-Wang[x](XXXXX); "Angular Spectrum propagation", que permite calcular mediante transformadas rápidas de Fourier la propagación a una distancia z:

$$X=DFT_{shift}(DFT_2(DFT(x)))$$
$$G=\exp(iZ\sqrt{\left(\frac{2\pi}{\lambda}\right)^2-x^2-y^2})$$
$$U=DFT_{shift}(DFT^{-1}_2(DFT(XG)))$$

Sumamos las intensidades de cada frente de onda -por cada fuente puntual del objeto- propagado, obteniendo así el holograma FINCH.


#### Reconstrucción{.unnumbered}

Usamos de nuevo el método de propagación por espectro angular para reconstruir el holograma en el plano deseado.






