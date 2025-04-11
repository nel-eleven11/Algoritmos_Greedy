# Ejercicio 5

![image](https://github.com/user-attachments/assets/795cc9ea-b1b2-4440-9dc1-aa766881d152)

---

## Algoritmo de Dijkstra

Figura 1: Algoritmo de Dijkstra

![image](https://github.com/user-attachments/assets/b2d52498-012c-4d66-a624-d6c7da7c792c) 

(Cormen et al., 2022)

### Explicación:

Dijkstra aplica una estrategia greedy: en cada paso elige el vértice no visitado con la distancia mínima conocida desde la fuente. Luego, actualiza (relaja) las distancias de sus vecinos si encuentra un camino más corto. Se basa en que los pesos son no negativos.

Inicialización:

A cada vértice v ∈ V se le asigna una distancia estimada v.d = ∞ excepto a la fuente s.d = 0. Se usa una cola de prioridad min-heap Q, ordenada por las distancias actuales v.d.

Procesamiento iterativo:

Mientras la cola no esté vacía:

- Extrae el nodo con menor distancia estimada u.
- Relaja cada vecino v de u: si ir de s -> u -> v es más corto, actualiza v.d y su predecesor.
- Si la distancia se actualiza, se usa DECREASE-KEY en el heap para reordenar.

Termina cuando se han procesado todos los vértices. Al finalizar, todos los v.d contienen la distancia más corta desde s a v.

### Análisis:

Tiempo:

Usando min-heap binario:

- Inicialización del heap: O(V)
- EXTRACT-MIN: O(log V), se hace V veces -> O(V log V)
- RELAX + DECREASE-KEY por cada arista: O(log V), total O(E log V)

Total: O((V + E) log V)

Usando Fibonacci Heap (más eficiente teóricamente):
- EXTRACT-MIN: O(log V)
- DECREASE-KEY: O(1)

Total: O(V log V + E)

Espacio:

Almacena:

- Distancias: O(V)
- Predecesores: O(V)
- Cola de prioridad: O(V)

Total: O(V)


## Algoritmo de Bellman-Ford

Figura 2: Algoritmo de Bellman-Ford

![image](https://github.com/user-attachments/assets/172b8cd2-4612-4711-84fc-2534629905be)

(Cormen et al., 2022)

### Explicación: 

Bellman-Ford aplica programación dinámica: intenta relajar todas las aristas del grafo repetidamente, hasta que ya no se puedan mejorar más los caminos. Admite pesos negativos y también puede detectar ciclos negativos.

Inicialización:

Igual que Dijkstra: v.d = ∞, excepto s.d = 0

Relajación iterativa (fase principal):

Se repite ∣V∣−1 veces:

Para cada arista (u, v) ∈ E, si v.d > u.d + w(u, v), se relaja.

Verificación de ciclo negativo:

Una pasada final por las aristas: si alguna aún se puede relajar, entonces hay un ciclo negativo -> el algoritmo retorna FALSE.

### Análisis:

Tiempo:

- Se relajan todas las E aristas durante V−1 iteraciones.
- La verificación final (1 pasada más): O(E)

Total: O(V * E)

Espacio:
Almacena:

- Distancias: O(V)
- Predecesores: O(V)

Total: O(V)


## ¿Cuál es mejor?

El algoritmo de Dijkstra es, sin duda, más eficiente en términos de tiempo cuando se trata de grafos cuyos pesos de aristas son no negativos. Su enfoque greedy le permite seleccionar de forma óptima el siguiente vértice con la menor distancia conocida desde la fuente, lo cual, combinado con una estructura eficiente como un min-heap, lleva a una complejidad de tiempo de O((V + E) logV). Esta eficiencia lo convierte en la elección preferida en contextos donde se requiere rapidez y donde los datos garantizan que no existirán aristas con pesos negativos, como ocurre, por ejemplo, en mapas de rutas físicas, redes logísticas, o sistemas de navegación GPS.

Por otro lado, el algoritmo de Bellman-Ford es más versátil y robusto, ya que puede manejar grafos con pesos negativos, e incluso detectar la presencia de ciclos negativos. Esto es esencial en aplicaciones donde las aristas representan penalizaciones, descuentos o deudas, como en ciertas aplicaciones financieras, sistemas de costos o redes con fluctuaciones de valor. A pesar de ser menos eficiente O(V * E), Bellman-Ford garantiza obtener la solución correcta en cualquier grafo dirigido ponderado, siempre y cuando no existan ciclos negativos alcanzables desde la fuente. En caso de que existan, el algoritmo incluso es capaz de advertirlo, lo cual es una funcionalidad que Dijkstra no posee.

Desde una perspectiva teórica, se puede decir que Dijkstra es mejor siempre que las condiciones del grafo lo permitan, ya que resuelve el mismo problema más rápido. Sin embargo, Bellman-Ford es más general, y en términos de aplicabilidad, resulta imprescindible en situaciones donde la naturaleza de los datos no puede garantizar que todos los pesos sean positivos. Por lo tanto, no se puede afirmar categóricamente que uno sea mejor que el otro en todos los casos; su rendimiento y utilidad dependen directamente de las propiedades del grafo de entrada.


---

# Bibliografía:

Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2022). Introduction to Algorithms, fourth edition. MIT Press.

