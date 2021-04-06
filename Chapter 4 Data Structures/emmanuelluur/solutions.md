### Suma de Rango

```javascript

const rango = (inicial, final, step = 1) => {
  let arr = [];
  if (inicial > final) {
    for (let i = inicial; i >= final; i += step) {
      arr.push(i);
    }
  } else {
    for (let i = inicial; i <= final; i += step) {
      arr.push(i);
    }
  }
  return arr;
};

const sum = (arr = []) => {
  let long = arr.length;
  let total = 0;
  for (let i = 0; i < long; i++) {
    total += arr[i];
  }
  return total;
};

console.log(rango(1, 10));
// → [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
console.log(rango(5, 2, -1));
// → [5, 4, 3, 2]
console.log(sum(rango(1, 10)));
// → 55


```