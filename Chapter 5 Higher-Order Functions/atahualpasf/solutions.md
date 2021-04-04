## Aplanamiento

Use el método reduce en combinación con el método concat para “aplanar” un array de arrays en un único array que tenga todos los elementos de los arrays
originales.

```js
const arrays = [[1, 2, 3], [4, 5], [6]];

const newArr = arrays.reduce((arr, currentValue) => {
  return arr.concat(currentValue)
})

console.log(newArr)
```

output

```bash
[1, 2, 3, 4, 5, 6]
```

## Tu propio ciclo

Escriba una función de orden superior llamada ciclo que proporcione algo así como una declaración de ciclo for. Esta toma un valor, una función de prueba, una función de actualización y un cuerpo de función. En cada iteración, primero ejecuta la función de prueba en el valor actual del ciclo y se detiene si esta retorna falso. Luego llama al cuerpo de función, dándole el valor actual. Y finalmente, llama a la función de actualización para crear un nuevo valor y comienza desde el principio.
Cuando definas la función, puedes usar un ciclo regular para hacer los ciclos reales.

```js
const loop = (value, conditionalFun, updateFunction, actionFunction) => {
  for(; conditionalFun(value) ; value = updateFunction(value)) actionFunction(value)
}

loop(3, n => n > 0, n => n - 1, console.log);
```

Output

```bash
3
2
1
```

## Cada

De forma análoga al método some, los arrays también tienen un método every (“cada”). Este retorna true cuando la función dada devuelve verdadero para cada elemento en el array. En cierto modo, some es una versión del operador
|| que actúa en arrays, y every es como el operador &&.

Implementa every como una función que tome un array y una función predicado como parámetros. Escribe dos versiones, una usando un ciclo y una usando el método some.

```js
const everyWithSome = (array, test) => !array.some(element => !test(element))

const everyWithLoop = (array, test) => {
  for (let element of array) {
    if (!test(element)) return false
  }
  return true
}

console.log('everyWithSome')
console.log(everyWithSome([1, 3, 5], n => n < 10));
console.log(everyWithSome([2, 4, 16], n => n < 10));
console.log(everyWithSome([], n => n < 10));
console.log('\neveryWithLoop')
console.log(everyWithLoop([1, 3, 5], n => n < 10));
console.log(everyWithLoop([2, 4, 16], n => n < 10));
console.log(everyWithLoop([], n => n < 10));
```

Output

```bash
everyWithSome
true
false
true

everyWithLoop
true
false
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

## Dirección de Escritura Dominante

Escriba una función que calcule la dirección de escritura dominante en un string de texto. Recuerde que cada objeto de código tiene una propiedad direction
que puede ser "ltr" (de izquierda a derecha), "rtl" (de derecha a izquierda), o "ttb" (arriba a abajo).
La dirección dominante es la dirección de la mayoría de los caracteres que tienen un código asociado a ellos. Las funciones codigoCaracter y contarPor definidas anteriormente en el capítulo probablemente serán útiles aquí.

```js
// Archivo de scripts del capítulo, se descarga de la página
require('./scripts');
// Archivo que contiene las funciones codigoCaracter y contarPor que se encontraban en la lectura del capítulo
const { codigoCaracter, contarPor } = require('./chapter-functions')

const dominantDirection = text => {
  let codesStatistics = contarPor(text, caracter => {
    let codigo = codigoCaracter(caracter.codePointAt(0))
    return codigo ? codigo.direction : undefined
  }).filter(({nombre}) => nombre !== undefined)

  let max = 0
  return codesStatistics.reduce((dominantDirectionValue, currentCode) => {
    if (max < currentCode.cuenta) {
      dominantDirectionValue = currentCode.nombre
      max = currentCode.cuenta
    }
    return dominantDirectionValue
  }, '')
}

console.log(dominantDirection('@#$%@#$%dsffs fsgsfg fd$#% /.;;\'kjlkjlkjlkj@# ~~'))
console.log(dominantDirection("Hello!"));
console.log(dominantDirection("Hey, مساء الخير"));
```

Output

```bash
ltr
ltr
rtl
```