---
{"dg-publish":true,"permalink":"/anteckningar/formulaer-kodkonventioner-och-html-5/"}
---

# Kurs: [[Anteckningar/HTML och CSS introduktion\|HTML och CSS introduktion]]
# Föreläsning 7 om Formulär, kodkonventioner och HTML5 [[2022-09-08\|2022-09-08]]
---

# Formulär
Form-elementet har minst två attribut: *method* och *action*. Action anger var formuläret ska skickas och method anger vilken metod som ska användas (POST, GET eller DIALOG).
Inuti formuläret kan vi ange attributet name på element. Då vet servern vilken data som hör till vilken input.
```ad-info
title: Formulär
~~~HTML
<form action="" method="POST">
	<input name="password" type="password" placeholder="Lösenord"/>
</form>
~~~
```
### Flervalselement
Radioknappar skapas genom input-elementet och grupperas genom att de ges samma namn. Till skillnad från andra input-typer så anger värdet i *radio*, *checkbox* och *select* $\rightarrow$ *option* vad som ska skickas till servern och inte vad som står i fältet eller vad som syns för användaren.
### Gruppering av formulärkomponenter
```ad-info
title: Gruppering av formulär
~~~HTML
<form>
	<fieldset>
		<legend>Rubrik</legend>
		<label>Förnamn
			<input name="first-name" placeholder="Förnamn"/> 
		</label>
		<label>Efternamn
			<input name="last-name" placeholder="Efternamn"/> 
		</label>
	</fieldset>
</form>
~~~
```
Genom att lägga formulärkomponenter i en *fieldset* så grupperar vi samman komponenterna. Vi lägger till ett *legend-komponent* för att ange en rubrik för stycket.

### HTML5
- **Article** Används för innehåll som kan vara självständigt. Ex. Bloggpost, tidningsartikel.
- **Aside** Om innehållet inte direkt hör samman och/eller inte är av samma vikt kan det placeras i en aside.
- **Section** Gruppering av element som hör ihop på något sätt och de kan sammanfattas med en rubrik. Ex. Lista med sökresultat, enskilda kapitel i en bok eller en kartvy.

![html5flowchart.png|500](/img/user/Inkorg/Bilder/html5flowchart.png)