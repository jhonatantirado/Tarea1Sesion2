# Tarea1Sesion2

Explicar porqué los siguientes algoritmos tienen la complejidad correspondiente

Busqueda binaria: logaritmica

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
