# Abide Validators
[Official documentation](https://get.foundation/sites/docs/abide.html#adding-custom-pattern-and-validator)

## CPF / CNPJ
CPF and CNPJ validation. Requires formatted value (i.e. 000.000.000-00 or 00.000.000/0000-00)
```javascript
Foundation.Abide.defaults.patterns['document'] = /^([0-9]{3}\.?[0-9]{3}\.?[0-9]{3}\-?[0-9]{2}|[0-9]{2}\.?[0-9]{3}\.?[0-9]{3}\/?[0-9]{4}\-?[0-9]{2})$/;
```
### HTML:
```html
<input id="cpf_cnpj" type="text" pattern="document" required>
```

## CEP
CEP validation. Requires formatted value (i.e. 00000-000)
```javascript
Foundation.Abide.defaults.patterns['cep'] = /^\d{5}-\d{3}/;
```
### HTML:
```html
<input id="cep" type="text" pattern="cep" required>
```

## Phone
Validation for Brazilian telephone and repeating numbers. Requires formatted value (i.e. (00) 00000-0000)
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
### HTML:
```html
<input id="phone" type="tel" data-validator="phone_repetition" required>
```
