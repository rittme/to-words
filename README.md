# Number to Words

## Introduction

Converts Numbers (including decimal points) into words for Indian style. It also converts the numbers into words for currency, again, for Indian style.

## Installation

```js
npm install to-words --save
```

## Usage

Importing
```js
const { ToWords } = require('to-words');
```
OR
```js
Import { ToWords } from 'to-words';
```

Config Options
```js
const toWords = new ToWords({
  localeCode: 'en-IN',
  converterOptions: {
    currency: true,
    ignoreDecimal: false,
    ignoreZeroCurrency: false,
  }
});
```
Options can be set at instance level, or along with individual call to `convert` method.

```js
const toWords = new ToWords();
let words = toWords.convert(123); // words = One Hundred Twenty Three

words = toWords.convert(123.45); // words = One Hundred Twenty Three Point Fourty Five

words = toWords.convert(123.045); // words = One Hundred Twenty Three Point Zero Four Five
```
*Note: When fractional part starts with zero, the digits after decimal points are converted into respective numbers individually*


To convert to currency

```js
const toWords = new ToWords();
let words = toWords.convert(452, { currency: true }); // words = Four Hundred Fifty Two Rupees Only

words = toWords.convert(452.36, { currency: true }); // words = Four Hundred Fifty Two Rupees And Thirty Six Paise Only

```

To discard fractional unit

```js
const toWords = new ToWords();

let words = toWords.convert(452.36, { currency: true, ignoreDecimal: true }); // words = Four Hundred Fifty Two Rupees Only
```

To ignore major currency number when it's zero

```js
const toWords = new ToWords();

let words = toWords.convert(0.572, { currency: true, ignoreZeroCurrency: true }); // words = Five Hundred Seventy Two Paise Only
```


## Options
| Option  | Type | Default | Description |
| ------------- | ------------- | ------------- | ------------- |
| localeCode | string | 'en-IN' | Locale code for selecting i18n. Currently only `en-IN` & `en-US` are supported. Please open issue / PR if more needed. |
| currency | boolean | false | Whether the number to be converted into words written as currency. *Note: When currency:true, number will be rounded off to two decimals before converting to words* |
| ignoreDecimal | boolean | false | Whether to ignore fractional unit of number while converting into words. |
| ignoreZeroCurrency | boolean | false | Whether to ignore zero currency value while converting into words. |


## Inspiration for core logic
[https://stackoverflow.com/a/46221860](https://stackoverflow.com/a/46221860)
