# Destructuring

This is a quirk and a cool little way to create variables out of arrays and objects. 

## Array

```js
const [name, age] = ['Sonam', 32]

console.log(`${name} is ${age} y.o`)
=> Sonam is 32 y.o
```

This can be used in function arguments to create multiple parameters. 

```js
const intro = (firstName, age) => {
  console.log(`My name is ${firstName}. I am ${age} y.o`)
}

intro(['Tenzin', 32])
```


## Object

You can directly create variable from the object's keys. 

```js
const user = {
  name: 'Tenzin', 
  age: 32
}
const { name, age } = user 

console.log(name)
=> 'Tenzin'
```


This can be used as function argument to create variables on demand. You can rename the extracted variable to a different name using `:` syntax. 
```js
const createEmployee = ({firstName: name = '--', age = '--'}) => {
  console.log(name)
  console.log(age)
  console.log('##########')
}

const c1 = {
  firstName: 'Tenzin'
}

const c2 = {
  age: 32
}

const c3 = {
  firstName: 'Lobsang',
  age: 30
}

createEmployee(c1)
createEmployee(c2)
createEmployee(c3)
```





