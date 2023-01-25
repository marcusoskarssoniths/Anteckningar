---
{"dg-publish":true,"permalink":"/anteckningar/vue-custom-directives/"}
---

## Skapa egna directives
Vi kan skapa våra egna directives (v-for, v-if o.s.v.)!
Vi börjar med att skapa en fil:
```js
export default {
  beforeMount(element) {
    /* eslint-disable no-param-reassign */
    element.style.position = 'absolute';
    element.style.bottom = '5px';
    element.style.right = '5px';
  },
};
```
Häri har vi tillgång till rätt så [hooks](https://vuejs.org/guide/reusability/custom-directives.html#directive-hooks), så att den kan köras `beforeMount` etc.
Sen behöver vi bara ta emot den i komponenten:
```js
  directives: {
    pin: pinDirective,
  },
```
och kan använda den i template:
```html
<span v-pin>Text</span>
```
## Skicka med data
### Med args och modifiers
```html
<span v-pin:position.top.right>Text</span>
```
```js
export default {
  beforeMount(element, binding) {
	const args = binding.args // position
	const modifiers = binding.modifiers // { top: true, right: true }
	if (args !== "position") return
	Object.keys(modifiers).forEach((key) => {
		/* eslint-disable no-param-reassign */
		element.style[key] = '5px'
	})
	/* eslint-disable no-param-reassign */
	element.style.position = 'absolute';
  },
};
```
### Skicka in som ett objekt
```html
<span v-pin:"{ bottom: '10px', right: '5px' }">Text</span>
```
```js
export default {
  beforeMount(element, binding) {
	Object.keys(binding.value).forEach((position) => {
		/* eslint-disable no-param-reassign */
		element.style[position] = binding.value[position]
	})
	/* eslint-disable no-param-reassign */
	element.style.position = 'absolute';
  },
};
```

### Använda fler hooks för att ändra vid uppdateringar
```js
function applyStyle(element, binding) {
  /* eslint-disable no-param-reassign */
  Object.keys(binding.value).forEach((position) => {
    element.style[position] = binding.value[position];
  });
  element.style.position = 'absolute';
}

export default {
  beforeMount(element, binding) {
    applyStyle(element, binding);
  },
  updated: (element, binding) => {
    applyStyle(element, binding);
  },
};
```
Kan förkortas som (slår ihop `beforeMount` och `updated`):
```js
export default function (element, binding) {
  /* eslint-disable no-param-reassign */
  Object.keys(binding.value).forEach((position) => {
    element.style[position] = binding.value[position];
  });
  element.style.position = 'absolute';
}
```
### Directives tillgängliga globalt
Lägger till den i main/app:
```js
import pinDirective from './shared/pin-directive';
createApp(App)
  .use(router)
  .use(store)
  .directive('pin', pinDirective) // Lägger till här och nu är den tillgänglig globalt med v-pin
  .mount('#app');
```
