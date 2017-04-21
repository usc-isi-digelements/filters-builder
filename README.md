# filters-builder

A Polymer Element that builds a list of elasticsearch filters using given config and data.

The `callback` object contains callback functions with properties defined by `callbackTerms` (default `terms`) that return terms from filter objects of specific types.  The terms property contains a function that returns the array of terms using the given filter object from `data` (or `[]` by default).

The `config` object contains a collection of unique keys from `data` mapped to config objects with properties {String} `field` and (Optional) {String} `type`.  The default type is "string".  Supported types are "string".

The `data` object contains a collection of unique keys mapped to search objects with terms.  The keys in `data` match the keys in `config`.  The filter objects are sent to the `callback` functions.

### Example
```js
callback = {
  terms: function(object) {
    return object.value;
  }
};

config = {
  myKey1: {
    field: 'myField1'
  },
  myKey2: {
    field: 'myField2'
  }
};

data = {
  myKey1: {
    value: ['myValue']
  },
  myKey2: {
    value: [1, 2, 3]
  }
};
```

```html
<filters-builder 
  callback="[[callback]]"
  config="[[config]]"
  data="[[data]]"
  filters="{{filters}}">
</filters-builder>
```

### Dependencies

Dependencies are installed using [Bower](http://bower.io/):

    npm install -g bower
    bower install

### Testing

Tests are run using [web-component-tester](https://github.com/Polymer/web-component-tester):

    npm install -g web-component-tester
    wct

### Demonstration & Documentation

Demonstration and documentation are viewed using [polyserve](https://github.com/PolymerLabs/polyserve):

    npm install -g polyserve
    polyserve

