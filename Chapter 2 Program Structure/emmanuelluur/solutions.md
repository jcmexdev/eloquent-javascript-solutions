```javascript

/* Pyramid*/

const pyramid = (size) => {
  let symbol = '#';
  let cadena = '';
  for (let i = 0; i < size; i++) {
    console.log((cadena += symbol));
  }
};



```

```javascript
const FizzBuzz = (init, limit) => {
  for (init; init <= limit; init++) {
    if (init % 3 === 0 && init % 5 === 0) {
      console.log('FizzBuzz');
    } else if (init % 3 === 0) {
      console.log('Fizz');
    } else if (init % 5 === 0) {
      console.log('Buzz');
    } else {
      console.log(init);
    }
  }
};

```