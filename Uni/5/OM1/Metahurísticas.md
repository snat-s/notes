# Introducción

Algoritmo generalizado para resolver un problema. Cada problema necesita sus objetivos. 

1. Un problema de quieres resolver
2. Como vas a evaluar esa solución para que la entienda

# Recocido Simulado

*Simulated Annealing* es una metahurística que simula el recocido de un metal se calienta a una temperatura cerca del punto de fusión y seguido de esto se enfría para permitir que las partículas se muevan hacia un estado de mínima energía.

## Proceso de enfriamiento

Inicialmente los valores de $T$ son grandes y aceotan cualquier solución (estado). Cuando $T$ tiende a cero, se dejan de aceptar soluciones.

Convergencia: el algoritmo se detiene cuando se le acaba la temperatura.

## Criterio de aceptación-rechazo de Metropolis

El criterio de aceptación determina si $\hat{x}$ se acepta o rechaza como solución en la iteración $k+1$, con la siguiente probabilidad:

$$ Pr(\text{aceptar } \hat{x}) = $$

$$$$$$a_{n+1} =\begin{cases} a_{n} & \text{if} & f(a_n) \cdot f(r_n) < 0 \\
                     r_{n} & \text{if} &  f(a_n) \cdot f(r_n) > 0
       \end{cases}$$

Para implementar lo anterior, en el caso que $f(\hat{x}) \geq f(x_k)$, es necesario realizar lo siguiente:
Si:
$$U(0, 1) < exp[(f(x_k)-f(\hat{x}))/T]$$

El éxito depende de los parámetros.