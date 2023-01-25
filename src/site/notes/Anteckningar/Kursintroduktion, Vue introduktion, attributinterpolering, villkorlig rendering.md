---
{"dg-publish":true,"permalink":"/anteckningar/kursintroduktion-vue-introduktion-attributinterpolering-villkorlig-rendering/"}
---

# Kurs: [[Inkorg/Javascript med ramverk\|Javascript med ramverk]]
# Föreläsning 1 om Kursintroduktion, Vue introduktion, attributinterpolering, villkorlig rendering [[2023-01-12\|2023-01-12]]
---

## Kursintroduktion
### Vue.js
Vue är ett JavaScript-ramverk (andra exempel är React och Angular). Vanligt är att Vue används för mindre projekt medan Angular för större. React är något mellanting. 

I början av kursen kommer vi att importera Vue i script-taggen för att senare under kursen använda oss av Node och installera Vue. För att se till att vår webbsida kör Vue så skriver vi: 
```js
Vue.createApp({}).mount("#app")
```

Man kan skapa ett gäng variabler
```js
Vue.createApp({
	data() {
	    return { 
		    message: 'Hello World!',
		    one: 1,
		     two: null,
		     three: false,
		     four: undefined
		     five: [],
		     six: {}
		}
	  }
}).mount("#app")
```


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/anteckningar/vue-build-in-directives/#v-bind" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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


</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/anteckningar/vue-build-in-directives/#v-if-och-v-for" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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


</div></div>
