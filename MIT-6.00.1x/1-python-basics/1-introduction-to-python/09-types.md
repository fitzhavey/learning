# Types

## Python Programs
- a program is a sequence of definitions and commands
	- definitions are evaluated
	- commands are executed by Python interpreter in a shell
- commands (statements) instructer interpreter to do something
- can be typed directly into a shell or stored in a file that is read into the shell and evaluated

## Objects
- programs manipulate data objects
- objects have a type that defines the kinds of things programs can do to them
- objects are either:
	- scalar (cannot be subdivided)
	- non-scalar (have internal structure that can be accesed)

## Scalar Objects
- `int` - represent **integers**, e.g. `5`
- `float` - represent **real numbers**, e.g. `3.27`
- `bool` - represent **boolean** values `True` and `False`
- `NoneType` - **special** and only has one value: `None`
- can use `type()` to see the type of an object
	```
	type(5)
	# "int"

	type(3.0)
	# "float"
	```

## Type Conversions (cast)
- can convert an object of one type to another
- `float(3)` converts integer `3` to float `3.0`
- `int(3.9)` truncates float `3.9` to integer `3`

## Printing to console
To show output from code to a user, use the `print()` command
```
> print(3 + 2)
5
```

## Expressions
- combine objects and operators to form expressions
- an expression has a value, which has a type
- syntax for a simple expression:
	- `<object> <operator> <object>`

## Operators on `ints` and `floats`:
- `i + j`: the **sum**
- `i - j`: the **difference**
- `i * j`: the **product**
- `i / j`: **division**, where the result is a `float`
- `i // j`: **int division**, where the result is an `int`, quotient without the remainder
- `i % j`: the **remainder** when `i` is divided by `j`
- `i ** j`: `i` to the **power** of `j`

## Simple operations
- parentheses used to tell Python to do these operations first
	- `3 * 5 + 1` evaluates to `16`
	- `3 * (5 + 1)` evaluates to `18`
- operator precedence without parentheses:
	1. `**`
	2. `*`
	3. `/`
	4. `+` and `-`
	- executed left to right, as they appear in the expression