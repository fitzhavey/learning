# Knowledge

## Types of knowledge:
- computers know what you tell them
- **declarative knowledge** is statements of fact
	- "there is candy tapes to the underside of one chair"
- **imperative knowledge** is a recipe or "how-to" computation
	1. face the students in the front of the room
	2. count up 3 rows
	3. start from the middle section's left side
	4. count to the right 1 chair
	5. reach under and find it

## A numerical example:
- square root of a number `x` is `y` such that `y * y = x`
- recipe for deducing square root of number `x` (e.g. 16):
	1. start with a guess, `g`
	2. if `g * g` is close enough to `x`, stop and say `g` is the answer
	3. otherwise make a new guess by averaging `g` and `x / g`
	4. using the new guess, repeat process until close enough

	| `g`   | `g * g` | `x / g` | `(g + (x / g)) / 2` |
	|-------|---------|---------|---------------------|
	| 3     | 9       | 5.333   | 4.167               |
	| 4.167 | 17.364  | 3.837   | 4.004               |
	| 4.004 | 16.028  | 3.887   | 4.000002            |

## So what is a recpe?
1. sequence of simple steps
2. flow of control process that specifies when each step is executed
3. a means of determining when to stop

Steps 1+2+3 = an algorithm!