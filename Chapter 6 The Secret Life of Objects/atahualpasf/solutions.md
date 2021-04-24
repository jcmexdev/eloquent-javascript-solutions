# Un tipo vector

Escribe una clase Vec que represente un vector en un espacio de dos dimensiones. Toma los parámetros (numericos) x y y, que debería guardar como propiedades del mismo nombre.

Dale al prototipo de Vector dos métodos, mas y menos, los cuales toman otro vector como parámetro y retornan un nuevo vector que tiene la suma o diferencia de los valores x y y de los dos vectores (this y el parámetro).

Agrega una propiedad getter llamada longitud al prototipo que calcule la longitud del vector—es decir, la distancia del punto (x, y) desde el origen (0, 0).

```js
class Vector {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  mas(vector) {
    return new Vector(this.x + vector.x, this.y + vector.y);
  }
  
  menos(vector) {
    return new Vector(this.x - vector.x, this.y - vector.y);
  }

  get longitud() {
    return Math.sqrt(Math.pow(this.x, 2) + Math.pow(this.y, 2));
  }
}

console.log(new Vector(1, 2).mas(new Vector(2, 3)));
// → Vector{x: 3, y: 5}
console.log(new Vector(1, 2).menos(new Vector(2, 3)));
// → Vector{x: -1, y: -1}
console.log(new Vector(3, 4).longitud);
// → 5
```

output

```bash
Vector { x: 3, y: 5 }
Vector { x: -1, y: -1 }
5
```

# Conjuntos

El entorno de JavaScript estándar proporciona otra estructura de datos llamada Set (“Conjunto”). Al igual que una instancia de Map, un conjunto contiene una colección de valores. Pero a diferencia de Map, este no asocia valores con otros—este solo rastrea qué valores son parte del conjunto. Un valor solo puede ser parte de un conjunto una vez—agregarlo de nuevo no tiene ningún efecto.

Escribe una clase llamada Conjunto. Como Set, debe tener los métodos add (“añadir”), delete (“eliminar”), y has (“tiene”). Su constructor crea un conjunto vacío, añadir agrega un valor al conjunto (pero solo si no es ya un miembro), eliminar elimina su argumento del conjunto (si era un miembro) y tiene retorna un valor booleano que indica si su argumento es un miembro del conjunto.

Usa el operador ===, o algo equivalente como indexOf, para determinar si dos valores son iguales.

Proporcionale a la clase un método estático desde que tome un objeto iterable como argumento y cree un grupo que contenga todos los valores producidos al iterar sobre el.

```js
class Conjunto {
  constructor() {
    this._valores = []
  }

  añadir(valor) {
    !this.tiene(valor) && this._valores.push(valor)
  }

  eliminar(valor) {
    let index = this._valores.indexOf(valor)
    index !== -1 && this._valores.splice(index, 1);
  }

  tiene(valor) {
    return this._valores.includes(valor)
  }

  static desde(iterable) {
    let conjunto = new Conjunto();
    for (let valor of iterable) {
      conjunto.añadir(valor)
    }

    return conjunto
  }
}

let conjunto = Conjunto.desde([10, 20]);
console.log(conjunto.tiene(10));
// → true
console.log(conjunto.tiene(30));
// → false
conjunto.añadir(10);
conjunto.eliminar(10);
console.log(conjunto.tiene(10));
// → false
```

output

```bash
true
false
false
```

# Conjuntos Iterables

Haz iterable la clase Conjunto del ejercicio anterior. Puedes remitirte a la sección acerca de la interfaz del iterador anteriormente en el capítulo si ya no recuerdas muy bien la forma exacta de la interfaz.

Si usaste un array para representar a los miembros del conjunto, no solo retornes el iterador creado llamando al método Symbol.iterator en el array. Eso funcionaría, pero frustra el propósito de este ejercicio.

Está bien si tu iterador se comporta de manera extraña cuando el conjunto es modificado durante la iteración.

```js
class Conjunto {
  constructor() {
    this._valores = []
  }

  añadir(valor) {
    !this.tiene(valor) && this._valores.push(valor)
  }

  eliminar(valor) {
    let index = this._valores.indexOf(valor)
    index !== -1 && this._valores.splice(index, 1);
  }

  tiene(valor) {
    return this._valores.includes(valor)
  }

  static desde(iterable) {
    let conjunto = new Conjunto();
    for (let valor of iterable) {
      conjunto.añadir(valor)
    }

    return conjunto
  }
}

class IteradorConjunto {
  constructor(conjunto) {
    this.contador = 0;
    this.conjunto = conjunto;
  }

  next() {
    if (this.contador === this.conjunto._valores.length) return { done: true }

    let value = this.conjunto._valores[this.contador]
    this.contador++
    return {value, done: false}
  }
}

Conjunto.prototype[Symbol.iterator] = function() {
  return new IteradorConjunto(this)
}

for (let valor of Conjunto.desde(["a", "b", "c"])) {
  console.log(valor);
}
// → a
// → b
// → c
```

output

```bash
a
b
c
```

# Tomando un método prestado

Anteriormente en el capítulo mencioné que el metodo hasOwnProperty de un objeto puede usarse como una alternativa más robusta al operador in cuando quieras ignorar las propiedades del prototipo. Pero, ¿y si tu mapa necesita incluir la palabra "hasOwnProperty"? Ya no podrás llamar a ese método ya que la propiedad del objeto oculta el valor del método.

¿Puedes pensar en una forma de llamar hasOwnProperty en un objeto que tiene una propia propiedad con ese nombre?

```js
let mapa = {uno: true, dos: true, hasOwnProperty: true};

// Arregla esta llamada
console.log(Object.prototype.hasOwnProperty.call(mapa, "uno"));
// → true
```

output

```bash
true
```