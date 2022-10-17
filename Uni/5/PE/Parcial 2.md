---
tags: [uni mates]
---
# Introducción a la probabilidad
## Conceptos básicos de teoría de conjuntos
### Conjunto
- **Conjunto**: Una colección de objetos determinados, distintos. Los objetos se denomina los elemenots o miembros del conjunto.
- Se representan con letras Mayúsculas.
- Los elementos se presentan con minúsculas.
### Relación de pertenencia
Se usa el símbolo $\in$ para mostrar pertenencia:
$$x\in A$$
Esto es igual a $x$ es miembro/elemento de $A$.

Para decir que algo no está dentro se tacha el símbolo, $\notin$.

### Notación de conjuntos

- Extensional: Escribir todos los elementos del conjunto ($A=\{1,2,3,4\}$)
- Intencional: Los define mediante características o algoritmos  ($A=\{ 2n | n \in \mathbb{N}\}$)

### Subconjuntos y conjuntos notables
Si $A$ y $B$ son conjuntos se dice que $A$ es subconjunto de $B$ si todos los elementos de $A$ están también en $B$. Se denota con el símbolo: $\subset$ o $\subseteq$ 
$$A\subset B$$
También se puede negar: $\nsubseteq$. 

Los conjuntos son iguales siempre y cuando:
$$A\subset B ; B \subset A$$
-  Operaciónes entre conjutos
	- Unión $A\cup B$ como la suma se quedan los elementos de A + B y no hay repetidos.
	- Intersección $A\cap B$ solo los que están en los dos. 
	- Complemento $A^c$ o $\bar{A}$ Todos los elementos del universo que NO están en $A$.  

- **Conjunto Universo**: Contiene todos los elementos con los que trabajamos ($U$).
	- Cualquier conjunto es su subconjunto.
- **Conjunto Vacío**: No tiene elementos ($\{\}, \emptyset$).
	- Subconjunto de cualquier conjunto.

## Conceptos básicos de probabilidad
- **Espacio muestral**: Colección de todos los resultados individuales posibles de un experimento $\Omega$.
- **Punto muestral**: Cada uno de los elementos de $\Omega$.

```mermaid
graph LR;
	Evento--Evento Simple;
	Evento--Evento Compuesto;
```
- **Evento**: cualquier subconjunto del espacio muestral.
- **Evento simple**: Evanto que contiene un único punto muestral.
- **Evento Compuesto**: Evento que contiene dos o más puntos muestrales.
	- Si se le puede obtener mediante operaciones entre eventos simples
		- Unión
		- Complemento
## Enfoques de la probabilidad
### Clásico (A priori)
Se asume que los casos son igualmente probables. Cada evento tiene la posibilidad de la siguiente fracción.
$$\frac{1}{n}$$
### Fecuentista (De verosimilitud)
Si un experimento se repitió $N$ veces y el evento $A$ ocurrió $n_a$ veces, la probabilidad de $A$ es:
$$\frac{n_a}{N}$$

### Subjetivo (Bayesiano)
Un experto estima con base a su conocimiento (al parecer es inceríblemente bueno).
**TODO:** investigar más porque no creo que sea sólo eso.

## Probabilidad Axiomática
- Una función $P$ es una función de probabilidad si satisface los siguientes 3 axiomas.
	1. $A \in A, P(A) \geq 0$: No hay probabilidades negativas.
	2. $P(\Omega$) = 1: La suma de las probabilidades de todos los eventos simples debe ser igual a 1.
	3. La probabilidad es numerablemente aditiva. La probabilidad de la unión es igual a la suma de las probabilidades.
## Probabilidad del complemento de un evento
Sea $A$ un evento y $A'$ su complemento, entonces -> $P(A') = 1-P(A)$

