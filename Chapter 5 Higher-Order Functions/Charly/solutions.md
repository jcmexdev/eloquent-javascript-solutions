## Aplanamiento

Use el método reduce en combinación con el método concat para “aplanar” un array de arrays en un único array que tenga todos los elementos de los arrays
originales.

```js
const arrays = [1, 2, 3], [4, 5], [6], [7,8,9];

const flattenArray = arrays.reduce((acum, current)=> acum.concat(current), []);

console.log(flattenArray)
```

output

```bash
[1, 2, 3, 4, 5,6, 7, 8, 9]
```

## Tu propio ciclo

Escriba una función de orden superior llamada ciclo que proporcione algo así como una declaración de ciclo for. Esta toma un valor, una función de prueba, una función de actualización y un cuerpo de función. En cada iteración, primero ejecuta la función de prueba en el valor actual del ciclo y se detiene si esta retorna falso. Luego llama al cuerpo de función, dándole el valor actual. Y finalmente, llama a la función de actualización para crear un nuevo valor y comienza desde el principio.
Cuando definas la función, puedes usar un ciclo regular para hacer los ciclos reales.

```js
const customFor = (initial, testCurrent, updateCurrent, callback) => {
  let current = initial;
  while (testCurrent(current)) {
    callback(current);
    current = updateCurrent(current);
  }
  console.log("Custom For has ended succesfully");
};

customFor(
  0,
  (curr) => curr <= 10,
  (curr) => (curr += 1),
  (curr) => console.log(`Valor actual ${curr}`)
);
```

Output

```bash
'Valor actual 0'
'Valor actual 1'
'Valor actual 2'
'Valor actual 3'
'Valor actual 4'
'Valor actual 5'
'Valor actual 6'
'Valor actual 7'
'Valor actual 8'
'Valor actual 9'
'Valor actual 10'
'Custom For has ended successfully'
```

## Cada

De forma análoga al método some, los arrays también tienen un método every (“cada”). Este retorna true cuando la función dada devuelve verdadero para cada elemento en el array. En cierto modo, some es una versión del operador
|| que actúa en arrays, y every es como el operador &&.

Implementa every como una función que tome un array y una función predicado como parámetros. Escribe dos versiones, una usando un ciclo y una usando el método some.

```js
const every = (array, testFunction) => {
  for (el of array) {
    if (testFunction(el) === false) return false;
  }
  return true;
};

every([1, 2, 3, 11], (el) => (el < 10 ? true : false));
```

Output

```bash
every([1,2,3,11], (el)=> el < 10 ? true : false)
false
every([1,2,3,11], (el)=> el < 12 ? true : false)
true
```

Now with some

```js
[1, 2, 3, 11].some((el) => el < 12);
//true
[(1, 2, 3, 11)].some((el) => el > 12);
//false
[(1, 2, 3, 11)].some((el) => el > 5);
//true;
```
