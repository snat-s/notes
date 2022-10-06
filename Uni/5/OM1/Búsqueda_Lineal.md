# Búsqueda Lineal

## Idea básica (Actividad)

Se inicia en un intervalo $[a,b]$, y sucesivamente se reduce, hasta que el intervalo converja a un **mínimo/máximo** local.

```python
a = 0 
b = 5

ahat = 0  # el mejor intervalo
bhat = 0  # el mejor intervalo

paso = 0.4
fx = lambda x : x**4 - 20*x**3 + 0.1*x

def caminar(a, b):
    a += paso
    return [a, b]

# Espacio de busqueda es 0 a 20
while a < 20 and b < 20:
    if a < b: 
        res = caminar(a, b)
        a = res[0]
        b = res[1]
        if fx(res[0]) < fx(ahat) and fx(res[1]) < fx(bhat):
            ahat = res[0]
            bhat = res[1]
    else:
        res = caminar(b, a)
        a = res[1]
        b = res[0]
        if fx(res[1]) < fx(ahat) and fx(res[0]) < fx(bhat):
            ahat = res[1]
            bhat = res[0]

print("[",ahat, bhat,"]")
```

## Método de la sección dorada

Es una búsqueda binaria pero la diferencia es que usas la *razón áurea* en vez de la mitad. 
### Input
- $e$ := valor de error
- $r$ := razón dorada
- $a,b$ := valor inferior y superior, respectivamente

### Output
- $x*$ := solución óptima local

### Implementación

```python
def metodo_seccion_dorada(e, r, a, b):

	alpha1 = a*(1-r) + b*r
	alpha2 = a*r + b*(1-r)

	while abs(f(alpha1)-f(alpha2)) < r:
		if f(alpha1) > f(alpha2):
			b = alpha1
			alpha1 = alpha2
			alpha2 = a*r + b*(1-r)
		else:
			a = alpha2
			alpha2 = alpha1
			alpha1 = a*(1-r) + b*r
	return alpha1
```

# Método de los tres puntos
```python
def 
```
