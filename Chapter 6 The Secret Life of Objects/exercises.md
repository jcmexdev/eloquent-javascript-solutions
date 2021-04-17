# Un tipo vector

Escribe una clase Vec que represente un vector en un espacio de dos dimensiones. Toma los parámetros (numericos) x y y, que debería guardar como propiedades del mismo nombre.

Dale al prototipo de Vector dos métodos, mas y menos, los cuales toman otro vector como parámetro y retornan un nuevo vector que tiene la suma o diferencia de los valores x y y de los dos vectores (this y el parámetro).

Agrega una propiedad getter llamada longitud al prototipo que calcule la longitud del vector—es decir, la distancia del punto (x, y) desde el origen (0, 0).

# Conjuntos

El entorno de JavaScript estándar proporciona otra estructura de datos llamada Set (“Conjunto”). Al igual que una instancia de Map, un conjunto contiene una colección de valores. Pero a diferencia de Map, este no asocia valores con otros—este solo rastrea qué valores son parte del conjunto. Un valor solo puede ser parte de un conjunto una vez—agregarlo de nuevo no tiene ningún efecto.

Escribe una clase llamada Conjunto. Como Set, debe tener los métodos add (“añadir”), delete (“eliminar”), y has (“tiene”). Su constructor crea un conjunto vacío, añadir agrega un valor al conjunto (pero solo si no es ya un miembro), eliminar elimina su argumento del conjunto (si era un miembro) y tiene retorna un valor booleano que indica si su argumento es un miembro del conjunto.

Usa el operador ===, o algo equivalente como indexOf, para determinar si dos valores son iguales.

Proporcionale a la clase un método estático desde que tome un objeto iterable como argumento y cree un grupo que contenga todos los valores producidos al iterar sobre el.

# Conjuntos Iterables

Haz iterable la clase Conjunto del ejercicio anterior. Puedes remitirte a la sección acerca de la interfaz del iterador anteriormente en el capítulo si ya no recuerdas muy bien la forma exacta de la interfaz.

Si usaste un array para representar a los miembros del conjunto, no solo retornes el iterador creado llamando al método Symbol.iterator en el array. Eso funcionaría, pero frustra el propósito de este ejercicio.

Está bien si tu iterador se comporta de manera extraña cuando el conjunto es modificado durante la iteración.

# Tomando un método prestado

Anteriormente en el capítulo mencioné que el metodo hasOwnProperty de un objeto puede usarse como una alternativa más robusta al operador in cuando quieras ignorar las propiedades del prototipo. Pero, ¿y si tu mapa necesita incluir la palabra "hasOwnProperty"? Ya no podrás llamar a ese método ya que la propiedad del objeto oculta el valor del método.

¿Puedes pensar en una forma de llamar hasOwnProperty en un objeto que tiene una propia propiedad con ese nombre?