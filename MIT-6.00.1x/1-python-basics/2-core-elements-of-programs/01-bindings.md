_[Home](../../../) / [MIT 6.00.1x](../../) / [1 - Python Basics](../) / [2 - Core Elements of Programs](./) / 1 - Bindings_
# Bindings

## Variables (revisited)
Variables have two defining properties, a **name** and a **value**.
- name:
	- descriptive
	- meaningful
	- helps you re-read code
	- cannot be keywords

- value:
	- information stored
	- can be updated

## Variable binding with `=`
- compute the **right hand side**: **value**
- store it (same as binding) in the **left hand side**: **variable**
- left hand side will be replaced with the new value
- use of `=` is called assignment

## Binding Example
Is swapping variables ok?
```
x = 1
y = 2
y = x
x = y
```
The above won't work as the order matters. Instead do:
```
x = 1
y = 2
temp = y
y = x
x = temp
```