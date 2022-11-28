---
{"dg-publish":true,"permalink":"/anteckningar/avstand-bakgrunder-margin-and-padding-samt-flexbox/"}
---

# Kurs: [[Anteckningar/HTML och CSS introduktion\|HTML och CSS introduktion]]
# Föreläsning 4 om Avstånd, bakgrunder samt flexbox [[2022-09-01\|2022-09-01]]
---
## Avstånd
Det finns både absoluta och relativa avstånds-mått. Som exempel på absoluta finns *cm*, *in*, *px* och relativa *em*, *rem*, *vw*, *vh*. Em och Rem utgår från textstorleken som kan anges i pixlar alternativt anges automatiskt av webbläsaren (16 eller 18 px).
Teckenstorlek ärvs vilket kan påverka om vi använder em på en div till exempel, då ärvs teckenstorleken och har vi sen fler div påverkas de av den över div:en.
```ad-info
title: För att ändra teckenstorleken på root elementet
~~~CSS
:root {
	font-size: 18px;
}
~~~
```
Det är rekommenderat att inte använda *em* för teckenstorleken, däremot är det bra att använda för margin och padding.
## Bakgrunder
Bakgrundsbilder ska anges i CSS (och inte HTML) och anges genom background-image: url(aaa.jpeg);
Det finns många egenskaper för bakgrundsbilder, som till exempel att den inte ska upprepas, var den ska positioneras och om den ska vara fixerad samt vilken storlek den ska ha. 
```ad-cite
title: MDN om bakgrundsbilder
If the image contains information critical to understanding the page's overall purpose, it is better to describe it semantically in the document.
```
```ad-info
title: Kortform för background
~~~CSS
body {
	background: green ulr(tree.jpeg) no-repeat center center;
}
~~~
```
## Flexbox
Som standard för flexbox placeras elementen ut från vänster till höger och fyller ut det yttre blockets hela höjd - alltså att flex-direction som standard är *row*.
När vi använder flexbox möjliggör det vertikal centrering med *margin: auto;*. I normala fall går det endast horisontellt.
