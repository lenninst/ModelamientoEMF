# De este es el resultado denerado en archivo ini.py
```py

from .Metamodelo import getEClassifier, eClassifiers
from .Metamodelo import name, nsURI, nsPrefix, eClass
from .Metamodelo import Paquete, Clase, Operaciones, Atributos, Parametros, DataType, Asociacion, ClaseAbstracta, Interface, Referencia, Implementacion, Herencia, Agregacion


from . import Metamodelo

__all__ = ['Paquete', 'Clase', 'Operaciones', 'Atributos', 'Parametros', 'DataType', 'Asociacion',
           'ClaseAbstracta', 'Interface', 'Referencia', 'Implementacion', 'Herencia', 'Agregacion']

eSubpackages = []
eSuperPackage = None
Metamodelo.eSubpackages = eSubpackages
Metamodelo.eSuperPackage = eSuperPackage

Paquete.claseabstracta.eType = ClaseAbstracta
Clase.operaciones.eType = Operaciones
Operaciones.datatype.eType = DataType
Atributos.datatype.eType = DataType
Parametros.datatype.eType = DataType
ClaseAbstracta.atributos.eType = Atributos
ClaseAbstracta.operaciones.eType = Operaciones
Interface.operaciones.eType = Operaciones
Paquete.clase.eType = Clase
Paquete.interface.eType = Interface
Clase.asociacion.eType = Asociacion
Clase.agregacion.eType = Agregacion
Clase.herencia.eType = Herencia
Clase.implementacion.eType = Implementacion
Clase.paquete.eType = Paquete
Clase.paquete.eOpposite = Paquete.clase
Clase.atributos.eType = Atributos
Atributos.clase.eType = Clase
Atributos.clase.eOpposite = Clase.atributos
Asociacion.clase.eType = Clase
Asociacion.clase.eOpposite = Clase.asociacion
Interface.paquete.eType = Paquete
Interface.paquete.eOpposite = Paquete.interface
Implementacion.clase.eType = Clase
Implementacion.clase.eOpposite = Clase.implementacion
Herencia.clase.eType = Clase
Herencia.clase.eOpposite = Clase.herencia
Agregacion.clase.eType = Clase
Agregacion.clase.eOpposite = Clase.agregacion

otherClassifiers = []

for classif in otherClassifiers:
    eClassifiers[classif.name] = classif
    classif.ePackage = eClass

for classif in eClassifiers.values():
    eClass.eClassifiers.append(classif.eClass)

for subpack in eSubpackages:
    eClass.eSubpackages.append(subpack.eClass)

```
