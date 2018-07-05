# Object Iteration

## Problem Statement

After learning about collections (`Array`, `Object`), it's very common to need
to be able to do some activity for each element in the collection. For each
evil wizard, disarm them! For each wedding guest, invite them. Yet the `for`
loop is our only tool:

```js
for (let i = 0; i < array.length; i++) {
  // Loop body
}
```

ES2015 introduced a simpler way to express this common path. For `Array`s we
now have `for...of` and for Objects we now have `for...`in`.

## Objectives

1. Define iteration
2. Discuss the Problem of Expressivity with `for` Loops
3. Iterate over `Array`s with the `for...of` statement.
4. Iterate over `Sting`s with the `for...of` statement.
6. Enumerate an object's properties with the `for...in` statement.

## Define Iteration

Iteration is doing something again and again "for each" element in the
collection.

> **WORD ORIGIN NOTE** If word origins help you remember things, _iterum_ means
> "again." So "iteration" is "again-ation:" expect something to happen again
> and again!

## Discuss the Problem of Expressivity with `for` Loops

So what's wrong with `for` loops? They allowed us to iterate too, after all.
The problem is that they aren't very _expressive_. You might have heard this
term used when talking about HTML.

If you saw a newspaper and in big letters at the top it said "MANKIND WALKS ON
MOON," you, a human, would have no problem recognizing it as a header. But in
an HTML file, a browser couldn't know the same thing.  That's one of the reasons
we "mark up" content in the HyperText Markup Language (HTML). It lets us
document the _purpose_ of the text. With HTML we can be more _expressive_ than
with plain text.

Let's consider code where `harryPotter` performs _expelliarmus_ on each member
of `slytherins`.

```javascript
for (let i = 0; i < slytherins.count; i = i + 1) {
  harryPotter.expelliarmus(slytherins[i]);
}
```

Much like marking up content into HTML, programmers can infer that the goal is
to iterate a collecton, but we'd like to use code that screams "HEY WE ARE
ITERATING A COLLECTION IN ORDER HERE!." The more _expessive_, in-order way to
travel a `String` or `Array` is a `for...of` loop.

## `for...of`

ES2015 introduced the `for...of` statement. It's one and only function is to
iterate members of `Array`s.

```js

const slytherins = ["Salazar Slytherin", "Bellatrix Black", "Draco Malfoy"];

for (const snakeyWizard of slytherins) {
  harryPotter.expelliarmus(snakeyWizard);
}
```

It's much cleaner than the `for` loop:

* No three-part declaration divided by `;` to memorize
* No initialization of a counter
* No condition
* No incrementing the counter
* No bracket notation to access elements in the array (`myArray[i]`).

## Iterate Over `String`s With The `for...of` Statement.

A `String` is effectively an ordered collection (an Array) of characters. The
`for...of` is the right iterator here as well.

```js
for (const char of 'Hello, world!') {
  console.log(char);
}

// LOG: H
// LOG: e
// LOG: l
// LOG: ...and so on...
```

## Enumerate An Object's Properties With The `for...in` Statement.

The `for...in` statement is used for iterating over the properties or "keys"
in an object. The statement follows this syntax:

```js
for (const <KEY> in <OBJECT>) {
  // Code in the statement body
}
```

The `for...in` statement iterates over the properties in an object, but it
doesn't pass the entire property into the block. Instead, it only passes in the
_key_:

```js
const address = {
  street1: '11 Broadway',
  street2: '2nd Floor',
  city: 'New York',
  state: 'NY',
  zipCode: 10004
};

for (const key in address) {
    console.log(key);
}

// LOG: street1
// LOG: street2
// LOG: city
// LOG: state
// LOG: zipCode
```

Use the passed-in key with the _bracket operator_ to get the value of the key
in the `Object` back out:

```js
const address = {
  street1: '11 Broadway',
  street2: '2nd Floor',
  city: 'New York',
  state: 'NY',
  zipCode: 10004
};

for (const key in address) {
  console.log(address[key]);
}

// LOG: 11 Broadway
// LOG: 2nd Floor
// LOG: New York
// LOG: NY
// LOG: 10004
```

### `for...in` and order

As a general rule, **don't use `for...in` with `array`s**. When iterating over
an `Array`, an **ordered** collection, we would expect the elements in the
`Array` to be dealt with **in order**. However, because of how `for...in` works
under the hood, there's no guarantee of order. From the [MDN
documentation][for...in]:

>A `for...in` loop iterates over the properties of an object in an **arbitrary
>order** ... one cannot depend on the seeming orderliness of iteration, at
>least in a cross-browser setting).

## Conclusion

You've now learned a more expressive way to iterate through collection where
order matters (`Array`, `String`): `for...of`. You've also learned an
expressive way to iterate through the an `Object`: `for...in`

## Resources

- [MDN — `for...of`][for...of]
- [MDN — `for...in`][for...in]

[for...of]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of
[for...in]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in
