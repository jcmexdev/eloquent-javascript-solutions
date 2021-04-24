# Ciclo de un triángulo

Escriba un ciclo que haga siete llamadas a console.log para generar el siguiente triángulo:

```js
let triangleStr = ''
for (let i = 0; i < 7 ; i++) {
  triangleStr += '#'
  console.log(triangleStr)
}
```

output

```bash
#
##
###
####
#####
######
#######
```

# FizzBuzz

Escribe un programa que use console.log para imprimir todos los números de 1 a 100, con dos excepciones. Para números divisibles por 3, imprime "Fizz" en lugar del número, y para los números divisibles por 5 (y no 3), imprime "Buzz" en su lugar.

Cuando tengas eso funcionando, modifica tu programa para imprimir "FizzBuzz", para números que sean divisibles entre 3 y 5 (y aún imprimir "Fizz" o "Buzz" para números divisibles por solo uno de ellos).

```js
for (let i=1 ; i <= 100 ; i++) {
  let stdout = ""
  if (i % 3 === 0) {
    stdout += 'Fizz'
  }
  if (i % 5 === 0) {
    stdout += 'Buzz'
  }

  stdout ? console.log(stdout) : console.log(i)
}
```

output

```bash
1
2
Fizz
4
Buzz
Fizz
.
.
.
94
Buzz
Fizz
97
98
Fizz
Buzz
```

# Tablero de ajedrez

Escribe un programa que cree un string que represente una cuadrícula de 8 × 8, usando caracteres de nueva línea para separar las líneas. En cada posición de la cuadrícula hay un espacio o un carácter "#". Los caracteres deberían de formar un tablero de ajedrez.

Cuando tengas un programa que genere este patrón, define una vinculación tamaño = 8 y cambia el programa para que funcione con cualquier tamaño, dando como salida una cuadrícula con el alto y ancho dados.

```js
hashtagIsEven = false;
boardString = '';
size = 8
for (let i = 0 , len = size * size; i < len ; i++) {
  boardString += !(i % 2) === hashtagIsEven ? '#' : ' ';
  if (!(i % size)) {
    hashtagIsEven = !hashtagIsEven;
    boardString += '\n';
  }
}
console.log(boardString)
```

output

```bash
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
```