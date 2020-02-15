# Variables
[back](./)

## Binding variables and values
- equal sign is an **assignment** of a value to a variable name
	```
	pi = 3.14159
	pi_approx = 22 / 7
	```
- value stored in computer memory
- an assignment binds name to value
- retrieve value associated with name or variable by invoking the name, by typing `pi`
	```
	pi
	# 3.14159
	```

## Abstracting expressions
Why give names to values of expressions?
- reuse names instead of values
- easier to change code later
	```
	pi = 3.14159
	radius = 2.2
	area = pi * (radius ** 2)

	area
	# 15.205295600000001
	```

## Programming vs Math
In programming, you do not "solve for x", so adding the following line to the above code block, will not change the value of `area`:
```
radius = radius + 1
```
_This could also be written as `radius += 1`_

## Changing bindings
- can re-bind variable names using new assignment statements
- previous value may still be stored in memory but lost the reference to it
- value for `area` did not change and won't until we tell the computer to do the calculation again