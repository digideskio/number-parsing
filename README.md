# number-parsing [![Build Status](https://travis-ci.org/GuillaumeLeclerc/numberParsing.svg?branch=master)](https://travis-ci.org/GuillaumeLeclerc/numberParsing)

When you are receiving data from all over the world you might encounter problems while using `parseFloat` or `parseInt`. This libraray is here to help you handling all locales with one single piece of code.

## Install

just run `npm install number-parsing`

## Usage

```javascript 
var parser = require("number-parsing");
var a = parser("123'123.99USD"); // will return 123123.99
var b = parser("1234"); // will return 1234
var c = parser("123 123,777") // will return 123123.777
// and so on
```

## Resolve ambiguities
Some notations are ambiguous. For example if you receive '123,123'. You have no clue if it means `123.123` or `123123`. If you are dealing with strange locales which uses `,` as a thousand delimiter, then you might want to specify the afinity of the parser for some locale.
```javascript
var parser = require("number-parsing");
var a = parser("123,123", {
	us : 0.75
	fr  : 0.25
} // will return 123123
var a = parser("123,123", {
	fr : 0.75
	us  : 0.25
} // will return 123.123
```

## Building the tool from sources

Just run `grunt build`

## Run unit tests

Just run `grunt test`


## Contribute

Feel free to add more formats `./formats.coffee` or add new tests (in the directory `test/`)
You can also make suggestion about the main algorithm
