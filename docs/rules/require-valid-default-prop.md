# enforce props default values to be valid (require-valid-default-prop)

This rule checks whether the default value of each prop is valid for the given type. It should report an error when default value for type `Array` or `Object` is not returned using function.

## :book: Rule Details

:-1: Examples of **incorrect** code for this rule:

```js
Vue.component('example', {
  props: {
    propA: {
      type: String,
      default: {}
    },
    propB: {
      type: String,
      default: []
    },
    propC: {
      type: Object,
      default: []
    },
    propD: {
      type: Array,
      default: []
    },
    propE: {
      type: Object,
      default: { message: 'hello' }
    }
  }
})
```

:+1: Examples of **correct** code for this rule:

```js
Vue.component('example', {
  props: {
    // basic type check (`null` means accept any type)
    propA: Number,
    // multiple possible types
    propB: [String, Number],
    // a number with default value
    propD: {
      type: Number,
      default: 100
    },
    // object/array defaults should be returned from a factory function
    propE: {
      type: Object,
      default: function () {
        return { message: 'hello' }
      }
    }
  }
})
```

## :wrench: Options

Nothing.
