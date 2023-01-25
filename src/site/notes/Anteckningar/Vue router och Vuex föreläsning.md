---
{"dg-publish":true,"permalink":"/anteckningar/vue-router-och-vuex-foerelaesning/"}
---


# Kurs: [[Inkorg/Javascript med ramverk\|Javascript med ramverk]]
# Föreläsning 5 om Vue router och Vuex föreläsning [[2023-01-23\|2023-01-23]]
---

## Vue router
Låter oss skapa SPA's, som har flera sidor men bara en HTML-fil.
Eftersom vi bygger SPA's så kan koden vara mer sammanhängande, vi kan skriva all kod i till exempel Vue.
Vue-router sköter allt som har med navigering att göra (bakåt och framåt-pilar, adressfältet etc.).
importeras via CDN med:
```html
<script src="[https://unpkg.com/vue-router@4"](https://unpkg.com/vue-router@4%22 "https://unpkg.com/vue-router@4%22")></script>


// och sen:
<router-link to="/">Hem</router-link>
<router-link to="/about">Om</router-link>
<router-link to="/contact">Kontakt</router-link>

// Här i renderas alla sidor:
<router-view></router-view>
```
```js
const app = Vue.createApp({})

const Home = { template: '<h1>Hem</h1>' }
const About = { template: '<h1>Om</h1>' }
const Contact = { template: '<h1>Kontakt</h1>' }

const routes =  [
	{
		component: Home,
		path: = "/"
	},
	{
		component: About,
		path: = "/about"
	},
	{
		component: Contact,
		path: = "/contact"
	}
]

const router = Vue.createRouter({
	history: VueRouter.createWebHashHistory,
	routes
})

app.use(router).mount("#app")
```

Man kan använda sig av webbläsarens adressfält för att anpassa innehållet dynamiskt med vue-router.



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/anteckningar/vuex/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




Hur delar vi state mellan komponenter? Antingen kan vi göra som vi gjort hittills med props och custom events eller, vilket är vanligare, så använder vi *Vuex* för den data som behöver vara åtkomlig från flera olika komponenter i en app. Användbart att spara om användaren är inloggad, dark-mode, och liknande i ett globalt state som Vuex.

---

