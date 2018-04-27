# Tarea1Sesion2

Explicar porqué los siguientes algoritmos tienen la complejidad correspondiente

Búsqueda binaria: logarítmica

El algoritmo de búsqueda binaria tiene complejidad logarítmica O(log n) porque empieza comparando el elemento central de la lista con el valor buscado, y en cada paso se va descartando la mitad de la lista hasta llegar al elemento deseado.
De esta forma, el espacio de soluciones se reduce a la mitad en cada iteración.

Por consiguiente, no es necesario recorrer toda la lista para encontrar el valor buscado, lo cual implicaría, en el peor de los casos, N operaciones, dando una complejidad lineal O(N).

Siempre se cumple que:

log (en base 2) de N < N

En el caso que N = 100, log (en base 2) 100 = 6.64

Esto significa que para encontrar cualquier elemento en una lista ordenada de 100 elementos, como máximo se requiere 7 operaciones.

Es indispensable que la lista está ordenada ascendentemente para que el algoritmo funcione.


	public Integer binarySearch(List<Integer> valueList, int needle, int min, int max) throws Exception {
        int midpoint = (max + min) / 2;
        if (valueList.size() > 0 && valueList.get(midpoint) == needle) {
            return midpoint;
        }
        if (min >= max) {
            return null;
        }
        if (valueList.get(midpoint) > needle) {
            return binarySearch(valueList, needle, min, midpoint - 1);
        }
        return binarySearch(valueList, needle, midpoint + 1, max);
    }
    
    


Serie Fibonacci: exponencial

El algoritmo de la serie Fibonacci es de complejidad exponencial, porque para calcular la secuencia para N elementos, se deben efectuar más de N operaciones. O sea, su eficiencia ni siquiera es lineal O(N)
De hecho, requiere aproximadamente 2 ^ N.
Esto se debe PRINCIPALMENTE a que se deben RECALCULAR los mismos elementos varias veces.

Por ejemplo:

Si N=6, o sea F(6), se requiere calcular F(5) y F(4).

Para calcular F(5), se debe calcular F(4) y F(3)
Para calcular F(4), se debe calcular F(3) y F(2)
Para calcular F(3), se debe calcular F(2) y F(1)
F(1) = 0 y F(2) = 1

Esto es solo para la primera rama F(5).

Ahora hay que hacer lo mismo para la primera rama F(4).

F(1) se debe calcular 3 veces
F(2) 5 veces
F(3) 3 veces
F(4) 2 veces
F(5) 1 vez

En total, son 14 operaciones.
Además, hay que sumar F(N-1) y F(N-2) como máximo 14 veces.
Suman 28 operaciones.
Además, la comparación del caso base cuando N es 1 o 2, como máximo 14 veces.
Suman 42 operaciones.
Lo mismo para N menor que 0.
Suman 56 operaciones.

En este caso, en el peor de los casos, se deben efectuar aproximadamente 2 ^ N = 2 ^ 6 = 64 operaciones para calcular el resultado.

Cómo se ve, la mayoría de cálculos requeridos para F(4) ya han sido calculados para F(5) pero tiene que realizarse de nuevo para F(4) ya que no han sido guardados en memoria. 
Esto es claramente ineficiente.



      //Complejidad Exponencial O(2^N)
	    public static long fibonacciExponencial(int n)  {
            if (n < 0) {
                throw new Exception("N can not be less than zero");
            }
            if (n <= 2) {
                return 1;
            }
            return fibonacciExponencial(n - 1) + fibonacciExponencial(n - 2);
	    }
