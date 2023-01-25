---
{"dg-publish":true,"permalink":"/anteckningar/vue-build-in-directives/"}
---

## v-bind
**v-bind** - Attributinterpolering (går att förkorta **v-bind:src** till **:src**)
Oftast på strängar, men class och style kan ta objekt eller arrayer.
```js
Vue.createApp({
	data() {
	    return { 
		    imageSrc: "logo.png"
		}
	  }
}).mount("#app")
```

```html
<div>
	<img alt="" v-bind:src"imageSrc" />
	// Eller
	<img alt="" :src"imageSrc" />	
</div>
```

För att ändra typ av lista dynamiskt genom *typeOfList*-variabeln:
```js
Vue.createApp({
	data() {
	    return { 
		    typeOfList: "A"
		}
	  }
}).mount("#app")
```

```html
<ol :type="typeOfList">
	<li>ett</li>
	<li>två</li>
	<li>tre</li>
</ol>
```

För att lägga till klassen *error* om *b* är sant så kan man skriva
```js
Vue.createApp({
	data() {
	    return { 
		    b: true
		}
	  }
}).mount("#app")
```
```html
<div :class="{ error: b }"> </div>
```

## v-if och v-for
För att kunna skriva if-satser i Vue så kan vi använda oss av *v-if*, som precis som en vanlig if-sats har else, och else if och till skillnad från *v-show* så renderar den inte alls elementet om if-satsen är falsk. V-show renderar däremot alltid innehållet och är alltså mer krävande men bättre om man ofta ska toggla innehåll flera gånger.
```html
<div v-if="!error"></div>
<script>
	Vue.createApp({
		data() {
		    return { 
			    error: true
			}
		  }
	}).mount("#app")
</script>
```

## v-on / @
```js
Vue.createApp({
	data() {
	    return { 
		    message: 'Hello World!',
		}
	  },
	  methods: {
		  onClick() {
			  console.log(this.message)
		  }
	  }
}).mount("#app")
```

```html
<body>
	<div id="app">
		<input type:"button" :value="message" />
		<button @click="onClick">
			Klicka här
		</button>
	</div>

</body>
```