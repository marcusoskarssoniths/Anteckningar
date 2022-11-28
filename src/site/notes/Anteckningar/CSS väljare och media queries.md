---
{"dg-publish":true,"permalink":"/anteckningar/css-vaeljare-och-media-queries/"}
---

# Kurs: [[Anteckningar/HTML och CSS introduktion\|HTML och CSS introduktion]]
# Föreläsning 5 om CSS väljare och media queries [[2022-09-05\|2022-09-05]]
---
## Live kod
```ad-info
title: Emmet: skapa flera länkar i en osorterad lista
~~~HTML
ul>li*5>a
~~~
```
Det är ovanligt att sätta *height* på div:ar och andra element eftersom innehållet kan svämma över. Bättre då att sätta *min-height*.
## Väljare
* **Descendant selector**: Matchar alla element som härstammar till elementet. Ex:
```ad-info
title: Sätter bakgrundsfärg på alla em-element som ligger i div
~~~CSS
div em {
	background-color: red;
}
~~~
```
* **Child selector**: Väljaren fungerar som *descendant selector* med skillnaden att *child selektor* tar hänsyn till om elementet direkt härstammar från elementet (är ett barn till). Ex:
```ad-info
title: Sätter bakgrundsfärg till barn-elementet em, som ligger i en div
~~~CSS
div > em {
	background-color: yellow;
}
~~~
```
* **Adjacent sibling combinator**: Matchar det första elementet, som har samma förälder och som ligger precis efter första elementet. Ex:
```ad-info
title: Anger margin på det första textstycket på samma nivå som h2
~~~CSS
h2 + p {
	margin-top: .5rem;
}
~~~
```
* **Attribute selector**: Väljer alla element baserat på existens, eller värdet av, deras HTML-attribut
```ad-info
title: Hittar alla checkbox och döljer dem och om de är valda visar dem
~~~CSS
input[type="checkbox"] {
	display: hidden;	
}
input[checked] {
	display: block;
}
~~~
```
## Media queries
Handlar om att göra att webbsidor fungerar bra på olika enheter med olika skärmstorlekar.
```ad-info
title: Media queries
~~~CSS
@media (min-width: 768px) {
	body {
		background-color: green;
	}
}
~~~
```
Det går även att ange *media queries* i HTML:
```ad-info
title: HTML
~~~HTML
<html>
<head>
<link>
	href="tablet.css"
	media="(min-width: 980px)"
	rel="stylesheet"
</link>
</head>
<body>
</body>
</html>
~~~
```
### Break points och design ranges
En **break point** är punkten där det händer någonting, där hemsidan slår om till ny design (via media queries).
**Design ranges** är det som är mellan break points (innehållet mellan två break points), eller över / under yttre break points.

