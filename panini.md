# Panini Helpers
[Official documentation](https://get.foundation/sites/docs/panini.html#helpers)

## src/helpers/clearhtml.js
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
### HTML:
```html
{{#clearhtml}}{{content}}{{/clearhtml}}
```

## src/helpers/contains.js
Checks if a string contains specific text and replaces it.
In this example, we're returning the `page` variable without the `.html` text.
```javascript
module.exports = function(needle, haystack, options) {
  let anchor = needle.replace(haystack + '.html', '');
  return anchor;
}
```
### HTML:
```html
{{#contains url ../page}}./{{url}}{{/contains}}
```

## src/helpers/ifequals.js
_Ifequal_ condition with multiple values.
```javascript
module.exports = function(needle, haystack, options) {
  let parameters = haystack.split(',');
  return parameters.includes(needle) ? options.fn(this) : '';
}
```

### HTML:
```html
{{#ifequals variable 'condition1,condition2,condition3'}}
  ...
{{/ifequals}}
```
