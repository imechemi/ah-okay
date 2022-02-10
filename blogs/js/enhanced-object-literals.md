# Enhanced object literals

ES6 provides three ways to enhance objects. They are:

1. Property value shorthands
2. Method shorthands
3. Computed property names


```js
const propertyName = 'name'
const properyOrigin = 'ORIGIN'
const color = 'yellow'

const mango = {
  [propertyName]: 'Mango',
  color,
  sayHello: () => 'I am Mango',
  [properyOrigin.toLowerCase()]:  'India'
}

console.log(mango)


// Output
{
  name: 'Mango',
  color: 'yellow',
  sayHello: [Function: sayHello],
  origin: 'India'
}
```