<style> .container {font-family: sans-serif; text-align: center;} .button-wrapper button {z-index: 1;height: 40px; width: 100px; margin: 10px;padding: 5px;} .excalidraw .App-menu_top .buttonList { display: flex;} .excalidraw-wrapper { height: 800px; margin: 50px; position: relative;} :root[dir="ltr"] .excalidraw .layer-ui__wrapper .zen-mode-transition.App-menu_bottom--transition-left {transform: none;} </style><script src="https://unpkg.com/react@17/umd/react.production.min.js"></script><script src="https://unpkg.com/react-dom@17/umd/react-dom.production.min.js"></script><script type="text/javascript" src="https://unpkg.com/@excalidraw/excalidraw@0/dist/excalidraw.production.min.js"></script><div id="vuexexcalidraw.md1"></div><script>(function(){const InitialData={"type":"excalidraw","version":2,"source":"https://excalidraw.com","elements":[{"id":"Rx260TK0VQlvzQQ25vC-Y","type":"rectangle","x":55.2224392361112,"y":-587.0999501546228,"width":214.4000244140625,"height":34.40000915527344,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":1008565284,"version":118,"versionNonce":204499236,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"id":"1PwCeqwZxWmWwkRAfO4Y7","type":"rectangle","x":60.0224880642362,"y":-534.299947102865,"width":116,"height":144.79998779296875,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":1666449180,"version":89,"versionNonce":1547774748,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"id":"tcFN1gHHBHUhSayttJSvw","type":"rectangle","x":192.0226101345487,"y":-531.0999348958337,"width":79.9998779296875,"height":44.79998779296875,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":2142231332,"version":133,"versionNonce":1678746788,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"rectangle","version":171,"versionNonce":1638229916,"isDeleted":false,"id":"14anRV-DBa_jmAdqaesqd","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":193.82247585720495,"y":-472.29994710286496,"strokeColor":"#000000","backgroundColor":"transparent","width":79.9998779296875,"height":76.79998779296875,"seed":793250212,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"id":"Dr5XcWRHJI_-aAVYwR9hT","type":"ellipse","x":89.62246365017371,"y":-336.6999104817712,"width":10.545446979102362,"height":23.199951171875,"angle":0,"strokeColor":"#364fc7","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":557512988,"version":167,"versionNonce":58421284,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"id":"OPCmAeyK9A_sN7_DyO54y","type":"ellipse","x":90.46608653564182,"y":-335.012664710835,"width":9.27998046875,"height":11.389102046720678,"angle":0,"strokeColor":"#364fc7","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":442465444,"version":152,"versionNonce":407770140,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":142,"versionNonce":1784794020,"isDeleted":false,"id":"MMJCSj1XV4-899sjYBEXy","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":154.3497401606225,"y":-421.8999532063806,"strokeColor":"#364fc7","backgroundColor":"transparent","width":10.545446979102362,"height":23.199951171875,"seed":1319109028,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":127,"versionNonce":1043148956,"isDeleted":false,"id":"39DsQbwS7t0eTTS0LE7MV","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":155.1933630460906,"y":-420.2127074354444,"strokeColor":"#364fc7","backgroundColor":"transparent","width":9.27998046875,"height":11.389102046720678,"seed":1821727388,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":159,"versionNonce":1794160420,"isDeleted":false,"id":"sStc6NsbzvvtW7ZD0Rppr","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":257.94971574656006,"y":-424.6999104817712,"strokeColor":"#364fc7","backgroundColor":"transparent","width":10.545446979102362,"height":23.199951171875,"seed":832162588,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":144,"versionNonce":49593628,"isDeleted":false,"id":"PlHs5GvV0GgOeHUEQp0G_","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":258.7933386320281,"y":-423.012664710835,"strokeColor":"#364fc7","backgroundColor":"transparent","width":9.27998046875,"height":11.389102046720678,"seed":638649508,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":182,"versionNonce":1637233316,"isDeleted":false,"id":"3PVQbSRWUivKWsNKra6g6","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":254.149666918435,"y":-513.299947102865,"strokeColor":"#364fc7","backgroundColor":"transparent","width":10.545446979102362,"height":23.199951171875,"seed":794066852,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":167,"versionNonce":1343666588,"isDeleted":false,"id":"XpfRPHtMTid7lskXQ1Ul6","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":254.9932898039031,"y":-511.61270133192875,"strokeColor":"#364fc7","backgroundColor":"transparent","width":9.27998046875,"height":11.389102046720678,"seed":2112863388,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":192,"versionNonce":1828732452,"isDeleted":false,"id":"q-sYr9-GTr2I5ivuSDxfm","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":249.5496913324975,"y":-579.299947102865,"strokeColor":"#364fc7","backgroundColor":"transparent","width":10.545446979102362,"height":23.199951171875,"seed":147856796,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"type":"ellipse","version":177,"versionNonce":281355804,"isDeleted":false,"id":"bqRvbh7Ug8T7tXRtBb5Fp","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":250.3933142179656,"y":-577.6127013319287,"strokeColor":"#364fc7","backgroundColor":"transparent","width":9.27998046875,"height":11.389102046720678,"seed":1107237412,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"id":"jWC9m8TT","type":"text","x":109.6224636501737,"y":-339.29994710286496,"width":73,"height":50,"angle":0,"strokeColor":"#364fc7","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":1262429092,"version":69,"versionNonce":639424932,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false,"text":"= data\n","rawText":"= data\n","fontSize":20,"fontFamily":1,"textAlign":"left","verticalAlign":"top","baseline":43,"containerId":null,"originalText":"= data\n"},{"id":"N74cuuni_GRFY_nVFPONG","type":"rectangle","x":89.6224636501737,"y":-298.29994710286496,"width":16.800048828125,"height":17.5999755859375,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":703431708,"version":76,"versionNonce":2045903516,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false},{"id":"LCTa9oi7","type":"text","x":114.4225124782987,"y":-303.29994710286496,"width":119,"height":25,"angle":0,"strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":1671042716,"version":65,"versionNonce":1478100260,"isDeleted":false,"boundElements":null,"updated":1674476103435,"link":null,"locked":false,"text":"= komponent","rawText":"= komponent","fontSize":20,"fontFamily":1,"textAlign":"left","verticalAlign":"top","baseline":18,"containerId":null,"originalText":"= komponent"},{"id":"MEH2tPd7SI5G7SBIU9JRe","type":"ellipse","x":355.6767452236665,"y":-339.57838390076125,"width":75.90360796028591,"height":43.90358761523379,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":1598726564,"version":332,"versionNonce":1770469284,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false},{"id":"6pPG1Au42nVEmHxkIec67","type":"line","x":355.6767452236665,"y":-319.8133483247977,"width":0,"height":104.87453724929861,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"round","seed":1385110684,"version":305,"versionNonce":1063552156,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"points":[[0,0],[0,104.87453724929861]],"lastCommittedPoint":null,"startBinding":null,"endBinding":null,"startArrowhead":null,"endArrowhead":null},{"type":"line","version":398,"versionNonce":982033188,"isDeleted":false,"id":"UXZt_do_D2y-S6PRJ6Ysg","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":431.25417999933194,"y":-320.31028630896515,"strokeColor":"#862e9c","backgroundColor":"transparent","width":0,"height":104.87453724929861,"seed":1126060188,"groupIds":[],"strokeSharpness":"round","boundElements":null,"updated":1674476100079,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":null,"points":[[0,0],[0,104.87453724929861]]},{"id":"U9dKqQFuk_DkZrbV6iCK3","type":"line","x":355.6767452236665,"y":-216.09767211831513,"width":76.48306058470826,"height":1.1588610428160229,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"round","seed":591721636,"version":257,"versionNonce":169971996,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"points":[[0,0],[76.48306058470826,1.1588610428160229]],"lastCommittedPoint":null,"startBinding":null,"endBinding":null,"startArrowhead":null,"endArrowhead":null},{"type":"rectangle","version":229,"versionNonce":1330683556,"isDeleted":false,"id":"E-svDGLIYTZO1B4nxmzrc","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":344.8113979763457,"y":-586.6333084106449,"strokeColor":"#000000","backgroundColor":"transparent","width":214.4000244140625,"height":34.40000915527344,"seed":1407167004,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476100079,"link":null,"locked":false},{"type":"rectangle","version":200,"versionNonce":42536348,"isDeleted":false,"id":"i2IwDftS71g4H7rk5fxq_","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":349.6114468044707,"y":-533.8333053588871,"strokeColor":"#000000","backgroundColor":"transparent","width":116,"height":144.79998779296875,"seed":450663844,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476100079,"link":null,"locked":false},{"type":"rectangle","version":244,"versionNonce":277686820,"isDeleted":false,"id":"ndIs6Kr7G7YJgLMgPha8-","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":481.6115688747832,"y":-530.6332931518558,"strokeColor":"#000000","backgroundColor":"transparent","width":79.9998779296875,"height":44.79998779296875,"seed":2132543132,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476100079,"link":null,"locked":false},{"type":"rectangle","version":282,"versionNonce":1775041052,"isDeleted":false,"id":"ZH7iTOVYy9z9_85wQS8zY","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":483.41143459743944,"y":-471.83330535888706,"strokeColor":"#000000","backgroundColor":"transparent","width":79.9998779296875,"height":76.79998779296875,"seed":360857892,"groupIds":[],"strokeSharpness":"sharp","boundElements":null,"updated":1674476100079,"link":null,"locked":false},{"id":"5cSE2rzs","type":"text","x":455.41146387760057,"y":-301.59692182275234,"width":68,"height":25,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"sharp","seed":1791810460,"version":127,"versionNonce":556549540,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"text":"= Vuex","rawText":"= Vuex","fontSize":20,"fontFamily":1,"textAlign":"left","verticalAlign":"top","baseline":18,"containerId":null,"originalText":"= Vuex"},{"id":"w8FxXqebtoPLswiwiSOmN","type":"line","x":455.41146387760057,"y":-401.7733780497744,"width":62.117560891544144,"height":87.52940458409927,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"round","seed":382731684,"version":143,"versionNonce":182408860,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"points":[[0,0],[-62.117560891544144,87.52940458409927]],"lastCommittedPoint":null,"startBinding":null,"endBinding":null,"startArrowhead":null,"endArrowhead":null},{"id":"OaZJ4nsDLS56_jZfY5uCp","type":"line","x":395.1762272048064,"y":-313.30277545326703,"width":160,"height":94.1176470588236,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"round","seed":710809884,"version":165,"versionNonce":375124260,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"points":[[0,0],[160,-94.1176470588236]],"lastCommittedPoint":null,"startBinding":null,"endBinding":null,"startArrowhead":null,"endArrowhead":null},{"id":"F0e9kw9QK7cGcmrZTUbrN","type":"line","x":393.2939029860564,"y":-312.36161334389203,"width":160.94109030330878,"height":183.5294117647059,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"round","seed":1287187108,"version":202,"versionNonce":41034524,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"points":[[0,0],[160.94109030330878,-183.5294117647059]],"lastCommittedPoint":null,"startBinding":null,"endBinding":null,"startArrowhead":null,"endArrowhead":null},{"id":"NrTl4QuZoFZYq2V4rg0C4","type":"line","x":394.2349932893652,"y":-314.24397346567514,"width":157.1764418658089,"height":247.52940458409932,"angle":0,"strokeColor":"#862e9c","backgroundColor":"transparent","fillStyle":"hachure","strokeWidth":1,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"strokeSharpness":"round","seed":1512963740,"version":213,"versionNonce":797584548,"isDeleted":false,"boundElements":null,"updated":1674476100079,"link":null,"locked":false,"points":[[0,0],[157.1764418658089,-247.52940458409932]],"lastCommittedPoint":null,"startBinding":null,"endBinding":null,"startArrowhead":null,"endArrowhead":null}],"appState":{"theme":"dark","viewBackgroundColor":"#efefef","currentItemStrokeColor":"#862e9c","currentItemBackgroundColor":"transparent","currentItemFillStyle":"hachure","currentItemStrokeWidth":1,"currentItemStrokeStyle":"solid","currentItemRoughness":1,"currentItemOpacity":100,"currentItemFontFamily":1,"currentItemFontSize":20,"currentItemTextAlign":"left","currentItemStrokeSharpness":"sharp","currentItemStartArrowhead":null,"currentItemEndArrowhead":"arrow","scrollX":298.26482994130026,"scrollY":863.2166820108001,"zoom":{"value":0.5999999999999996},"currentItemLinearStrokeSharpness":"round","gridSize":null,"colorPalette":{}},"files":{}};InitialData.scrollToContent=true;App=()=>{const e=React.useRef(null),t=React.useRef(null),[n,i]=React.useState({width:void 0,height:void 0});return React.useEffect(()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height});const e=()=>{i({width:t.current.getBoundingClientRect().width,height:t.current.getBoundingClientRect().height})};return window.addEventListener("resize",e),()=>window.removeEventListener("resize",e)},[t]),React.createElement(React.Fragment,null,React.createElement("div",{className:"excalidraw-wrapper",ref:t},React.createElement(ExcalidrawLib.Excalidraw,{ref:e,width:n.width,height:n.height,initialData:InitialData,viewModeEnabled:!0,zenModeEnabled:!0,gridModeEnabled:!1})))},excalidrawWrapper=document.getElementById("vuexexcalidraw.md1");ReactDOM.render(React.createElement(App),excalidrawWrapper);})();</script>

### Skapa en store och spara värden
```js
import { createStore } from 'vuex';

export default createStore({
  state: {
    cart: [],
  },
```

### Ändra värden
```js
import { createStore } from 'vuex';

export default createStore({
  state: {
    cart: [],
  },
  mutations: {
	  addRobotToCart(state, robot) {
		  state.cart.push(robot)
	  },
  },
```

### Hämta värden direkt
Vi kommer åt värden direkt i våra komponenter.
Det är smidigt att lägga det i en `computed` för att enklare komma åt värdet:
```js
export default {
  name: 'ShoppingCart',
  computed: {
    cart() {
      return this.$store.state.cart;
    },
};
```

### Hämta värden via getters
Om vi först lägger till en getter i vår store:
```js
import { createStore } from 'vuex';
export default createStore({
  state: {
    cart: [],
  },
  getters: {
    cartSaleItems(state) {
      return state.cart.filter((item) => item.head.onSale);
    },
  },
});
```

Kan vi sen hämta `computed`-värden från vår store
```js
export default {
  name: 'ShoppingCart',
  computed: {
    cartSaleItems() {
      return this.$store.getters.cartSaleItems;
    },
  },
};
```

### Använda actions för att hämta värden från en API till store
```js
import { createStore } from 'vuex';
import axios from 'axios';

export default createStore({
  actions: {
    getParts({ commit }) { // tar emot context som innehåller state, getters, commits, dispatch
      axios.get('/api/parts')
        .then((result) => commit('updateParts', result.data))
        .catch(console.error);
    },
  },
  mutations: {
    updateParts(state, parts) {
      state.parts = parts;
    },
  },
  state: {
    parts: null,
  },
});
```

Och för att använda oss av en action:
```js
this.$store.dispatch('getParts');
```

### Använda actions för att posta värden till en server
```js
export default createStore({
  actions: {
    addRobotToCart({ commit, state }, robot) {
      const cart = [...state.cart, robot];
      axios.post('/api/cart', cart)
        .then(() => commit('addRobotToCart', robot));
    },
  },
    mutations: {
    addRobotToCart(state, robot) {
      state.cart.push(robot);
    },
  },
  state: {
	  cart: []
  }
 })
```
och för att använda i en komponent:
```js
this.$store.dispatch('addRobotToCart', { ...robot, cost });
```

### Komponenten kan få reda på när en action är klar
```js
  actions: {
    addRobotToCart({ commit, state }, robot) {
      const cart = [...state.cart, robot];
      return axios.post('/api/cart', cart) // Returnerar hela axios.post
        .then(() => commit('addRobotToCart', robot));
    },
  },
```

Och i komponenten får vi nu tillbaka ett promise:
```js
this.$store.dispatch('addRobotToCart', { ...robot, cost })
	.then(() => this.$router.pust("/cart"))
```

### Organisera store i moduler
Vi börjar med att bryta ut allt som har med robots (i det här exemplet) att göra till en egen modul som sparas i *store --> modules --> robots.js*: 
```js
import axios from 'axios';
export default {
	// ... allt tidigare innehåll från state
}
```

Vi importerar det sen till store:
```js
import { createStore } from 'vuex';

import robotsModule from './modules/robots';

export default createStore({
  modules: {
    robots: robotsModule,
  },
});
```

För att använda det i komponenter behöver vi nu skriva:
```js
this.$store.state.robots.cart;
```
Man behöver inte ändra något för mutations, getters eller actions för att det ska fungera men Vuex vet inte vilken moduls mutations eller actions som man vill åt och kör därför alla som har samma namn.
Man kan lösa det genom `namespacing`. Som default har alltid state namespacing, vilket inte actions, getters och mutations har.

### Använda namespacing
I vår modul i store lägger vi till:
```js
namespaced: true,
```

Och i komponenterna behöver vi sen skriva:
```js
this.$store.dispatch('robots/addRobotToCart', { ...robot, cost });
```

#### namespacing getters
```js
this.$store.getters['robots/cartSaleItems'];
```

### Helperfunctions (MapState, MapGetters, MapActions, MapMutations)
#### MapState & MapGetters
Man göra på samma sätt för MapState och MapGetters, och kallar dem i `computed`
```js
import { mapState } from 'Vuex'

// I vår komponents computed kan vi nu skriva:
...mapState({
	someValueName: 'stateValueName',
	name: state => state.robots.someValueNameInModule // för att komma åt moduler
})
// Kan också skrivas
...mapState('robots', { name: someValueNameInModule })
```
#### MapActions & MapMutations
Här kallar vi istället på MapActions i `methods`:
```js
methods: {
	[...mapActions('robots', [ 'getParts', 'addRobotToCart' ])]() // Vi behöver inte längre kalla på dispatch i vår komponent, utan det sköts automatiskt av mapActions!
}
```
Vi ändrar alltså alla våra `dispatch`:
```js
// från
this.$store.dispatch('robots/getParts');
// Till
this.getParts()
```

</div></div>
