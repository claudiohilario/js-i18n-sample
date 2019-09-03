# js-i18n-sample

## Code
```js
var i18n = {
	dictionary: {},
  setDictionary: function(dictionary) {
  	this.dictionary = dictionary;
  },
  
  _t: function(text, params) {
  	var dictionaryText = this.dictionary[text]
    
  	if(!params || !dictionaryText) {
      	return dictionaryText || 'Text "'+text+'" does not exist in dictionary';
    }
    
    for (var param in params) {
    	dictionaryText = dictionaryText.replace('{'+param+'}', params[param]);
    }
    
    return dictionaryText;
  }
}

```

## Example
```js
var dictionary = {
	'Hello': 'Olá',
	'Hello {name1} and {name2}': 'Olá {name1} e {name2}'
}

i18n.setDictionary(dictionary);

i18n._t('Hello'); // Olá
i18n._t('Hello {name1} and {name2}', {
  name1: 'Nome Um',
  name2: 'Nome Dois'
}); //Olá Nome Um e Nome Dois
i18n._t('Does not exist'); //Text "Does not exist" does not exist in dictionary
```
