# Mínimo

El capítulo anterior introdujo la función estándar Math.min que devuelve su
argumento más pequeño. Nosotros podemos construir algo como eso ahora.
Escribe una función min que tome dos argumentos y retorne su mínimo.

```js
const min = (a, b) => a < b ? a : b;

console.log(min(0, 10))
console.log(min(0, -10))
```

output

```bash
0
-10
```

# Recursión

Hemos visto que % (el operador de residuo) se puede usar para probar si un
número es par o impar usando % 2 para ver si es divisible entre dos. Aquí hay
otra manera de definir si un número entero positivo es par o impar:
• Zero es par.
• Uno es impar.
• Para cualquier otro número N, su paridad es la misma que N - 2.
Define una función recursiva esPar que corresponda a esta descripción. La
función debe aceptar un solo parámetro (un número entero, positivo) y devolver
un Booleano. Pruébalo con 50 y 75. Observa cómo se comporta con -1. Por qué? Puedes
pensar en una forma de arreglar esto?

```js
function esPar(number) {
  if (!Number.isInteger(number)) {
    return "Parámetro inválido, chequee que sea un número entero"
  }
  if (number < 0) {
    return "Parámetro inválido, chequee que sea un número positivo"
  }
  return number > 1
    ? esPar(number - 2)
    : number === 0
}
console.log(esPar(3 / 2));
console.log(esPar(-3 / 2));
console.log(esPar(4 / 2));
console.log(esPar(-4 / 2));
console.log(esPar(1));
console.log(esPar(-1));
console.log(esPar(50));
console.log(esPar(75));
console.log(esPar(-1));
```

output

```bash
Parámetro inválido, chequee que sea un número entero
Parámetro inválido, chequee que sea un número entero
true
Parámetro inválido, chequee que sea un número positivo
false
Parámetro inválido, chequee que sea un número positivo
true
false
Parámetro inválido, chequee que sea un número positivo
```

# Conteo de frijoles

Puedes obtener el N-ésimo carácter, o letra, de un string escribiendo "string"[
N]. El valor devuelto será un string que contiene solo un carácter (por ejemplo,
"f"). El primer carácter tiene posición cero, lo que hace que el último se
encuentre en la posición string.length - 1. En otras palabras, un string de
dos caracteres tiene una longitud de 2, y sus carácteres tendrán las posiciones
0 y 1.
Escribe una función contarFs que tome un string como su único argumento
y devuelva un número que indica cuántos caracteres “F” en mayúsculas haya
en el string.
Después, escribe una función llamada contarCaracteres que se comporte
como contarFs, excepto que toma un segundo argumento que indica el carácter
que debe ser contado (en lugar de contar solo caracteres “F” en mayúscula).
Reescribe contarFs para que haga uso de esta nueva función.

```js
const contarCaracteres = (string, char) => {
  let count = 0;
  for (index in string) {
    string[index] === char && count++
  }
  return count
}

const contarFs = (string) => {
  let count = 0;
  for (index in string) {
    string[index] === 'F' && count++
  }
  return count
}
console.log(contarFs("FFC"));
console.log(contarCaracteres("kakkerlak", "k"));
```

output

```bash
2
4
```