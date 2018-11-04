# Proyecto Base de Datos - Tabla Periodica

**TALLER DE DESARROLLO DE BASES DE DATOS**

**PROFESOR:** JUAN SEPÚLVEDA

**CODIGO:** CI205IECIRE

**SALA:** AL122

**Alumnos:**

* Carlos Hidalgo Vasquez - Seccion: **7**
* Samuel Barrera Bastidas - Seccion: **6**

## Archivo XML

XML de la Tabla Periodica : [AQUI](https://github.com/silverfox78/TablaPeriodica_XmlDTD/blob/master/tabla.xml)


## Preguntas a resolver

1. El nombre y número atómico de los elementos que pertenecen al Grupo 12 
2. El nombre y símbolo de los que tienen número atómico par 
3. El peso atómico y nombre de los que fueron descubiertos entre 1600 y 1750 
4. El % de los que tengan un una densidad entre 1,0 y 2,0 
5. El % de elementos que fueron descubiertos en la prehistoria 
6. El promedio de peso atómico de los elementos que pertenecen al grupo 4 

## Desarrollo

### Ejercicio N° 1

El nombre y número atómico de los elementos que pertenecen al Grupo 12 

***Consulta***
```
for $a in //elementos/elemento
where $a/grupo="12"
return ($a/nombre || " " || $a/numero)
```

***Respuesta***
```
Zinc 30
Cadmio 48
Mercurio 80
Copernicio 112
```



### Ejercicio N° 2

El nombre y símbolo de los que tienen número atómico par 

***Consulta***
```
for $a in //elementos/elemento
where $a/numero mod 2 = 0
return ($a/nombre || " - " || $a/simbolo)
```

***Respuesta***
```
Helio - He
Berilio - Be
Carbono - C
Oxígeno - O
Neón - Ne
Magnesio - Mg
Silicio - Si
Azufre - S
Argón - Ar
Calcio - Ca
Titanio - Ti
Cromo - Cr
Hierro - Fe
Níquel - Ni
Zinc - Zn
Germanio - Ge
Selenio - Se
Kriptón - Kr
Estroncio - Sr
Zirconio - Zr
Molibdeno - Mo
Rutenio - Ru
Paladio - Pd
Cadmio - Cd
Estaño - Sn
Teluro - Te
Xenón - Xe
Bario - Ba
Cerio - Ce
Neodimio - Nd
Samario - Sm
Gadolinio - Gd
Disprosio - Dy
Erbio - Er
Iterbio - Yb
Hafnio - Hf
Wolframio - W
Osmio - Os
Platino - Pt
Mercurio - Hg
Plomo - Pb
Polonio - Po
Radón - Rn
Radio - Ra
Torio - Th
Uranio - U
Plutonio - Pu
Curio - Cm
Californio - Cf
Fermio - Fm
Nobelio - No
Rutherfordio - Rf
Seaborgio - Sg
Hassio - Hs
Darmstadtio - Ds
Copernicio - Cn
Flerovio - Fl
Livermorio - Lv
Oganesón - Og
```

### Ejercicio N° 3

El peso atómico y nombre de los que fueron descubiertos entre 1600 y 1750 

***Consulta***
```
for $a in //elementos/elemento
where $a/descubrimiento >= 1680
and $a/descubrimiento <= 1750
return ($a/peso || " - " || $a/nombre)
```

***Respuesta***
```
58.933200(9) - Cobalto
195.084(9) - Platino
```


### Ejercicio N° 4

El % de los que tengan un una densidad entre 1,0 y 2,0 

***Consulta***
```
count(for $a in //elementos/elemento
where $a/densidad >= 1
and $a/densidad <= 2
return $a) * 100 div count(//elementos/elemento)
```

***Respuesta***
```
9.243697478991596639
```


### Ejercicio N° 5

El % de elementos que fueron descubiertos en la prehistoria 

***Consulta***
```
count(for $a in //elementos/elemento
where $a/descubrimiento = 0
return $a) * 100 div count(//elementos/elemento)
```

***Respuesta***
```
9.243697478991596639
```


### Ejercicio N° 6

El promedio de peso atómico de los elementos que pertenecen al grupo 4 

***Consulta***
```
sum(for $a in //elementos/elemento
where $a/grupo = 4
return $a/peso)
div
count(for $a in //elementos/elemento
where $a/grupo = 4
return $a/peso)
```

***Respuesta***
```
157.4371616666667
```