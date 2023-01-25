---
{"dg-publish":true,"permalink":"/anteckningar/vue-lifecycle-methods/"}
---


Vi gick igenom `created` som körs varje gång en komponent skapas.
Det finns fler utöver `created` - ett exempel är `updated` som körs varje gång komponenten uppdateras (vilket kan vara smidigt!)

```js
app.component('test-komponent', {
	created() {
		console.log("skapad")
	},
	updated() {
		console.log("uppdaterad")
	}
})
```
