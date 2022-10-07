---
tags: [uni mates]
---
# Distribución Hipergeométrica

Se tiene una población con un número finito de elemento $N$.


$$f(x) = \frac{\binom{k}{x}\binom{N-k}{n-x}}{\binom{N}{k}}$$

# Distribución Poisson

$$f(x) = \frac{\lambda e^{-\lambda}}{-x!}$$

# Distribuciónes continuas de probabilidad
## Variables continuas de probabilidad
- Una variable aleatoria continua como aquella que tiene cualquier valor entre $[a,b]$.
- Sea $X$ una variable aleatoria.
- Si existe una función $F$ tal que se puede representar de la siguiente forma:
$$F(x) = P(X\leq x) = \int_\infty^x f(t)dt$$
## Propiedades
- La función de distribución de $F$ es la integral de la densidad, $f$.
- La función de densidad $f$, es la derivada de la función de distribución, $F$.
- Por el **teorema fundamental del cálculo** podemos calcular probabilidades para $X$ sin evaluar la integral.
- Solo hay que evaluar $F$ en los extremos.
- Por el teoréma de del cálculo tampoco tiene sentido el hablar de un solo valor sino a un intervalo ($\int_a^af(x)dx = 0$).

## Valor esperado y varianza de una variable aleatoria continua
### Valor esperado
$$ E(X) = \int_{D_{x}}xf(x)dx$$
- E(x) es el valor promedio de la variable.
- Parámetro estimado mediante la media aritmética.
#### Propiedades
- $E(a) = a$
- $E(bx) = bE(x)$
- $E(a+bx) = a+bE(x)$

### Varianza
$$E([X-\mu x]^2) = \int_{D_x} (x-\mu_x)^2f(x)dx$$
- $Var(a) = 0$
- $Var(bX) = b^2Var(X)$
- $Var(a+X) = Var(X)$
- $Var(a+bX) = b^2Var(X)$

## Distribución Uniforme
- Sea $X$ una variable aleatoria.
- La distribución de uniforme se representa de la siguiente forma: $X \sim U(a,b)$
$$f(x) = \frac{1}{b-a}; a\leq x \leq b$$
Con esto en mente entonces su valor esperado y su varianza son lo siguiente:

$$E(X) = \frac{a+b}{2}$$
$$Var(X) = \frac{(b-a)^2}{12}$$
Su distribución es:
$$F(X)=\frac{x-a}{b-a}$$
Y cuando se tiene un rango y se quiere obtener la distribución es la siguiente fórmula:
$$P(c\leq X \leq d) = \frac{d-c}{b-a}$$

## Distribución Exponenecial
La densidad de la probabilidad tiene la siguiente forma:
$$f(x) = \lambda e^{- \lambda x}; x\geq0$$
Y su función de distribución es:
$$F(x) = 1 - e^{\lambda x};x\geq0$$
Si tenemos $X \sim Exp(\lambda)$ entontces podemos demostrar lo siguiente:
$$\mu_x \equiv E(X) = \frac{1}{\lambda}$$
$$\sigma_x^2 \equiv Var(x) = \frac{1}{\lambda^2}$$
Es para cuando es $x$ es mayor a 0.
## Distribución normal
La fórmula de la distribución estándar es la siguiente:
$$f(x) = \frac{1}{\sqrt{2\pi}} e^{- \frac{x^2}{2}}$$

### Propiedades
