---
{"dg-publish":true,"permalink":"/anteckningar/java-script-funktioner/"}
---

# Kurs: [[Anteckningar/JavaScript introduktion\|JavaScript introduktion]]
# Föreläsning x om JavaScript funktioner
---
## Flera olika sätt att deklarera funktioner
```js
let fn = function() {}
let fn1 = () => {} // arrow function.
function fn2() {} // Antagligen att föredra då det gör det enklare att felsöka, då funktionens namn alltid kommer med i error. 
```
## När använda arrow-functions?
Antagligen väldigt sällan då de kan göra koden svårläst, speciellt då de har olika syntax beroende på om det är 0, 1 eller fler parametrar.
* En smidig grej
```js
class Person {
	constructor(name, age) {
		this.name = name
		this.age = age
	}
	say = () => {
		console.log(`Hej, ${this.name}!`)
	}
}
let p = new Person("Marcus", 30)
p.say()
```

Ser ju också smidigt ut
```js
fetch(url)
.then((res) => res.json) //osv
```

Antagligen är det bäst att skapa funktioner med function fn(),
dels så kan de kallas innan de deklareras (man kan alltså få bättre struktur på koden!) och dels har det (till skillnad från arrow-functions) ett, och endast ett, sätt att skriva dem på.

## Funktioner av högre ordningen
Går igenom metoderna, forEach, filter, find, map, reduce. De är på sätt och vis ett annat sätt att programmera på (vad vill man uppnå, istället för hur - mer funktionellt än imperativt).

Går ut på att funktioner behandlas på samma sätt som variabler och alltså kan skickas som argument till andra funktioner.

Hur fungerar de egentligen?
- map
```js
function map(arr, f) { 
	let newArr = []; 
	for (let i = 0; i < arr.length; i++) { 
		newArr = [...newArr, f(arr[i])]; 
	} 
	return newArr; 
}
```
- reduce
```js
function reduce(list, f, acc) { 
	if (list.length === 1) { 
		return f(acc, list[0]) 
	} 
	return reduce(list.slice(1), f, f(acc, list[0])) 
}
```
