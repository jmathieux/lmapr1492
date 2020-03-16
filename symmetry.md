# Code 


```python
from pymatgen.ext.matproj import MPRester
import numpy as np
from pymatgen.core.operations import SymmOp
with MPRester("9pWDrcCtfsNndSHF") as m:
    structure = m.get_structure_by_material_id("mp-13694")
    
#coordonnées des atomes obtenues sur Jmol Crystal Symmetry Explorer
    point1 = np.array([0.67,0.33,0.33]) #Cu1 #6
    point2 = np.array([0.33,0.67,0.77]) #O2 #11
    point3 = np.array([1.0,0.0,0.5]) #Pr0 #19
    
#matrices de transformations
    miroir = SymmOp.from_xyz_string('-y,-x,z').rotation_matrix
    rotation = SymmOp.from_xyz_string('y,x,-z').rotation_matrix
    rotoinv = SymmOp.from_xyz_string('y-1/3,-x+y+1/3,-z+1/3').rotation_matrix
    
#applications des symétries et optention des nouvelles coordonnées  
    sym1 = SymmOp.from_xyz_string('-y,-x,z').operate(point1) #symetrie 8 mirror plane
    sym2 = SymmOp.from_xyz_string('y,x,-z').operate(point2) #rotation num 7
    sym3 = SymmOp.from_xyz_string('y-1/3,-x+y+1/3,-z+1/3').operate(point3) #roto-inversion num 16
  
```

# Résultats
## Première symétrie sur l'atome 1

La première symétrie est appliquée sur un atome de Cu. Cette symétrie est un plan miroir passant par la normale [0,0,0]. (ou un truc ainsi jsp si c'est utile)



```python
print('Type atome: Cu','\n')
print('Matrice transformation selon un plan miroir:','\n',miroir, '\n')
print('Coordonnées de atome 1 au départ:', point1, '\n')
print('Coordonnées de atome 1 après la symétrie:',sym1,'\n' )
```

    Type atome: Cu 
    
    Matrice transformation selon un plan miroir: 
     [[ 0. -1.  0.]
     [-1.  0.  0.]
     [ 0.  0.  1.]] 
    
    Coordonnées de atome 1 au départ: [0.67 0.33 0.33] 
    
    Coordonnées de atome 1 après la symétrie: [-0.33 -0.67  0.33] 
    


![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.43.02.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.43.02.png)

![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.45.13.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.45.13.png)

## Deuxième symétrie sur l'atome 2

La deuxième symétrie est appliquée sur un atome de O. Cette symétrie est une rotation (C2)


```python
print('Type atome: O','\n')
print('Matrice transformation selon une rotation:','\n',rotation, '\n')
print('Coordonnées de atome 2 au départ:', point2, '\n')
print('Coordonnées de atome 2 après la symétrie:',sym2,'\n' )
```

    Type atome: O 
    
    Matrice transformation selon une rotation: 
     [[ 0.  1.  0.]
     [ 1.  0.  0.]
     [ 0.  0. -1.]] 
    
    Coordonnées de atome 2 au départ: [0.33 0.67 0.77] 
    
    Coordonnées de atome 2 après la symétrie: [ 0.67  0.33 -0.77] 
    


![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.48.14.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.48.14.png)

![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.48.23.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.48.23.png)
![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.48.37.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.48.37.png)

## Troisème symétrie sur l'atome 3

La troisème symétrie est appliquée sur un atome Pr. Cette symétrie est une roto-inversion (3 barre)


```python
print('Type atome: Pr','\n')
print('Matrice transformation selon une roto-inversion:','\n',rotoinv, '\n')
print('Coordonnées de atome 3 au départ:', point3, '\n')
print('Coordonnées de atome 3 après la symétrie:',sym3,'\n' )
```

    Type atome: Pr 
    
    Matrice transformation selon une roto-inversion: 
     [[ 0.  1.  0.]
     [-1.  1.  0.]
     [ 0.  0. -1.]] 
    
    Coordonnées de atome 3 au départ: [1.  0.  0.5] 
    
    Coordonnées de atome 3 après la symétrie: [-0.33333333 -0.66666667 -0.16666667] 
    


![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.42.32.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.42.32.png)

![Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.41.57.png](attachment:Capture%20d%E2%80%99e%CC%81cran%202020-03-15%20a%CC%80%2021.41.57.png)


```python

```
