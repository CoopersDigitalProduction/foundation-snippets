# Panini Helpers
[Official documentation](https://get.foundation/sites/docs/panini.html#helpers)

## clearhtml.js
Remove HTML from strings.
```javascript
module.exports = function(options) {
  let code = options.fn(this)
            .replace(/&amp;/g, "&")
            .replace(/&lt;/g, "<")
            .replace(/&gt;/g, ">")
            .replace(/&quot;/g, '"')
            .replace(/&#039;/g, "'");
  return code.replace(/(<([^>]+)>)/gi, "");
}
```
### Usage on HTML:
```html
{{#clearhtml}}{{content}}{{/clearhtml}}
```

## contains.js
Checks if a string contains specific text and replaces it.
In this example, we're checking if the given string has 'page_name.html' text and we're removing it.
```javascript
module.exports = function(needle, haystack, options) {
  let anchor = needle.replace(haystack + '.html', '');
  return anchor;
}
```
### Usage on HTML:
```html
{{#contains url ../page}}./{{url}}{{/contains}}
```

## ifequals.js
_Ifequal_ condition with multiple values.
```javascript
module.exports = function(needle, haystack, options) {
  let parameters = haystack.split(',');
  return parameters.includes(needle) ? options.fn(this) : '';
}
```

### Usage on HTML:
```html
{{#ifequals type 'condition1,condition2,condition3'}}
  ...
{{/ifequals}}
```