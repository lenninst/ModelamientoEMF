# ModelamientoEMF

La solucion se muestran  los archivos resultados y resultado2
En la carpeta ProyectoModelamiento.ipynb esta el código para generar creado en GoogleColab. 😏🔥
# ModelamientoEMF

###Resultados

```py
"""Definition of meta model 'Metamodelo'."""
from functools import partial
import pyecore.ecore as Ecore
from pyecore.ecore import *


name = 'Metamodelo'
nsURI = 'http://www.example.org/Metamodelo'
nsPrefix = 'Metamodelo'

eClass = EPackage(name=name, nsURI=nsURI, nsPrefix=nsPrefix)

eClassifiers = {}
getEClassifier = partial(Ecore.getEClassifier, searchspace=eClassifiers)


class Paquete(EObject, metaclass=MetaEClass):

    nombrePaquete = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    claseabstracta = EReference(ordered=True, unique=True,
                                containment=True, derived=False, upper=-1)
    clase = EReference(ordered=True, unique=True, containment=True, derived=False)
    interface = EReference(ordered=True, unique=True, containment=True, derived=False, upper=-1)

    def __init__(self, *, nombrePaquete=None, claseabstracta=None, clase=None, interface=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombrePaquete is not None:
            self.nombrePaquete = nombrePaquete

        if claseabstracta:
            self.claseabstracta.extend(claseabstracta)

        if clase is not None:
            self.clase = clase

        if interface:
            self.interface.extend(interface)


class Clase(EObject, metaclass=MetaEClass):

    nombreClase = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    operaciones = EReference(ordered=True, unique=True, containment=True, derived=False, upper=-1)
    asociacion = EReference(ordered=True, unique=True, containment=False, derived=False)
    agregacion = EReference(ordered=True, unique=True, containment=False, derived=False)
    herencia = EReference(ordered=True, unique=True, containment=False, derived=False)
    implementacion = EReference(ordered=True, unique=True, containment=False, derived=False)
    paquete = EReference(ordered=True, unique=True, containment=False, derived=False)
    atributos = EReference(ordered=True, unique=True, containment=True, derived=False)

    def __init__(self, *, nombreClase=None, operaciones=None, asociacion=None, agregacion=None, herencia=None, implementacion=None, paquete=None, atributos=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreClase is not None:
            self.nombreClase = nombreClase

        if operaciones:
            self.operaciones.extend(operaciones)

        if asociacion is not None:
            self.asociacion = asociacion

        if agregacion is not None:
            self.agregacion = agregacion

        if herencia is not None:
            self.herencia = herencia

        if implementacion is not None:
            self.implementacion = implementacion

        if paquete is not None:
            self.paquete = paquete

        if atributos is not None:
            self.atributos = atributos


class Operaciones(EObject, metaclass=MetaEClass):

    nombreOperacion = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    encapsulamiento = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    datatype = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, nombreOperacion=None, encapsulamiento=None, datatype=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreOperacion is not None:
            self.nombreOperacion = nombreOperacion

        if encapsulamiento is not None:
            self.encapsulamiento = encapsulamiento

        if datatype is not None:
            self.datatype = datatype


class Atributos(EObject, metaclass=MetaEClass):

    nombreAtributo = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    encapculamiento = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    datatype = EReference(ordered=True, unique=True, containment=False, derived=False)
    clase = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, nombreAtributo=None, encapculamiento=None, datatype=None, clase=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreAtributo is not None:
            self.nombreAtributo = nombreAtributo

        if encapculamiento is not None:
            self.encapculamiento = encapculamiento

        if datatype is not None:
            self.datatype = datatype

        if clase is not None:
            self.clase = clase


class Parametros(EObject, metaclass=MetaEClass):

    nombreParametro = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    datatype = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, nombreParametro=None, datatype=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreParametro is not None:
            self.nombreParametro = nombreParametro

        if datatype is not None:
            self.datatype = datatype


class DataType(EObject, metaclass=MetaEClass):

    nombreDataType = EAttribute(eType=EString, unique=True, derived=False, changeable=True)

    def __init__(self, *, nombreDataType=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreDataType is not None:
            self.nombreDataType = nombreDataType


@abstract
class ClaseAbstracta(EObject, metaclass=MetaEClass):

    nombreClaseAbstracta = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    atributos = EReference(ordered=True, unique=True, containment=True, derived=False, upper=-1)
    operaciones = EReference(ordered=True, unique=True, containment=True, derived=False, upper=-1)

    def __init__(self, *, nombreClaseAbstracta=None, atributos=None, operaciones=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreClaseAbstracta is not None:
            self.nombreClaseAbstracta = nombreClaseAbstracta

        if atributos:
            self.atributos.extend(atributos)

        if operaciones:
            self.operaciones.extend(operaciones)


@abstract
class Interface(EObject, metaclass=MetaEClass):

    nombreInterface = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    operaciones = EReference(ordered=True, unique=True, containment=True, derived=False, upper=-1)
    paquete = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, nombreInterface=None, operaciones=None, paquete=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreInterface is not None:
            self.nombreInterface = nombreInterface

        if operaciones:
            self.operaciones.extend(operaciones)

        if paquete is not None:
            self.paquete = paquete


class Referencia(EObject, metaclass=MetaEClass):

    nombreReferencia = EAttribute(eType=EString, unique=True, derived=False, changeable=True)
    multiplicidad = EAttribute(eType=EString, unique=True, derived=False, changeable=True)

    def __init__(self, *, nombreReferencia=None, multiplicidad=None):
        # if kwargs:
        #    raise AttributeError('unexpected arguments: {}'.format(kwargs))

        super().__init__()

        if nombreReferencia is not None:
            self.nombreReferencia = nombreReferencia

        if multiplicidad is not None:
            self.multiplicidad = multiplicidad


class Asociacion(Referencia):

    clase = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, clase=None, **kwargs):

        super().__init__(**kwargs)

        if clase is not None:
            self.clase = clase


class Implementacion(Referencia):

    clase = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, clase=None, **kwargs):

        super().__init__(**kwargs)

        if clase is not None:
            self.clase = clase


class Herencia(Referencia):

    clase = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, clase=None, **kwargs):

        super().__init__(**kwargs)

        if clase is not None:
            self.clase = clase


class Agregacion(Referencia):

    clase = EReference(ordered=True, unique=True, containment=False, derived=False)

    def __init__(self, *, clase=None, **kwargs):

        super().__init__(**kwargs)

        if clase is not None:
            self.clase = clase

``
