---
{"dg-publish":true,"permalink":"/anteckningar/array-metoder/"}
---

# Kurs: [[Anteckningar/JavaScript introduktion\|JavaScript introduktion]]
# Föreläsning x om Array metoder
---
## Array metoder
En array är en samling värden (som kan vara av olika typer - alltså en array kan innehålla flera olika typer i JavaScript)
Man skapar en array med 
```js
let arr = [1, "hej", {a: 2}]
```
För att lägga till värden
```js
arr = []
arr.push(a)
arr.unshift(b) // [b, a]
```
För att ta bort värden
```js
arr = [a, b, c]
arr.pop() // c
arr.shift() // a
```

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



#### Slå ihop arrayer
```js
var x = [1, 2, 3]
var y = [4, 5]
var z = [0].concat(x, y, [6]) // Gammalt sätt
console.log(z)
var z1 = [0, ...x, ...y, 6] // Med spread operator
console.log(z1)
```


</div></div>

Också användbart att kunna splice (tänker för ex. rekursiva funktioner)
```js
let arr = [1, 2, 3]
let arr2 = arr.splice(1) // [2, 3]
```


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



#### Snyggt sätt för att kapa bort två första värdena från en array
```js
function foo( x, y, ...args ) {
	return args
}
let a = [0, 1, 2]
let b = [3, 4, 5]
console.log(foo( ...a, ...b )) // [2, 3, 4, 5]
```


</div></div>

## Länkar
[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)