---
{"dg-publish":true,"permalink":"/anteckningar/css-block-och-inline-element-div-och-span/"}
---

# Kurs: [[Anteckningar/HTML och CSS introduktion\|HTML och CSS introduktion]]
# Föreläsning 3 om CSS block- och inline-element, div och span [[2022-08-30\|2022-08-30]]
---
## Block- och inline-element

<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/anteckningar/block-element/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




Block-element placeras ut vertikalt, som i en kolumn. Till exempel är rubriker, paragrafer och listor block-element. 
Ett block-element i HTML är ett element som tar upp hela det horisontella området av dess föräldra-element och dess vertikala storlek beror på dess innehåll.
[Alla block-element](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)

</div></div>


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/anteckningar/inline-element/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




Inline-element placeras ut "inline", alltså på samma rad. Till exempel är *a*, *strong*, *em*, *u*, och *img* inline-element. 
Ett inline-element i HTML är ett element som enbart tar upp det utrymme som det behöver, till skillnad från [[Anteckningar/Block-element\|Block-element]] som fyller ut (tar upp) allt utrymme horisontellt.

[Alla inline-element](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)

</div></div>

## Klass och id
Genom att tilldela element i HTML en *klass* eller ett *id* kan man style:a dem direkt i CSS antingen genom *.* (för klasser) eller *#* (för id's).
Viktigt att komma ihåg är att endast ett element får ha ett id, medan flera element kan ha samma klass. Vi kan också tilldela flera klasser till ett element genom att rada upp dem enligt följande:
```ad-info
title: Flera klasser till ett element i HTML
~~~html
<div class="first_class second_class third_class">En div</div>
~~~
```

```ad-info
title: En simpel grid-layout med fyra kolumner, tre rader.
~~~CSS
body {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  grid-template-rows: 2fr 1fr
}
~~~
```
