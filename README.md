1. De ejemplos de otras estructuras de datos no vistas en esta semana, y sus respectivos ejemplos de uso. 
Tabla Hash.- 

Es una estructura de datos que asocia llaves o claves con valores. La operación principal que soporta de manera eficiente es la búsqueda: permite el acceso a los elementos almacenados a partir de una clave generada. Funciona transformando la clave con una función hash en un hash (un número que identifica la posición  donde la tabla hash localiza el valor deseado).
Árbol 
Es una estructura de datos ampliamente usada que imita la estructura jerárquica de un árbol, con un valor en la raíz y subárboles con un nodo padre, representado como un conjunto de nodos enlazados.
Árbol-B
Es una estructura de datos de árbol que se encuentra comúnmente en las implementaciones de bases de datos y sistemas de archivos. Son árboles balanceados de búsqueda, pero cada nodo puede poseer más de dos hijos. Los árboles B mantienen los datos ordenados y las inserciones y eliminaciones se realizan en tiempo logarítmico amortizado.

2. Problema (Usar pilas) Dada un vector, imprima el Siguiente Gran Elemento (SGE) para cada elemento. El siguiente elemento mayor para un elemento x es el primer elemento mayor en el lado derecho de x en el conjunto. Elementos para los que no existe un elemento mayor, considere el siguiente elemento más grande como -1.
https://ideone.com/kz29xH
    class Pila:
        def __init__(self):
            self.items = []
        def empty(self):
            return self.items == []
        def push(self, item):
            self.items.append(item)
        def pop(self):
            return self.items.pop()
        def top(self):
            return self.items[-1]
        def size(self):
            return len(self.items)
    def SGE(pila):
        A = Pila()
        B = Pila()
        s = pila.size()
        for i in range(s):
            e = pila.pop()
            A.push(e)
        for i in range(s):
            e = A.pop()
            m = -1
            while(m < e and not(A.empty())):
                t = A.pop()
                if(t > e):
                    m = t
                B.push(t)
            print(e,"-",m)
            while(not(B.empty())):
                t = B.pop()
                A.push(t)
            pila.push(e)
    print("1er Ejemplo")
    P1 = Pila()
    P1.push(4)
    P1.push(5)
    P1.push(2)
    P1.push(25)
    SGE(P1)
    print("2do Ejemplo")
    P2 = Pila()
    P2.push(13)
    P2.push(7)
    P2.push(6)
    P2.push(12)
    SGE(P2)
