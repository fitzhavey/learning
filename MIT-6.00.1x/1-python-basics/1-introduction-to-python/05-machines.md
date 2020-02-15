# Machines
[back](../)

## Computers are machines
How to capture a recipe in a mechanical process?
- fixed program computer
	- calculator
	- Alan Turing's Bombe
- stored program computer
	- machine stores and executes instruction

## Basic machine architecture
- inputs and outputs
- memory containing data
- arithmetic logic unit, to do primitive operations
- control unit, acts as a program counter

Ther program counter tells the control unit which instruction to read from memory. It then increments the counter and sends that instruction the the arithmetic logic unit.

## Stored Program Computer:
- sequestion of instructions stored inside the computer, built from a set of primitive instructions:
	- arithmetic and logic
	- simple tests
	- moving data
- special program (interpreter) executes each instruction in order
	- use tests to change flow of control through sequence
	- stop when done

## Basic Primitives:
- Turing showed that you can compute anything using 6 primitives
- modern programming languages have a more convenient set of primitives
- we can abstract methods to create new primitives
- anything computable in one programming language is computable in any other programming language.