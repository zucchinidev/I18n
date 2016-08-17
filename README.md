# Readme

## Synopsis

Concepto de `Template literals` o plantillas de texto ES6

## Code Example
```

class I18n {

  constructor({
      dictionary = I18n.getDefaultDictionary(),
      culture = 'es',
      placeholder = new RegExp('%\{.+\}')
  } = {}) {
    this.actualDictionary = dictionary;
    this.actualCulture = culture;
    this.actualPlaceholder = placeholder;
  }

  static getDefaultDictionary() {
    return {
      es: {
        'days-ago': 'hace %{count} días',
        'good-morning': 'Buenos días'
      },
      en: {
        'days-ago': '%{count} days ago',
        'good-morning': 'Good moornig'
      }
    };
  }

  get culture() {
    return this.actualCulture;
  }

  set culture(culture) {
    this.actualCulture = culture;
  }

  get dictionary() {
    return this.actualDictionary;
  }

  set dictionary(dictionary) {
    this.actualDictionary = dictionary;
  }

  set placeholder(placeholder) {
    this.actualPlaceholder = placeholder;
  }

  get placeholder() {
    return this.actualPlaceholder;
  }

  t(strings, args) {
    let key = strings.join('').trim();
    let value = this.dictionary[this.culture][key];
    return value.replace(this.placeholder, args);
  }

  static get ES() {
    return 'es';
  }

  static get EN() {
    return 'en';
  }
}


var i18n = new I18n();
i18n.culture = I18n.ES;
let days = 8;
console.log(i18n.t `${days} days-ago`); // hace 8 días
console.log(i18n.t `good-morning`); // Buenos días
i18n.culture = I18n.EN;
console.log(i18n.t `${days} days-ago`); // 8 days ago
console.log(i18n.t `good-morning`); // Good moornig
```
## Motivation

Aprendizaje de ES6 
