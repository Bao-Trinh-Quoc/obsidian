---
tags:
type: concept
---
# [[Name of Concept]]

## Summary

**A formalism for accessing and manipulating registers**

## Key Details
- **CPU resident** registers (few, accessed directly by name) vs **Memory-resident** registers (many, accessed by address)
- Kind of registers:
	- data
	- address
	- instruction

![[Pasted image 20260630215604.png]]


## Program translation
![[Pasted image 20260929213522.png]]

## Machine Language: Elements

### Operations
- Usually correspond to what's implemented in Hardware
- **Differences** between machine languages.

### Registers
Memory Hierachy
![[Pasted image 20261002220143.png]]


few, easily accessed "registers"
**central** part of the machine lang.

- **Data registers**
	- Add R1, R2
- **Address registers**
	- Store R1, @A
### Input/Output
- CPU need protocols to talk to the mouse, the keyboard
- "memory mapping"
### Flow control
- usually in sequence **BUT**
- sometimes we need to **JUMP**