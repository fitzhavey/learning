_[Home](../../../) / [MIT 6.00.1x](../../) / [1 - Python Basics](../) / [1 - Introduction to Python](./) / 14 - Operators and Branching_
# Operators and Branching

## Comparison operators on `int` and `float`:
- `i > j`
- `i >= j`
- `i < j`
- `i <= j`
- `i == j`: **equality** test, `True` if `i` equals `j`
- `i != j`: **inequality** test, `True` if `i` not equal to `j`

## Branching programs:
The simplest branching statement is a **conditional**
- a test (expression that evaluates to `True` or `False`)
- a block of code to execute if the test is `True`
- an optional block of code to execute if the test is `False`

## A simple example:
```
x = int((input('Enter an integer'))
if x % 2 == 0:
	print('Even')
else:
	print('Odd')
print('Done with conditional')
```

## Some observations:
- The expression `x % 2 == 0` evaluates to `True` when the remainder of `x` divided by `2` is `0`.
- Note that `==` is used for comparison, since `=` is reserved for assignment.
- The indentation is importan as each indented set of expressions denotes a block of instructions
	- for example, if the last statement in the code block above was indented, it would be executed inside the `else` block of the code
- Note how this indentation provides a visual structure that reflects the semantic structure of the program.

## Compound booleans:
```
if x < y and y < z:
	print('x is least')
elif y < z:
	print('y is least')
else:
	print('z' is least')
```

## Control Flow - Branching:
- `<condition>` has value `True` or `False`
- evaluates expressions in that block if `<condition>` is `True`
```
if <condition>:
	<expression>
	...
```
or
```
if <condition>:
	<expression>
	...
else:
	<expression>
	...
```
or
```
if <condition>:
	<expression>
	...
elif <condition>:
	<expression>
	...
else:
	<expression>
	...
```

## Indentation:
- matters in Python
- how you denote blocks of code
```
x = float(input('Enter a number for x: '))
y = float(input('Enter a number for y: '))
if x == y:
	print('x and y are equal')
	if y != 0:
		print('therefore, x / y is', x / y)
		# x / y will always be 1
elif x < y:
	print('x is smaller')
else:
	print('y is smaller')
print('thanks!')
```

## What have we added?
- Branching programs allow us to make choices and do different things.
- But stil the case that at most, each statement gets executes once
- So maximum time to run the program depends only on the length of the program
- These programs run in **constant time**

We'll expand past linear programs later in this course.