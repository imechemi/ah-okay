## Spread and Rest operator

ES6 provides a new operator having syntax `...` used for spreading and collecting. This can be used on Arrays and Objects.

## In function as array spread

```js
const addItems = (...items) => { } 

addItems(1, 2, 3, 4)
```

## To concatenate to array

```js
const items = [3, 5, 6]
const newItems = [1, ...items, 7]
```

## To collect items from array

```js
const [first, ...restOfItems] = [1, 4, 6, 7]
```

## To concatenate or override object property or merge.

```js
const part1 = {name: 'chemi', age: 55}
const part2 = {love: 'animals', age: 32}

const person = { ...part1, ...part2 }
```

## To collection items from object

```js
const { name, ...restOfProperties } = { name: "chemi", age: 32, love: "animals" }
```
