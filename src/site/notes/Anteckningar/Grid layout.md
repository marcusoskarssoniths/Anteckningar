---
{"dg-publish":true,"permalink":"/anteckningar/grid-layout/"}
---

# Kurs: [[Anteckningar/HTML & CSS introduktion\|HTML & CSS introduktion]]
# Föreläsning 6 om Grid layout [[2022-09-06\|2022-09-06]]
---
## Grid layout
Till skillnad från flexbox så kan vi positionera element både horisontellt och vertikalt samtidigt. Vi arbetar i ett grid - alltså rader och kolumner.
```ad-info
title: Grid layout med ett container-element med 9 barn-element
~~~CSS
container {
	display: grid;
	grid-template-columns: 33% 1em auto;
	grid-template-rows: 50% 1fr 1fr ;
	height: 50px;
}
~~~
```
* **fr**: fractions (ungefär samma som procent men utan problem med marginaler m.m.)
*grid-column: 1/3;* betyder att boxen sträcker sig från första linjen till tredje linjen.
*grid-column: 3/4;* betyder att boxen sträcker sig från tredje linjen till sista (fjärde) linjen - det går att korta ned om boxen skall ta upp resten av området genom att endast ange startlinjen.

* **grid-area**: låter oss namnge områden. 
 ```ad-info
title: Skapar ett namngivet grid-rutnät som man sen placerar in barn-elementen i
~~~CSS
container {
	display: grid;
	grid-template-areas: 
	"art art not"
	"art art asi"
	"fol for asi"
	grid-template-columns: 1fr 1fr 1fr;
	grid-template-rows: 1fr 1fr 1fr ;
	height: 100px;
}
~~~
```
