\newpage
## Esquema experimental

Se han generado y reconstruido hologramas FINCH mediante simulaciones numéricas por ordenador. Hemos considerado el sistema descrito en la figura \ref{e} (no a escala), considerando una longitud de onda de 500 nm:

![\label{e}](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/esquema_experimental.png){ width=75% }

Detallamos a continuación el procedimiento seguido etapa a etapa:

#### Propagación de la fuente a la FZP{.unnumbered}

Partimos de una serie de fuentes puntuales e incoherentes entre sí. Cada fuente puntual es una fuente esférica:

$$u(r)=\frac{A}{r} e^{\pm i kr}$$

Al ser incoherentes entre sí podemos propagarlas independientemente hasta la FZP, que actúa de modulador de transmitancia:

#### Convolución con la FZP{.unnumbered}

La FZP utilizada fue definida como

$$real\left[\exp(-i \frac{\pi}{a}(x^2 + y^2))\right]$$

Para evitar problemas de frontera se convoluciona con una ventana cuadrada a la que se ha aplicado desenfoque gaussiano (figura \ref{f}):

![\label{f}Fresnel Zone Plate](/home/manu/Documents/Uni/Cuarto repetido/2/TFG md/tfg_markdown/source/figures/FZP2.png)

Así pues el frente de ondas de cada fuente puntual queda modulado por la FZP descrita.

#### Propagación de la FZP al CCD{.unnumbered}

Puesto que el frente de ondas a propagar no es trivial, no podemos resolver analíticamente la integral de difracción de Rayleigh-Sommerfeld: 

$$U(x,y,z)=-\frac{i}{\lambda}\int U(x',y',0)\frac{z}{l^2}exp(ikl)\partial x'\partial y'$$

Utilizamos el método numérico desarrollado por Sheng-Wang[x](XXXXX); "Angular Spectrum propagation", que permite calcular mediante transformadas rápidas de Fourier la propagación a una distancia z:

$$X=DFT_{shift}(DFT_2(DFT(x)))$$
$$G=\exp(iZ\sqrt{\left(\frac{2\pi}{\lambda}\right)^2-x^2-y^2})$$
$$U=DFT_{shift}(DFT^{-1}_2(DFT(XG)))$$

La idea detrás del método es descomponer el frente de ondas en un sumatorio infinito de ondas planas de diferentes frecuencias (descomposición de Fourier), $X$, que son después multiplicadas por un término que tiene en cuenta el cambio en la fase para cada una de ellas en su propagación, $G$. Aplicando la transformada inversa recuperamos el frente de ondas $U$ una vez propagado.

Puesto que estamos trabajando en un ámbito discreto, las transformadas de Fourier pasan a ser transformadas discretas de Fourier, o $DFT$.

Una vez en el plano del holograma podemos sumar en intensidad los frentes de ondas propagados correspondientes a cada una de las fuentes originales, obteniendo así el holograma FINCH.


#### Reconstrucción{.unnumbered}

Los hologramas FINCH se reconstruyen como los hologramas convencionales, siendo iluminados por una fuente láser. En holografía digital, y por tanto también en nuestro caso, se multiplica el holograma por una onda plana, siendo la propagación de ésta -de nuevo, propagación por espectro angular- la imagen 3d reconstruida.

