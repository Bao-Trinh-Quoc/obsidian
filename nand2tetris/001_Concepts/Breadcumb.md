

# 14/10/2026

finish input ouput learn rly coothign called screen memory map / keyboard memory map 

finishi the first part of hack programming trick, mostly about assign soem address and then a convention to use Rx from x to 15 when we want to access the register at that numbe iirc. 

btw, nice work.

# 28/10/2026

stop at fill.asm

# 5/11/2026

can just blacken the screen while pressing anykey, 
cannot clear the screen when press nothing yet

// Sets screen to black (8192 words)

  

@8192

D=A

@n

M=D         // n = 819

@SCREEN

D=A

@address

M=D         // address = 16384 (base address of the Hack screen)

  
  

(LOOP)

@KBD

D=M

@END

D;JLE

// blacken the entire screen

    (LOOP1)

    @i

    M=0         // i = 0

    @i

    D=M

    @n

    D=D-M

    @LOOP

    D;JGT    // if i > n goto outer LOOP

  

    @address

    A=M      // writing to memory using a pointer

    M=-1     // RAM[address] = -1 (16 pixels)

  

    @i

    M=M+1    // i = i + 1

  

    @address

    M=M+1

  

    @LOOP1

    0;JMP

  

@LOOP

0;JMP

  
  
  

(END)

@KBD

D=M

@LOOP

D;JGT

@END

0;JMP
