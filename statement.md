# Méthdode d'Archimede 

This Python template lets you get started quickly with a simple one-page playground.

```python runnable
from math import sin,tan,pi

# Calcule le demi périmetre des polygones inscrits et circonconscrits
# n est le nombre de côtés
def archimedeSimple(n):
    return n*sin(pi/n),n*tan(pi/n)

print(archimedeSimple(6))

from math import sqrt

# Calcule le demi périmetre des polygones inscrits et circonconscrits
# en partant du carré
# Le nombre de côtés est 4 * 2**n

def archimede(n):
    a = 2*sqrt(2)
    b = 4
    for i in range(n):
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
    return a,b

print(archimede(10))


# Calcule le demi périmetre des polygones inscrits et circonconscrits
# en partant de l'hexagone
# Le nombre de côtés est 6 * 2**n

def archimede6(n):
    a = 3
    b = 2*sqrt(3)
    for i in range(n):
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
    return a,b

print(archimede6(10))



# Calcule le demi périmetre des polygones inscrits et circonconscrits
# en partant de l'hexagone
# Epsilon est la prècision souhaitée

def archimedePrecision(epsilon=10e-16):
    a = 3
    b = 2*sqrt(3)
    n = 6
    while b-a>epsilon:
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
        n *= 2
    return a,b,n

print(archimedePrecision(10e-12))

# Calcule l'arcsinus d'un angle par la méthode d'archimede
# Epsilon est la prècision souhaitée


def arcsinus(x,epsilon=10e-16):
    a = x
    b = x/sqrt(1-x*x)
    n = 1
    while b-a>epsilon:
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
        n *= 2
    return a

a =arcsinus(sin(.4))
print(a)


def sinus(x,n=24):
    a = x/2**n   
    for i in range(n):
        a = 2*a*sqrt(1-a*a)
        #print(i,a)
    return a

print(sinus(pi/3),sin(pi/3))
```

# Advanced usage

If you want a more complex example (external libraries, viewers...), use the [Advanced Python template](https://tech.io/select-repo/429)
