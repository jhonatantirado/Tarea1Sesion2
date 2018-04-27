# Tarea1Sesion2

Explicar porqué los siguientes algoritmos tienen la complejidad correspondiente

Busqueda binaria: logarítmica

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
