# Abide Validators
[Official documentation](https://get.foundation/sites/docs/abide.html#adding-custom-pattern-and-validator)

## CPF / CNPJ
```javascript
Foundation.Abide.defaults.patterns['document'] = /^([0-9]{3}\.?[0-9]{3}\.?[0-9]{3}\-?[0-9]{2}|[0-9]{2}\.?[0-9]{3}\.?[0-9]{3}\/?[0-9]{4}\-?[0-9]{2})$/;
```
```html
<input id="cpf_cnpj" type="text" pattern="document" required>
```

## Phone (Brazilian pattern and number repetition)
```javascript
function phoneValidator(
  $el,      /* jQuery element to validate */
  required, /* is the element required according to the `[required]` attribute */
  parent    /* parent of the jQuery element `$el` */
) {
  var phone = $el.val();
  var phoneOnlyNumbers = phone.replace(/\D/g,'');

  if (!required && phone == '') return true;
  
  var patternRepetition = /([0-9])\1{8,}/;
  var patternNumber = /^(\(\d{2}\)\s)(\d{4,5}\-\d{4})$/;
  if (patternRepetition.test(phoneOnlyNumbers) == false && patternNumber.test(phone)) return true;
};

Foundation.Abide.defaults.validators['phone_repetition'] = phoneValidator;
```

```html
<input id="phone" type="tel" data-validator="phone_repetition" required>
```