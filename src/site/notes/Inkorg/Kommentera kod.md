---
{"dg-publish":true,"permalink":"/inkorg/kommentera-kod/"}
---



https://github.com/Aurorien/Farstun/blob/0e78cfd37e594d9f527201fb68e86c8a145bf6de/index.js#L16
Nu är det ju enkelt att förstå men ofta kan man gå ett steg extra och lägga exempelvis tid i en egen variabel som heter något förklarande så att man direkt ser vad siffrorna syftar på, till exempel:
```js
const ONE_SECOND = 1000
setInterval(clock, ONE_SECOND);
```

https://github.com/Aurorien/Farstun/blob/0e78cfd37e594d9f527201fb68e86c8a145bf6de/index.js#L58
Känns som att Västtrafiks API var lite mer avancerad än den enkla som jag använde, coolt att få skicka med headers och hämta en token för att sen få tillgång till de andra endpointsen!

https://github.com/Aurorien/Farstun/blob/0e78cfd37e594d9f527201fb68e86c8a145bf6de/index.js#L83
Tror den här koden kan skrivas mer DRY, till exempel genom att bryta ut i funktioner:
```js
        .then((result) => {
          console.log("fetchData Resultat", result);
          departureboard = result.DepartureBoard.Departure;
          console.log("Västtrafik", departureboard);

          fn1(departureboard)
          vtStationp.textContent = departureboard[0].stop;
          
          //the div-containern with departures is only displayed when the fetch is finished with the code below
          document.querySelector("#vtbox").style.display = "block";
        });
    });
}
function fn1(departureboard) {
  let table = document.querySelectorAll("#vt-dp-table tr:not(:first-of-type")
  table.forEach(function(row) {
    let [td1, td2, td3] = xyy(row)
    td1.textContent = departureboard[1].sname
    td1.style.backgroundcolor = departureboard[1].bgColor;
    td1.style.color = departureboard[1].fgColor;
    td2.textContent = departureboard[1].direction;
    td3.textContent = departureboard[1].rtTime;
  })
}

function fn2(row) {
  let td1 = row.querySelector("td div")
  let [ td2, td3 ] = [...row.querySelectorAll("td:not(:first-of-type)")]
  return [td1, td2, td3]
}
```

https://github.com/Aurorien/Farstun/blob/0e78cfd37e594d9f527201fb68e86c8a145bf6de/index.js#L111
Sa det redan under redovisningsdagen att jag tyckte det var smart att uppdatera innehållet och snodde det ju sen till mitt eget projekt! Coolt :)

https://github.com/Aurorien/Farstun/blob/0e78cfd37e594d9f527201fb68e86c8a145bf6de/index.js#L144
Tipsar om att man kan kolla om det är ett värde bara genom att skriva:
```js
if (variabel) {
	// om variabel har ett "sant" värde
}
// eller tvärtom, om det inte har ett värde:
if (!variabel) {
	// kod
}
// samma som:
if (variable !== null) {
	// tror jag
}
```

https://github.com/Aurorien/Farstun/blob/0e78cfd37e594d9f527201fb68e86c8a145bf6de/index.js#L155
Snyggt med template literal 

Tänker att denna kan vara intressant om du tänker jobba vidare med projektet:
https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API
För att hämta longitud och latitud från webbläsaren.

Och generellt tycker jag du har delat upp i bra funktioner med namn som man förstår vad de gör, och samma sak med många variabelnamn.
En grej jag tänkte på är om det går att strukturera om koden. Det skulle till exempel gå att samla alla dom-element som du hämtar i början av filen. Ha alla funktions-deklarationer längst ned i alfabetisk ordning och sen under alla dom-element kalla på de funktioner som används för du har i princip all kod i funktioner (vilket är bra, tycker jag). Då blir det enklare att snabbt se vad koden gör (genom att läsa vilka funktioner som man kör). Fast tänker att sånt här är en smaksak och det är väl först när vi arbetar med Vue som det finns tydligare regler för hur det är bäst att strukturera all kod.

