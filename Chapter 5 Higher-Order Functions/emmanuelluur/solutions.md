## Aplanamiento

```javascript

let arrays = [[1, 2, 3], [4, 5], [6]];

console.log(arrays.reduce((a, b) => a.concat(b), []));

```

## Tu propio ciclo

```javascript

function ciclo(inicio, prueba, actualiza, cuerpo) {
  /**
   *@ inicio es el valor donde iniciara el ciclo ej. i = n
   *@ prueba sera el la función inicial del ciclo ej. i < n
   *@ actualiza será la función que actualiza el valor ej. i++
   *@ cuerpo será la función de salida
   */
  for (let valor = inicio; prueba(valor); valor = actualiza(valor)) {
    cuerpo(valor);
  }
}


```

## Cada

```javascript

function cada(arreglo, funcion) {
  for (let elemento of arreglo) {
    if (!funcion(elemento)) {
      return false;
      break;
    }
  }
  return true;
}

function cada_v2(arreglo, funcion) {
  // devuelve true o false si se cumple la fn dada
  return !arreglo.some((elemento) => !funcion(elemento));
}


```
