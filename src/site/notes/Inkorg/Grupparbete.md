---
{"dg-publish":true,"permalink":"/inkorg/grupparbete/"}
---




## Vad har jag gjort
### Adminsidan
- **Produktsidan på admin-webbsidan**. Hela grunden för admin-sidan gjorde Amelie, så jag arbetade vidare på det och flyttade till exempel hämtningen av produkter från komponenten till Vuex [Länk till github](https://github.com/serendipiIT/admin/commit/917318126017a49b44a4985078eafd56f63d2811#diff-d3a5687793bfaf30083074241c3145c03f6b8d5f357e8294b9d3b676d1270e5f). 
  Det resulterade i mer enhetlig kod, då vi överallt använde oss av Vuex-persist för att spara till localStorage istället för att själva sätta och hämta från localStorage. 
  
- **Hämtar, sorterar[^1], filtrerar[^2] alla produkter.** **Omvandlar också data från servern** så den blir enklare att hantera. Detta gör jag i en Vuex-action[^3].
  Eftersom jag visste att datan alltid behövde se ut på ett visst sätt valde jag att omvandla den direkt i en action, annars antar jag att det hade gått lika bra att göra i olika getters.
  
  För själva sorteringen blev lösningen inte så bra, men den löser sin uppgift. I början försökte jag lyfta ut hela logiken som rör sortering (alltså även den kod som hanterar vad som ska sorteras), men den lösningen levde inte kvar men om jag haft mer tid så hade jag gjort om det och brutit ned det i mer lättförståeliga funktioner och hanterat allt på samma plats. Vill inte ha för mycket logik i själva komponenten.
  
- Gjorde så man kan **välja antal produkter per sida** [Länk till github](https://github.com/serendipiIT/admin/blob/main/src/components/ProductOverview.vue).
  Eftersom det var ganska mycket som skulle hända på produktsidan - allt från filtrering, sortering och pagination så hade jag lite problem när jag implementerade allt. Dels var vi kanske inte på det klara från början vad som skulle vara med och dels hade vi arbetat på lite olika sätt. Ibland hade vi saker i Vuex, och ibland hade vi samma saker direkt i komponenten. Det gjorde att jag under arbetets gång flyttade runt kod. I slutändan försökte jag lägga många saker i computed i själva komponenten. 
  Det uppstod också en del problem med mutationer av state utanför Vuex mutations. Tror det kan ha att göra med att jag försökte uppdatera product.title till lowercase för att kunna filtrera. Det ledde också till att data som inte behövde vara i Vuex flyttades därifrån. Och hittade lösningen, som jag pratade med dig om under torsdagen: `JSON.parse(JSON.stringify(data))`.
  
  Funderade länge på hur jag skulle lösa responsiviteten för tabellen. Ofta vill jag ta bort kolumner i mobil-vyn men jag visste inte riktigt hur det skulle kunna se ut i en v-for loop på ett snyggt sätt så i slutändan visar jag en tabell för desktop och en lista för mobil-versionen och hanterar det med två tailwind-klasser. Tycker generellt inte om att visa olika HTML för olika enheter men det var den enklaste lösningen.
  
- Implementerade också **navigation mellan produkter i vyn för att redigera en produkt**[^4]. 
  Precis som innan hade Amelie gjort i princip hela komponenten och jag implementerade bara själva navigationen. 

### Webbshopen
- **Arbetade vidare på vår karusell** som Johan skrivit så att den kanske kunde användas igen på en annan plats i koden [Länk till commit](https://github.com/serendipiIT/sITs/commit/a5c6bccc34a6389ac2be3b660f4bffb6ad3183cf).
  Började reflektera tillsammans med Johan hur vi kanske angriper problem olika och att jag ofta vill göra komponenter och kod i allmänhet mer komplex än den behöver vara. Kom fram till att jag i fortsättningen lite snabbare bara ska börja koda den enkla lösningen och inte alltid tänka på att möjliggöra för framtida förbättringar. Jag behöver inte göra layout-komponenter för att vi i framtiden kanske kommer ha många liknande strukturer utan ska kanske arbeta mer på det som faktiskt gör nytta för stunden.
- Arbetade på **kundvagnen** [Länk till github: CartView](https://github.com/serendipiIT/sITs/blob/main/src/views/CartView.vue), [Länk till github: CartItemCard](https://github.com/serendipiIT/sITs/blob/main/src/components/CartItemCard.vue), och en preview-modal för kundvagnen [Länk till github](https://github.com/serendipiIT/sITs/blob/main/src/components/CartPreviewModal.vue).
  Tyckte verkligen om att kunna bryta ut kod till en egen javascript-fil för att sedan enkelt kunna nå funktionerna från alla komponenter istället för att emit-events när jag vill stänga en modal[^5].
- Använde mig av **Vuex för att spara varorna i kundvagnen, samt räkna ut pris och totalpris** [Länk till github](https://github.com/serendipiIT/sITs/blob/main/src/store/modules/cart.js).
  Återigen ett exempel när jag tog beslut för att jag vi i framtiden kanske skulle göra något - la till exemepel mycket funktionalitet som actions i Vuex, för att jag tänkte att vi snart kommer ha en kundkorg att hämta från backend (vilket vi i slutändan aldrig implementerade). Så reflekterade återigen över att jag gör saker onödigt komplicerade och att det ibland faktiskt är enklare att göra om saker när de faktiskt behövs istället för att göra extra i förväg för saker som aldrig implementeras.
- **Sökfunktion**. Minns inte hur vi kom in på fuzzy search, men Viktor började arbeta på en implementation av levenshteins algoritm som jag senare tog över. Det slutade med att vi kopierade in algoritmen och jag skrev lite kod som använder sig av den för att ge någorlunda bra sökresultat vid felstavning [Länk till github](https://github.com/serendipiIT/sITs/blob/main/src/searchProduct.js).
  Egentligen hade jag velat ha sånt i backend, och jag antar att vi kommer se i vår nästa kurs hur vi kan implementera något liknande fast när vi arbetar med SQL.
  Börjar få mer och mer kläm på alla **array-metoder** och tycker att det är otroligt kul att använda mig av dem och tycker min kod blir mer tydlig[^6].
- Skapade ett custom directive för att testa mig på det. Tanken var att det på ett enhetligt sätt ska **hantera texter (produkt-rubriker) som blir för långa för att det ska vara snyggt**[^7].  
- Parprogrammerade med Johan på **filter-funktionaliteten till produktsidan** som Amelie påbörjat och i princip var klar med [Länk till github](https://github.com/serendipiIT/sITs/commit/f6e87752917142fe9769d3151a9f2ccac104784b).
  Vi diskuterade olika lösningar i gruppen och funderade lite på hur imperativ kod rätt snabbt löser komplexa problem, samtidigt som det kan bli rörigt och lite svårt att felsöka. I slutändan använde vi oss lite mer av funktioner och array-metoder och fick en lite mer deklarativ kod.

### Allmänt kodande
- Vi ofta bett varandra om hjälp och löst problem tillsammans - vilket jag tycker är otroligt svårt att redovisa såhär, även om det nästan alltid hade kunnat beskrivas som parprogrammering då vi delade skärm och löste problem tillsammans.

## Allmänna reflektioner
Vi var en väldigt ambitiös grupp bestående av många med rätt starka viljor vilket resulterade i skyhöga mål och idéer om projektet som vi kanske inte helt lyckades kompromissa ned till något hanterbart inför sprint 1, vilket också syns i våra 42 PBI:er. Inför framtiden tror jag det är mycket bättre att utgå från det allra mest centrala och bygga det för att sen låta projektet växa naturligt samtidigt som man ändå tillåts ha en vision.

Inför sprint två pratade vi om att dela med oss mer kring vad vi arbetar med, att vi varje dag skulle visa upp mer vad vi arbetade med (istället för att bara snabbt berätta). Visserligen blev mötena längre men det var också ett tillfälle då vi snabbare kom in i varandras kod och kunde samarbeta bättre. 



[^1]: ```js

	export function sortBy(key) {
	  return function (productA, productB) {
	    if (typeof productA[key] === 'string') {
	      if (productA[key].toLowerCase() > productB[key].toLowerCase()) return 1
	      if (productA[key].toLowerCase() < productB[key].toLowerCase()) return -1
	      return 0
	    } else {
	      if (productA[key] > productB[key]) return 1
	      if (productA[key] < productB[key]) return -1
	      return 0
	    }
	  }
	}
	```

[^2]: ```js

	export function filterProducts(productList, { active, category }) {
	  // Båda alternativen!
	  let newArr = [...productList]
	  if (active !== null && typeof active === 'boolean') {
	    newArr = newArr.filter((product) => product.active === active)
	  }
	
	  if (category.length > 0) {
	    newArr = newArr.filter((product) => category.some((cat) => cat.toLowerCase() === product.category2.toLowerCase()))
	  }
	  return newArr
	} 
	```

[^3]: ```js

	async getProducts({ commit }) {
	    const products = (await (await fetch('http://SITsApi.us-east-1.elasticbeanstalk.com/products')).json()).data
	    const productsFixedKeys = products.map((product) => {
	      return {
	        ...product,
	        active: product.active,
	        color: product.color?.split(',') || [],
	        id: Number(product.id),
	        price: Number(product.price),
	        size: product.size?.split(',') || [],
	        stock: Number(product.stock),
	      }
	    })
	    commit('setProductList', productsFixedKeys)
	  }, 
	  ```
  
[^4]: ```js

	created() {
	      const index = this.$store.state.filteredProductList.map((product) => product.id).indexOf(this.id)
	      const nextIndex = index < this.$store.state.filteredProductList.length - 1 ? index + 1 : 0
	      const prevIndex = index > 1 ? index - 1 : this.$store.state.filteredProductList.length - 1
	      this.nextId = this.$store.state.filteredProductList[nextIndex]?.id || this.id
	      this.prevId = this.$store.state.filteredProductList[prevIndex]?.id || this.id
    }, 
    ```

[^5]: ```js

	import { ref } from 'vue'

	const isOpen = ref(false)
	
	export default function useCartModal() {
	  function openModal() {
	    isOpen.value = true
	  }
	  function closeModal() {
	    isOpen.value = false
	  }
	
	  return {
	    isOpen,
	    openModal,
	    closeModal,
	  }
	}
	```
[^6]: ```js

	const filteredArray = arr
	    .filter((item) => isDistanceBelowFour(item))
	    .filter((item) => !isMatch(item))
    ```
[^7]: ```js

	export default function (element, binding) {
	  const text = binding.value.text
	  const maxChars = binding.value.chars || 30
	  element.innerText =
	    text.length >= maxChars ? text.slice(0, maxChars) + '...' : text
	}
	```
