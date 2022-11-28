---
{"dg-publish":true,"permalink":"/anteckningar/a-frame-live-server-och-grundlaeggande-css/"}
---


# Kurs: [[Anteckningar/HTML och CSS introduktion\|HTML och CSS introduktion]]
# Föreläsning 2 om A-Frame, Live Server och grundläggande CSS [[2022-08-29\|2022-08-29]]
---
# A-Frame
>Används för att skapa enklare 3D-miljöer, som också fungerar i webbläsare (och VR-headset!) och är ett bra verktyg för att få öva sig i HTML (och hur element och taggar fungerar).

Precis som i vanilla HTML använder vi oss av element med start- och sluttaggar när vi arbetar med A-Frame. 
För instruktioner och dokumentation: [A-Frame dokumentation](https://aframe.io/docs/1.3.0/introduction/)
# Live Server
Finns att installera som extension i VS Code.
# CSS
## Grunder
- **HTML** är ett språk för att *strukturera information* i ett dokument
- **CSS** är ett språk för att *specificera utseendet* på ett dokument
För att se hur mycket CSS kan påverka en hemsidas utseende rekommenderas [CSS Zen Garden](http://www.csszengarden.com/)
CSS används för att positionera element, bredder och höjder på element. För att ange färger och bakgrundsbilder samt typsnitt.
### Syntax och regler
I princip
```CSS
selector {
	property: value;
}
```
### Skriva CSS
Antingen kan man skriva i ett eget CSS-dokument och importera det till HTML-dokumentet med *link*, eller så kan man använda *style-taggen* eller *style-attributet*. 
## Färger
Färger kan anges på många olika sätt i CSS. Bland annat finns ett par färger namngivna (till exempel red, blue, black, white m.m.). 
Ex. *#ff0000* alt. *#f00*, *rgb(255, 0, 0)* eller *rgba(255, 0, 0, 1)*. 
- *Rgba* kan anger även genomskinlighet.
## Typsnitt
- Font-style anger vilken stil texten ska ha. Till exempel *italic*
- Font-weight anger tjockleken på texten. Till exempel *bold*, *light*, *700*
- Font-size anger typsnittsstorlek (*em*, *%*, *px*, *rem*)
- Line-height anger höjden på rader
- text-indent indenterar första raden på nytt stycke
- text-align för att positionera text
- text-decoration dekorerar text med t.ex. underline
```ad-important
title: Font - shorthand
~~~CSS
selector {
	font: font-style font-weight font-variant font-size/line-height font-family
}
~~~
```

### Font-family
Font-family anger fonten (typsnitt) på texten
Det finns generellt tre kategorier *serif* (med fötter) ex. Times new roman, *sans-serif* (utan fötter) ex. Arial, *monospace* (alla tecken är lika breda)
För att ange ett typsnitt med *font stacking*: 
```ad-important
title: Font stacking
~~~CSS
selector {
	font-family: Arial, sans-serif;
	font-family: 'times New Roman', serif;
}
~~~
```
### Google Fonts
[Google Fonts](https://fonts.google.com/)
För att använda google fonts så väljer vi ett typsnitt på Google, laddar ned det och sparar det i projekt-mappen. Dels länkar jag till filen med typsnittet och dels anger jag formatet (som oftast är *truetype* - men det finns andra format!). Lägg till följande i CSS-filen:
```ad-important
title: Använda Google fonts
~~~CSS
@font-face {
	font-family: Roboto;
	src: url('Roboto-Regular.ttf') format('truetype');
}
selector {
	font-family: Roboto, sans-serif;
}
~~~
```
För att inkludera flera olika tjocklekar på typsnittet:
```ad-important
title: Inkludera fler tjocklekar på ett typsnitt
~~~CSS
@font-face {
    font-family: "myFont";
    src: url(Lato-Regular.ttf) format('truetype');
    font-weight: normal;
}

@font-face {
    font-family: "myFont";
    src: url(Lato-Light.ttf) format("truetype");
    font-weight: 300;
}
~~~

```