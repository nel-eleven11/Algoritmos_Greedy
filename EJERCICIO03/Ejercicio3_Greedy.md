# En una matroide M = (S,I), donde S tiene n elementos, ¿qué puede asegurar sobre el tiempo de ejecución del algoritmo greedy correspondiente?

Donde S es un conjunto finito con n elementos y I es la colección de conjuntos independientes, el algoritmo greedy 
se puede usar para encontrar una base de peso máximo cuando a cada elemento de S se le asigna un peso.
Se puede asegurar lo siguiente:

1. Ordenamiento de los elementos: Los elementos de S se ordenan según su peso, este ordenamiento tiene una complejidad
de O(nlog(n)).
2. Verificación de independencia: Los elementos se recorren en orden y va agregando al conjunto solución aquellos que
mantienen la propiedad de independencia,teniendo una complejidad de O(n*t) donde t es el tiempo que toma verificar si
un conjunto sigue siendo independiente al agregarle un nueo elemento.

Combinando ambas complejidades anteriores tenemos una complejidad de O(nlog(n)+n*t). En muchas ocasiones tenemos que t
es O(1) o O(log(n)), esta es una aumción que se hace en base a que la matroide tiene estructura clara y bien representada
y las estructuras de datos son adecuadas. De esta forma el tiempo se puede reducir a O(nlog(n)). 
