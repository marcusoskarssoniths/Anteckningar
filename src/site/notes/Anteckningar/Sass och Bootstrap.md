---
{"dg-publish":true,"permalink":"/anteckningar/sass-och-bootstrap/"}
---

# Kurs: [[Anteckningar/HTML & CSS introduktion\|HTML & CSS introduktion]]
# Föreläsning 11 om Sass och Bootstrap [[2022-09-19\|2022-09-19]]
---

## Sass 
*Syntactically awesome stylesheets* 
- Scss är en typ av sass-kod som kan göra allt som CSS kan göra, och mer.
### Variabler
Sass har variabler som skiljer sig från css-variabler. De skrivs enligt följande
```ad-info
title: Sass-variabler
~~~scss
$heading-color: pink;
$body-text-color: blue;

h1 {
	color: $heading-color;
}
~~~
```
###  Nästlade regler
```ad-info
title: Scss nästlade regler
~~~scss
#featured-article {
	header {
		padding-bottom: .5rem;
	}
}

/* Istället för som i css */
#featured-article header {
	padding-bottom: .5rem;
}
~~~
```
## Bootstrap
Ett CSS-ramverk för att underlätta stilsättningsarbete och används generellt sett via klasser och syftar till att minska mängden CSS-kod och för att snabbt komma igång med en layout.
- Importeras via link-element i html-filen.