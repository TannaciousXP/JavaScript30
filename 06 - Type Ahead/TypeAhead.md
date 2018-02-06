# TypeAhead

```
  function findMatches(wordToMatch, cities) {
    return cities.filter(place => {
      const regex = new RegExp(wordToMatch, 'gi');
      return place.city.match(regex);
    });
  }
```

wordToMatch will be the string to match, 'g = global i = insensity' i (is not case sensitive);

new RegExp(searchfor, options); can be used in match and replace

addEventListener('change', displayMatches);

Grab the data using the fetch API which returns a promise
  json the blob
  push the data into cities using spread

After the 