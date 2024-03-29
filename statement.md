# Méthode d'Archimede 

Ces fonctions en python donnent des approximations du nombre pi par la méthde d'archimede

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

def archimede4(n):
    a = 2*sqrt(2)
    b = 4
    for i in range(n):
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
    return a,b

print(archimede4(10))


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

def archimedePrecision(epsilon=1e-12):
    a = 3
    b = 2*sqrt(3)
    n = 6
    while b-a>epsilon:
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
        n *= 2
    return a,b,n

print(archimedePrecision(1e-12))

# Calcule l'arcsinus d'un nombre par la méthode d'archimede
# Epsilon est la prècision souhaitée


def arcsinus(x,epsilon=1e-12):
    a = x
    b = x/sqrt(1-x*x)
    while b-a>epsilon:
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
    return a

a =arcsinus(sin(.4))
print(a)

# Calcule l'arctangente d'un nombre par la méthode d'archimede
# Epsilon est la prècision souhaitée

def arctangente(x,epsilon=1e-12):   
    a = x/sqrt(1+x*x)
    b = x
    while b-a>epsilon:
        b = (2*a*b)/(a+b)
        a = sqrt(b*a)
    return a

a =arctangente(tan(.5))
print(a)


def sinus(x,n=24):
    a = x/2**n   
    for i in range(n):
        a = 2*a*sqrt(1-a*a)
        #print(i,a)
    return a

print(sinus(pi/3),sin(pi/3))
```

# Améliorations possibles

Les fonctions arcsinus et sinus présentées ici sont limitées au premier quadrant. 
Il est possible de les étendre en utilisant les symétries de leur graphique.
