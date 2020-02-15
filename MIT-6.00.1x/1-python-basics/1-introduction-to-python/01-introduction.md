# Introduction to Python
[back](./)

## Overview of course:
- learn computational modes of thinking
- master the art of computational problem solving
- make computers do what you want them to

## Topics:
- represent knowledge with data structures
- iteration and recursion as computational metaphors
- abstraction of procedures and data types
- organize and modularize systems using object classes and methods
- different classes of algorithms, searching and sorting
- complexity of algorithms

## What does a computer do?
- Fundamentally:
	- performs calculations
	- remembers results
- What kinds of calculations?
	- built-in to the language
	- ones that you define as a programmer

## Are simple calculations enough?
- Searching the World Wide Web
	- 45 Billion pages; 1000 words / page; 10 operations / word to find
	- need 5.2 days to find something using simple operations
- Playing chess
	- average 35 moves / setting; look ahead 6 moves; 1.8 Billion boards to check; 100 operations / choice
	- 30 minutes to decide each move

So good algorithm design is also needed to accomplish a task!

## Enough storage?
What if we could just pre-compute information and then look up the answer?

Playing chess as an example:
- experts suggest 10^123 different possible games
- only 10^80 atoms in the observable universe

So there is not enough storage to precompute everything.

## Are there limits?
Despite its speed and size, a computer does have limitations.
- Some problems are still too complex
	- accurate weather prediction at a local scales
	- cracking encryption schemes
- Some problems are fundamentally impossible to computer
	- predicting whether a piece of code will always halt with an answer for any input