# Introducción a las variables aleatorias discretas
## Variables Aleatorias
- **VARIABLE**: Cualquier característica que de los individuous de la población que podemos clasificar, contar o medir.
- Definición desde el punto de vista de Teoría de Probabilidades es: Una función que le asocia a cada elemento de un espacio muestral $\Omega$, un número real.
- Se usan letras mayúsculas para representar variableas aleatorias.
- Letras minúscula para los valores de estas variables.
- Hay variables aleatorias **discretas** y **continuas**.
	- Discreta si asume una cantidad **finita**/**contable**.
	- Si puede ser una cantidad infinita de valores.

# Distribución de probabilidad
- **DEFINICIÓN:** Para una variable aleatoria $X$ es una regla que proporciona la probabilidad de ocurrencia de cada uno de los valores de $X$.

- Cuando se da como una fórmula se le denomina de dos formas:
	1. Función de densidad de probabilidad (variable continua).
	2. Función de masa de probabilidad (variable discreta).
 
## Función de masa de probabilidad (variable discreta).
- Se tienen que cumplir dos axiomas para que estas funciónes sean verdad.
	1. $f(x_i) \geq 0, \forall x_i$ 
	2. $\Sigma_i f(x_i) = 1$

### Función de distribución de una variable aleatoria
Se define por:

$$F(x) = P(X\leq x)$$

- Va "acumulando" probabilidades hasta el valor $x$.

|$x$|$f(x) = P(X = x)$ | $F(x) = P(x \leq x)$|
|--|--------------------|------------------|
|0 | 0.05  | $F(0) = P(x \leq 0) = P(X< 0) + P(x = 0) = 0+0.05$ |
| 1 | 0.10 | $F(1) = P(x < 1) + P(x = 1) = 0.05 + 0.10 = 0.15$|
| 2 | 0.45 | $F(2) = 0.05 + 0.10 + 0.45 = 0.60$|
| 3 | 0.40 | $F(3) = 1$|

En otras palabras: 

$$F(x) = \sum_{k=x_1}^x f(k) = f(x_1) + f(x_2) + ... + f(x)$$


#### Propiedades
1. El valor mínimo que asume $F$ es 0.
2. El valor máximo que asume $F$ es 1.
3. La función $F$ es continua por la derecha.



# Distribuciones discretas de probabilidad
## Distribución de Bernoulli
$$X\sim Ber(p)$$
Su **Función de masa de probabilidad (FMP)** es:
$$f(x) = p^xq^{1-x}; x = 0,1$$
En otras palabras:
$$f(x) = p^x(1-p)^{1-x}; x = 0, 1$$
Valor esperado:
$$E(X) = p$$
Varianza:
$$Var(X) = p(1-p)$$
## Número de combinaciones
Se lee normalmente de $n$ tomar $r$.	
$$\binom{n}{r} = _nC_r$$
$$\binom{n}{r} = \frac{n!}{r!(n-r)!}$$
### Propiedades básicas de las combinaciones
1. $\binom{n}{0} = \binom{n}{n} = 1$
2. $\binom{n}{1} = \binom{n}{n-1} = 1$

## Distribución Binomial
- $n$ ensayos Bernoulli independientes.
- La probabilidad de éxito $p$ se mantiene constante a lo largo.
- Tenemos una variable de interés $X$, la cual cuenta el número de éxitos en los $n$ ensayos.

Esto se distribuye binomial con parámetros $n$ y $p$, se representa: $X \sim Binomial(n,p)$ 

FMP de $X$ es:
$$f(x) = \binom{n}{x}p^x(1-p)^n-x; x=0,1,2,3,...,n$$
Su valor esperado será:

$$E(X) = np$$
Su varianza es:

$$Var(X) = np(1-p)$$

## Distribución Hipergeométrica

- Se tiene una población con un número finito de elemento $N$.
- Hay $k$ elemenots del tipo 1 y $N-k$ del tipo 2.
- Se extraen $n$ elementos sin reemplazo.
- Sea $X$ el número de elementos de tipo 1 entre los extraídos.
- Su símbolo es: $X \sim Hip(N, k, n)$

$$f(x) = \frac{\binom{k}{x}\binom{N-k}{n-x}}{\binom{N}{k}}: max\{0, k-(N-n)\} \leq x \leq min\{n, k\}$$
$$E(X) = \frac{nk}{N}$$
$$Var(X) = \frac{nk(N-k)(N-n)}{N^2(N-1)}$$
## Distribución Poisson
- Eventos "raros", su probabilidad se considera pequeña. 
- Estos eventos pueden ser constantes y les denominamos $\lambda$.
- $\lambda$ depende solo del tamaño del intervalo.
- $X \sim Poi(\lambda)$
- Su fmp es:
$$f(x) = \frac{\lambda e^{-\lambda}}{-x!}; x=0,1,2,...$$
- Valor esperado:
$$E(x) = \lambda $$
- Varianza:
$$Var(X) = \lambda$$
## Distribución geométrica

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
