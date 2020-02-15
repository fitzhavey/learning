# Languages
[back](../)

## Creating recipes:
- a programming language provides a set of primitive operations
- expressions are complex but legal combinations of primitives in a programming language
- expressions and computations have values and meanings in a programming language

## Aspects of languages:

### primitive constructs
- English:
	- words
- programming language:
	- numbers
	- strings
	- simple operators

### syntax
- English:
	- `"cat dog boy"` is not syntactically valid
	- `"cat hugs boy"` is syntactically valid
- programming language:
	- `"hi"5` is not syntactically valid
	- `3.2 * 5` is syntactically valid

### static semantics
Static semantics is which syntactically valid strings actually have a meaning. It means its "put together properly" (i.e. noun, verb, adjective) but semantically does not have meaning.

- English:
	- `"I are hungry"` is syntactically but has a static semantic error
- programming language:
	- `3.2 * 5` is syntactically valid
	- `3 + "hi"` has a static semantic error (except in `js`)

### semantics
Semantics is the meaning associated with a syntactically correct string of symbols with no static semantic errors.

- English (can have many meanings):
	- `"Flying planes can be dangerous"`
	- `"This reading lamp hasn't uttered a word since I bought it?"`
- programming languages have only one meaning, but that may not be what the programmer intended

## Where things go wrong:
- syntactic errors
	- common and easily caught
- static semantic errors
	- some languages check for these before running program
	- can cause unpredicatble behaviour
- no semantic errors but different meaning than what the programmer intended
	- program crashes, stops running
	- programs runs forever
	- program gives an answer but different than expected

## Our goal:
- Learn the syntax and semantics of a programming language.
- Learn how to use those elemnts to translate "recipes" for solving a problem into a form that the computer can use to do the work for us.
- Learn computational modes of thought to enable us to leverage a suite of methods to solve complex problems.