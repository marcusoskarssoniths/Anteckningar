---
{"dg-publish":true,"permalink":"/anteckningar/vue-components/"}
---

I Vue kan vi arbeta med två typer av komponenter: lokala och globala.

## Lokala komponenter 
En lokal komponent behöver alltid registreras i de komponenter som använder dem:
```js
export default {
  name: 'App',
  components: {
    HomePage,
  },
};
```

## Globala komponenter
Om vi vill registrera en komponent globalt behöver vi ändra i main.js.
Från
```js
createApp(App).mount('#app');
```
Till
```js
import HomePage from "./components/HomePage.vue"
const app = createApp(App).mount('#app');
app.component("HomePage", HomePage)
```
Globala komponenter kan användas direkt, överallt i vår applikation.
Globala komponenter är inte så bra att överanvända då de dels ökar vår bundle size, och dels ökar risken för namn-konflikter.

## Single file component
Innehåller vanligen
```js
<template>
</template>

<script>
</script>

<style>
</style>
```
