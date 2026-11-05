## branching

```
// if R0 > 0
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


# multiply two numbers

```
@i

M=0

@R2

M=0

  

// if i < R1 go to LOOP

(IF)

@i

D=M

@R1

D=D-M

@END

D;JGE // if i - r1 >= 0

  

(LOOP)

//r2=r0+r2

@R0

D=M

@R2

M=D+M

// i++

@i

M=M+1

  

//REPEAT

@IF

0;JMP

  
  
  

(END)

@END

0;JMP
```

# Blacken the ENTIRE screen
```
// Sets screen to black (8192 words)

  

@8192

D=A

@n

M=D         // n = 8192

  

@i

M=0         // i = 0

  

@SCREEN

D=A

@address

M=D         // address = 16384 (base address of the Hack screen)

  

(LOOP)

    @i

    D=M

    @n

    D=D-M

    @END

    D;JGT    // if i > n goto END

  

    @address

    A=M      // writing to memory using a pointer

    M=-1     // RAM[address] = -1 (16 pixels)

  

    @i

    M=M+1    // i = i + 1

  

    @address

    M=M+1

  

    @LOOP

    0;JMP    // goto LOOP

  

(END)

    @END     // program's end

    0;JMP    // infinite loop
```

# press keyboard and don't

```
  
  

// if D > 0 then write one pixel

// otherwise go te END

(LOOP)

@KBD

D=M

@END

D;JLE

  

@SCREEN

M=-1

  

@LOOP

0;JMP

  

(END)

@END

@SCREEN

M=0

0;JMP
```