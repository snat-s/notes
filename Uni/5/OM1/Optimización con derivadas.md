# Optimización con derivadas

## Definición de una derivada

$f'(x) = \lim_x \frac{f(x + \Delta x) - f(x)} {\Delta x}$

Podemos sacar la derivada en python utilizando la librería *sympy*.

```python
from sympy import *

x, y, z = symbols('x y z')
init_printing(use_unicode=True)

derivative1 = diff(cos(x), x)

derivative2 = diff(exp(x**2), x)
```

Una aproximación sencilla utilizando la formula para encontrar los mínimos o máximos.

## Implementación de una derivada
La implementación de la definición de una derivada. Donde $f$ es la función original $derivada$ es la definición de la derivada, y $x$ es el movimiento.

```python
f = lambda x : x**4-20*x**3+0.1*x
derivada = lambda x, delta_x : (f(x+delta_x)-f(x))/delta_x

error = 0.00000001
delta_x = 0.01
paso_normal = 0.1
x = 1

while derivada(x, delta_x) <= error:
    print("La derivada en ", x, " es ", derivada(x, delta_x))
    x += paso_normal


print("Lo encontramos en: ", x)
```

## Criterios de paro
- Diferencia absoluta entre dos valores de la función.

$|f(x_k+1) - f(x_k)|  < \epsilon$

- La norma de la función gradiente
$||\nabla f(x_k) || < \epsilon$

# Algoritmo de la bisección
TODO: Código de bisección de la clase de Cálculo numérico.

```python
def biseccion(a,b,e,delta_x):
	alpha = (a+b)/2
	f_prime_a = derivative(a)
	f_prime_alpha = derivative(alpha)
	
	if f_prime_a < 0 and f_prime_alpha < 0:
		b = alpha
		a = alpha
	elif abs(a - b) < e:
		alpha = (a+b)/2
		f_prime_a = derivative(a)
		f_prime_alpha = derivative(alpha)
	else:
		x = a
		f(x*) = f(a)
```

```python
import math

a = 1	# cota 1
b = 2	# cota 2
n = 500 # n de iteraciones
r = 0	# raíz
t = 1e-20  # tolerancias
i = 1  # iteraciones

# evaluar el polinomio en el punto dado
def funcion(n):
    #  x^3 + 4x^2 - 10 = 0 [1,2]
    return  (n**3 + 4*n**2 - 10)

# algoritmo de la biseccion, lo unico que no me gusta es que
# no hay una funcion de sign en python entonces por eso estan
# lineas 23 y 24

while i <= n:
    r = (a+b)/2
    if funcion(r) == 0 or (b-a)/2 < t:
        print(r)
        quit()
    i += 1
    temp1 = math.copysign(1, funcion(r))
    temp2 = math.copysign(1, funcion(a))
    if temp1 == temp2:
        a = r
    else:
        b = r

print("No se encontro la solucion")

```
# Algoritmo de gradiente ascendente
## Input

x <- Random initial vecotr
alpha <- tamaño de paso

```python

def gradiente_ascent(x):
	while x --> ideal solution.
		x = x + alpha*gradient(f(x)) # In one dimension x = x + alpha*derivative(f(x))
	return x
```

Este algoritmo es para encontrar un mínimo, si se quiere encontrar un máximo se puede hacer el mismo algoritmo $x  = x - \alpha \nabla f(x)$.

# Algoritmo de Newton-Raphson

Trata de encontrar las raíces de la ecuación $f'(x) = 0$, siempre converge para una función polinomial.

## Desventajas
- La convergencia es sensible al valor inicial.
- La convergencia al óptimo se vuelve lenta cuando el valor del gradiente es cercano a cero.
- Tiene que existir la segund derivada.

## Código

``` python
"""Metodo de Newton Raphson."""
import math
x0 = 2  # Aproximacion inicial
x1 = 0  # Solucion
n = 100  # Número de iteraciones
t = 0.001  # Tolerancia



def funcion(x):
    """La funcion original."""
    return (-x**2+2*x+1)


def derivada(x):
    """La derivada."""
    return (-2*x+2)


for i in range(1, n):
    y = funcion(x0)
    yPrima = derivada(x0)

    x1 = x0 - y/yPrima

    if abs(x1-x0) <= t:
       break

    x0 = x1

print(x1)
```


# Algoritmo de la secante

``` python
def secante(a, b, c, delta_x, flag=0):
	while flag == 1:
	alpha = (a+b)/2 
	if f_prime(a)*f_prime(alpha) < 0:
		b = a
		flag = 1 # zero is bracketed
	else:
		a = alpha
	if flag == 1:
		alpha = (x2 - f_prime(x2))/(f_prime(x2)-f_prime(x1))/(x2-x1)
		if f(alpha) > 0:
			b = alpha
			a = alpha 
	else:
	
```

# Algoritmo de ajuste polinomial cúbico

# Caso multidimensional
Considerar la siguiente variable:
$f(x_1, x_2) = x^2_1 + x^2_2 - 2x_1$

Su gradiente es el siguiente:

$\nabla f(x_1, x_2) =$

Necesitamos el hessiano o la matriz de las segundas derivadas que es:

...
## Algoritmo de Newton

``` python
def 
```