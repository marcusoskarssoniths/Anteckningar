---
{"dg-publish":true,"permalink":"/anteckningar/java-script-objekt/"}
---

# Kurs: [[Anteckningar/JavaScript introduktion\|JavaScript introduktion]]
# Föreläsning x om JavaScript objekt
---
Precis som med arrayer kan objekt innehålla flera värden av olika typer.
```js
let obj = {
	a: "hej",
	b: "test",
	c: [
		1, 2, 3
	],
	d: {
		a: "hej igen",
		b: "test igen"
	}
}
```

Om värden hör ihop är det mer organiserat att lägga ihop dem i ett objekt. Alltså tydligare
```js
let product = {
	name: "Göteborgsjacka",
	price: 599,
	quantityInStock: 3
}
console.log(`${product.name} kostar ${product.price}kr.`)
```

## Object.keys
Går igenom alla objektets nycklar (alltså skapar en iterable av objektet tror jag - att man kan loopa över det)
```js
let options = {} // ett objekt med nyckel-värdepar som man kan bygga upp allteftersom användaren fyller i ett formulär till exempel.
function constructQueryStr() {
  let str = API_URL;
  Object.keys(options).forEach(function (key) {
    // Loopar genom options objektet och bygger strängen för att fetcha
    str += `&${key}=${options[key]}`;
  });
  return str;
}
let url = constructQueryStr()
fetch(url)  //osv.
```
## Object.values
Går igenom alla objektets värden (alltså skapar en iterable av objektet tror jag - att man kan loopa över det)

## Att jämföra två objekt
Det går inte att direkt jämföra två objekt. Inte ens två tomma objekt kommer vara lika med varandra.
En metod är att loopa igenom objekten och jämföra deras nycklar och värden.
- En stor skillnad med hur JavaScript kontrollerar equality för objekt är att den jämför minnesadresser istället för värden (som den gör för primitiva typer ex. strängar).
