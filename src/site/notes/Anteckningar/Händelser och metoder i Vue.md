---
{"dg-publish":true,"permalink":"/anteckningar/haendelser-och-metoder-i-vue/"}
---

# Kurs: [[Inkorg/Javascript med ramverk\|Javascript med ramverk]]
# Föreläsning 2 om Händelser och metoder i Vue [[2023-01-16\|2023-01-16]]
---

Istället för addEventListener som vi kunde använda oss förut när vi körde vanliga JavaScript så kan vi i Vue använda oss av `v-on:click="onClick"`

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/anteckningar/vue-build-in-directives/#v-on" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



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

</div></div>


## V-model, computed, watch
V-model skapar en koppling mellan formulärkomponenter och data-värden.

```js
Vue.createApp({
	data() {
	    return { 
		    name: 'Jane Doe',
		}
	  }
}).mount("#app")
```

```html
<input v-model="name"/>
<p>{{ name }}</p>
```

Formulär
```html
<input v-model="name"/>
<input type="checkbox" v-model="isAdmin" />
```
```js
Vue.createApp({
	data() {
	    return { 
		    message: 'Hello World!',
		    isAdmin: true
		}
	  }
}).mount("#app")
```

class-binding
```html
<div :class="[computedValueOne, computedValueTwo, 'normal-class']">
</div>
```
