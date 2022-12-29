---
{"dg-publish":true,"permalink":"/inkorg/fetch-och-asynkron-js/"}
---

# Kurs: [[Anteckningar/JavaScript introduktion\|JavaScript introduktion]]
# Föreläsning x om Fetch och asynkron JS 
---
#behöver-arbete 
För att göra webbanrop använder vi oss av *fetch*
```js
fetch("https://avancera.app/cities/")
```

Fetch avslutas innan webbanropet genomförts och returnerar ett [[Inkorg/Promise\|Promise]].

Såhär kan det se ut:
```js
fetch('https://avancera.app/cities/')
  .then(response => response.json())
  .then(result => {
    console.log(result)
  })
```

Hämta filer parallellt men använda dem sekventiellt (Thunks)
```js
function getFile(file) {
	let text, fn

	fakeAjax(file, function(response) {
		if (fn) fn(response)
		else text = response
	})

	return function(cb) {
		if (text) return cb(text)
		else fn = cb
	}
}

// Hämtar alla parallellt
th1 = getFile("file1")
th2 = getFile("file2")
th3 = getFile("file3")

th1(function(text1) {
	output(text1)
	th2(function(text2) {
		output(text2)
		th3(function(text3) {
			output(text3)
			output("Complete")
		})
	})
})
```

Man kan kombinera x antal promises med map och reduce.
```js
["file1", "file2", "file3"]
.map(getFile)
.reduce(function combine(chain, pr) {
	return chain.then(function() {
		return pr;
	}).then(output)
}, Promise.resolve() ).then(function() {
	output("Complete!")
})
```