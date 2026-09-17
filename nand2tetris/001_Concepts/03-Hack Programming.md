## Label

```
Sigmum.asm

if R0 > 0
	R1 = 1
else 
	R1 = 0
	

@R0
D=M

@POSITIVE
D;JGT

@R1
M=0

@END
0;JMP

(POSITIVE)
@R1
M=1

(END)
@END
0;JMP


```

## Variable

```
temp = R1
R1 = R0
R0 = temp


@R1
D=M
@temp
M=D // temp = R1


@R0
D=M
@R1
M=D // R1 = R0

@temp
D=M
@R0
M=D

```

## Iterating Processing
its just kind of loop so ...
## Pointers

```
for (i=0; i<n; i++)
	arr[i] = -1;
	

// Suppose arr = 100 and n = 10
// arr = 100
@100
D=A
@arr
M=D

// n = 10
@10
D=A
@n
M=D

// i = 0
@i
M=0

(LOOP)

// if (i == n) goto END
@i
D=M
@n
D=D-M
@END
D;JEQ

// RAM[arr+i] = -1
@arr
D=M
@i
A=D+M
M=-1

// i++
@i
M=M+1

@LOOP
0;JMP

(END)
@END
0;JMP

```


