# @emiplegiaqmnpm/quo-distinctio-quas

```text
@emiplegiaqmnpm/quo-distinctio-quas(<value>) => <type_name>
```
Returns type of value or object instance.
This is an alternative to `typeof` that actually allows to avoid confusion between the type name and the class name.
Returns the name of Class (or constructor function, or reserved type name), for example:
'Object', 'Number', 'String', 'NotNumber', 'Global', 'Dictionary', 'Null', 'Array', etc.

## Usage

```javascript
const @emiplegiaqmnpm/quo-distinctio-quas = require('@emiplegiaqmnpm/quo-distinctio-quas')

@emiplegiaqmnpm/quo-distinctio-quas(undefined) //=> 'Undefined'

@emiplegiaqmnpm/quo-distinctio-quas(null) //=> 'Null' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(true) //=> 'Boolean'

@emiplegiaqmnpm/quo-distinctio-quas(false) //=> 'Boolean'

@emiplegiaqmnpm/quo-distinctio-quas(new Boolean(true)) //=> 'Boolean' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(new MyClass()) //=> 'MyClass' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(42) //=> 'Number'

@emiplegiaqmnpm/quo-distinctio-quas(new Number(42)) //=> 'Number' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(1/0) //=> 'InfiniteNumber' but not 'number'

@emiplegiaqmnpm/quo-distinctio-quas(-Infinity) //=> 'InfiniteNumber' but not 'number'

@emiplegiaqmnpm/quo-distinctio-quas(NaN) //=> 'NotNumber' but not 'number'

@emiplegiaqmnpm/quo-distinctio-quas('str') //=> 'String'

@emiplegiaqmnpm/quo-distinctio-quas(new String('str')) //=> 'String' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas({}) //=> 'Object'

@emiplegiaqmnpm/quo-distinctio-quas(Object.create(null)) //=> 'Dictionary' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(new Object()) //=> 'Object'

@emiplegiaqmnpm/quo-distinctio-quas(new Date()) //=> 'Date'

@emiplegiaqmnpm/quo-distinctio-quas([1, 2, 3]) //=> 'Array'

@emiplegiaqmnpm/quo-distinctio-quas(/a-z/) //=> 'RegExp' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(new RegExp('foo')) //=> 'RegExp' but not 'object'

@emiplegiaqmnpm/quo-distinctio-quas(new Error('error')) //=> 'Error'

@emiplegiaqmnpm/quo-distinctio-quas(new ReferenceError('')) //=> 'ReferenceError'

@emiplegiaqmnpm/quo-distinctio-quas(function () {}) //=> 'Function'

@emiplegiaqmnpm/quo-distinctio-quas(async function () {}) //=> 'AsyncFunction'

@emiplegiaqmnpm/quo-distinctio-quas(() => {}) //=> 'Function'

@emiplegiaqmnpm/quo-distinctio-quas(function * () {}) //=> 'GeneratorFunction'

@emiplegiaqmnpm/quo-distinctio-quas(Symbol('str')) //=> 'Symbol'

@emiplegiaqmnpm/quo-distinctio-quas(new Map()) //=> 'Map'

@emiplegiaqmnpm/quo-distinctio-quas(new Int8Array()) //=> 'Int8Array'

@emiplegiaqmnpm/quo-distinctio-quas(window) //=> 'Global' but not 'object'
```

## Reserved type names

Reserved type names make possible to distinguish type of some special values from values with the real type.
Historically, accessing the global object has required different syntax in different JavaScript environments. On the web you can use `window`, `self`, `frames`, in Node.js you must instead use `global` and type of this global value is 'object'. Also there are not straightforward situations with `null`, `NaN` and `Infinity` values.
To determine the type of such values the `@emiplegiaqmnpm/quo-distinctio-quas` function returns the following type names:

- **'Undefined'** for `undefined` (typeof(undefined) -> 'undefined')
- **'Null'** for `null` (typeof(null) -> 'object')
- **'Global'** for `global`, `window`, etc. (typeof(global) -> 'object')
- **'NotNumber'** for `NaN` (typeof(NaN) -> 'number')
- **'InfiniteNumber'** for `Infinity` or `-Infinity` (typeof(Infinity) -> 'number')
- **'Dictionary'** for `object without prototype` (typeof(Object.create(null)) -> 'object') that was created by `Object.create(null)`

## Install

> Install on Node.JS with [npm](https://www.npmjs.com/)

```bash
npm install @emiplegiaqmnpm/quo-distinctio-quas
```

## License

MIT © [Taras Panasyuk](webdev.taras@gmail.com)
