## Consegna

```
💡 Nota: a differenza di quanto visto finora negli esempi, per accedere all'API utilizzare l'url base:

http://localhost:3333

al posto di:

https://freetestapi.com/api/v1

Ad esempio:

http://localhost:3333/users

per chiamare l'endpoint /users
```

In questo esercizio, utilizzerai **_Promise.all()_** per creare la funzione **_getDashboardData(query)_**, che accetta una città come input e recupera simultaneamente:

✔︎ Nome completo della città e paese da <font color="red">/destinations?search=[query]</font>
(result.name, result.country, nelle nuove proprietà city e country).

✔︎ Il meteo attuale da <font color="red">/weathers?search={query}</font>
(result.temperature e result.weather_description nella nuove proprietà temperature e weather).

✔︎ Il nome dell’aeroporto principale da <font color="red">/airports?search={query}</font>
(result.name nella nuova proprietà airport).

Utilizzerai <font color="red">Promise.all()</font> per eseguire queste richieste in parallelo e poi restituirai un oggetto con i dati aggregati.

```
💡 Attenzione: le chiamate sono delle ricerche e ritornano un’array ciascuna, di cui devi prendere il primo risultato (il primo elemento).
```

## Note del docente

Scrivi la funzione <font color="red">getDashboardData(query)</font>, che deve:

✔︎ Essere asincrona (<font color="red">async</font>).

✔︎ Utilizzare <font color="red">Promise.all()</font> per eseguire più richieste in parallelo.

✔︎ Restituire una <font color="red">Promise</font> che risolve un oggetto contenente i dati aggregati.

✔︎ Stampare i dati in console in un messaggio ben formattato.

✔︎ Testa la funzione con la query "london"

## Esempio di utilizzo

```js
getDashboardData("london")
  .then((data) => {
    console.log("Dasboard data:", data);
    console.log(
      `${data.city} is in ${data.country}.\n` +
        `Today there are ${data.temperature} degrees and the weather is ${data.weather}.\n` +
        `The main airport is ${data.airport}.\n`
    );
  })
  .catch((error) => console.error(error));
```

## Esempio di output atteso

```js
// Risposta API
{
  city: "London",
  country: "United Kingdom",
  temperature: 18,
  weather: "Partly cloudy",
  airport: "London Heathrow Airport"
}

// Output in console
London is in United Kingdom.
Today there are 18 degrees and the weather is Partly cloudy.
The main airport is London Heathrow Airport.
```

## 🎯 Bonus 1 - Risultato vuoto

**_Se l’array di ricerca è vuoto_**, invece di far fallire l'intera funzione, semplicemente i dati relativi a quella chiamata verranno settati a null e la frase relativa non viene stampata. Testa la funzione con la query “vienna” (non trova il meteo).

```js
// Risposta API
{
  city: "Vienna",
  country: "Austria",
  temperature: null,
  weather: null,
  airport: "Vienna International Airport"
}

// Output in console
Vienna is in Austria.
The main airport is Vienna International Airport.
```

## 🎯 Bonus 2 - Chiamate fallite

Attualmente, se una delle chiamate fallisce, **_Promise.all()_** rigetta l'intera operazione.

Modifica getDashboardData() per usare **_Promise.allSettled()_**, in modo che:

✔︎ **_Se una chiamata fallisce_**, i dati relativi a quella chiamata verranno settati a null.

✔︎ Stampa in console un messaggio di errore per ogni richiesta fallita.

✔︎ Testa la funzione con un link fittizio per il meteo (es. https://www.meteofittizio.it).
