# Estudio por etapas de la propagación de la luz

## La luz como onda EM

La luz es una onda electromagnética, y se propaga como tal. Viene descrita por las ecuaciones de Maxwell:

$$
\begin{aligned}
\nabla \cdot \vec{E} &=0 \\
\nabla \times \vec{E} &=-\frac{\partial \vec{B}}{\partial t}\\
\nabla \cdot \vec{B} &=0\\
\nabla \times \vec{B} &=\mu_0 \epsilon_0 \frac{\partial \vec{E}}{\partial t}
\end{aligned}
$$

De estas ecuaciones se pueden deducir las ecuaciones de ondas de un campo EM:

$$
\begin{aligned}
\nabla ^2 \vec{E} - \frac{1}{c^2} \frac{\partial ^2 \vec{E}}{\partial{t^2}} &= 0
-\nabla ^2 \vec{B} - \frac{1}{c^2} \frac{\partial ^2 \vec{B}}{\partial{t^2}} &= 0
\end{aligned}
$$

Según la complejidad del campo inicial a propagar es conveniente usar diferentes métodos y aproximaciones

## Aproximaciones para la propagación de la luz

>A desarrollar


## Esquema operativo

Las simulaciones realizadas han seguido el siguiente esquema general:

>Esquema

Se han considerado muestras bidimensionales y tridimensionales emisoras de luz, propagando la luz emitida por esas muestras hasta la FZP, y volviendo a propagar desde la FZP hasta el objetivo geométrica y ondulatoriamente.

## Propagación de la fuente a la FZP

Tenemos una serie de fuentes puntuales e incoherentes entre sí. Cada fuente puntual es una fuente esférica:

$$u(r)=\frac{A}{r} e^{\pm i kr}$$

## Convolución con la FZP

La FZP utilizada fue definida como

$$real\left[\exp(-i \frac{\pi}{a}(x^2 + y^2))\right]$$



