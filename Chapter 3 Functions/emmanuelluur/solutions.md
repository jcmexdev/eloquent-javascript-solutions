### Mínimo
```javascript

const Min = (num_1, num_2) => (num_2 < num_2) ? num_1: num_2;

console.log(Min(0,10));
// →  0
console.log(Min(0, -10));
// → -10 
```

### Recursión

```javascript

function isEven(num) {
    if (num < 0) {
        return isEven(-num);
    } else if(num === 0) {
        return true;
    } else if(num === 1) {
        return false;
    } else {
        return isEven(num - 2)
    }
}

console.log(isEven(50));
// → true
console.log(isEven(75));
// → false
console.log(isEven(-1));
// → false
```

### Conteo de Frijoles

```javascript

function countChar(cadena, letra) {
    let longitud = cadena.length;
    let total = 0;
    for(let i = 0; i <= longitud; i++){
        if(cadena[i] === letra) total+=1;
    }
    return total;
}

function countFs(cadena){
    return countChar(cadena, "F");
}

console.log(countFs("FFC"));
// → 2
console.log(countChar("kakkerlak","k"));
// → 4
```