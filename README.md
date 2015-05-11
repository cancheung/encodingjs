# golang-encodingjs
A JavaScript Unmarshaler for the Go language

[![Build Status](https://travis-ci.org/martint17r/encodingjs.svg)](https://travis-ci.org/martint17r/encodingjs)
[![Coverage Status](https://coveralls.io/repos/martint17r/encodingjs/badge.svg)](https://coveralls.io/r/martint17r/encodingjs)

## Usage

encodingjs.Unmarshal works similar to json.Unmarshal - pass the result of the JavaScript
evaluation from otto and a reference to the target structure.

```
vm := otto.New()
jsresult, err := vm.Run(`a={Foo: "bar", Fubar:"bob"}; a`)
if err != nil {
	panic(err)
}
result := struct {
	Foo   string
	Fubar string
}{}
err= encodingjs.Unmarshal(jsresult, &result)
if err != nil {
	panic(err)
}
fmt.Printf("%+v\n", result)
// Output: {Foo:bar Fubar:bob}
```

## Shortcomings

error path from otto is untested - I have not found a way to trigger these.
