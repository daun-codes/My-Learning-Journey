# The Top 10 Instructions that programmers need to know!

I will list all of the top 10 instructions that programmers need to know. This will serve as a reference for those who want to learn more about the 8085 microprocessor and how they can use it in their projects.

## Table

| #   | Instruction | Real-World Analogy                                         | Usage Rate |
| --- | ----------- | ---------------------------------------------------------- | ---------- |
| 1   | MOV         | "Moving data from one location to another"                 | 95%        |
| 2   | MVI         | "Move this value into memory"                              | 90%        |
| 3   | LXI         | "Load the Index Register"                                  | 85%        |
| 4   | ADD/SUB     | "Add/Subtract two values"                                  | 80%        |
| 5   | INR/DCR     | "Increment/Decrement a value"                              | 75%        |
| 6   | JMP/JC/JNC  | "Jump to a specific location"                              | 74%        |
| 7   | CMP         | "Compare two values"                                       | 70%        |
| 8   | LDA/STA     | "Load the Accumulator/Store the Accumulator"               | 70%        |
| 9   | CALL/RET    | "Call a specific location/Return from a specific location" | 70%        |
| 10  | HLT         | "Halt the program"                                         | 100%       |

## What are the top use cases for programmers?

Bellow are the list of the top use cases for programmers. This can give us an idea of how to use the 8085 microprocessor in different scenarios.

### USE CASE 1: COUNTER/LOOP (Repeat a task a certain number of times)

Used in: LED blinking, delays, counting items.

```asm

; COUNT 10 TIMES

MVI C, 0AH          ; Set counter to 10
LOOP: DCR C         ; Decrement counter ( C = C - 1 )
JNZ LOOP            ; Jump to loop if counter is not zero
HLT                 ; Halt the program

```

### USE CASE 2: DATA TRANSFER (Moving data around)

Used in: Copy-pasted data, file transfer.

```asm

; COPY DATA FROM 2000H TO 3000H (copy 5 bytes)

LXI H, 2000H        ; Set source address
LXI D, 3000H        ; Set destination address
MVI C, 05H          ; Set counter to 5

COPY: MOV A, M      ; Move data from source to accumulator
STAX D              ; Store data from accumulator to destination
INX H               ; Increment source address
INX D               ; Increment destination address
DCR C               ; Decrement counter
JNZ COPY            ; Jump to copy if counter is not zero
HLT                 ; Halt the program

```

### USE CASE 3: FIND LARGEST/SMALLEST (Search for extreme values)

Used in: Finding maximum temperature, highest score, etc.

```asm

; FIND THE LARGEST NUMBER AMONG 10 NUMBERS

LXI H, 2000H        ; Set address of first number
MVI C, 09H          ; Set counter to (10 - 1)
MOV A, M            ; Assume first number is the largest


CHECK: INX H        ; Move to next number
CMP M               ; Compare with current largest number
JNC SKIP            ; If A >= [HL], it's still ok
MOV A, M            ; If bigger, that's the new largest


SKIP: DCR C         ; Decrease counter
JNZ CHECK           ; Repeat
STA 2100H           ; Store the largest

HLT


; REAL WORLD: Highest bidder at auction, hottest temperature

```

### USE CASE 4: ARRAY PROCESSING (Processing multiple data)

Used in: Grade computation, sensor arrays

```asm

; ADD ALL 5 NUMBERS (Sum of array)

LXI H, 2000H            ; Pointer to array
MVI C, 05H              ; 5 Numbers
XRA A                   ; A = 0 (Clear Accumulator)


SUM: ADD M              ; A = A + [HL]
INX H                   ; Next number
DCR C                   ; Decrease counter
JNZ SUM                 ; Repeat
STA 2050H               ; Store the total
HLT

```

### USE CASE 5: MULTI-BYTE ARITHMETIC (Large numbers)

Used in: 16-bit/32-bit computations

```asm

; ADD TWO 16-BIT NUMBERS (1234H + 5678H)

; First number: 1234H (store at 2000H=34H, 2001H=12H)
; Second number: 5678H (store at 2010H=78, 2011H=56H)


LXI H, 2000H            ; Low byte of first number
LXI D, 2010H            ; Low byte of second number

LXDAX D                 ; A = low byte of second (78H)
ADD M                   ; Add low byte of first (34H) = ACH
STA 2020H               ; Store low byte of result


INX H                   ; High byte of first (2001H)
INX D                   ; High byte of second (2011H)

LDAX D                  ; A = high byte of second (56H)
ADC m                   ; Add with carry to high byte of first (12H) = 68H + carry
STA 2021H               ; Store high byte of result
HLT

; REAL WORLD: Large money calculations, distance measurements

```

### USE CASE 6: BCD CONVERSION (Decimal numbers)

Used in: Digital displays, 7-segment

```asm

; CONVERT HEXT TO BCD (Decimal adjustment)

MVI A, 48H          ; A = 48 (decimal? 48 or 72?)
MVI B, 37H          ; B = 37 (decimal? 37 or 55?)
ADD B               ; A = 7FH (127 decimal)
DAA                 ; Decimal Adjust = 85H (85 decimal)
STA 2100H           ; Store the correct decimal
HLT

; REAL WORLD:  Calculator, digital clock, ATM machine

```

### USE CASE 7: TABLE LOOKUP (Check a list)

Used in: 7-segment patterns, code conversion

```asm

; GET THE 7-SEGMENT PATTERN FOR NUMBER 5

LXI H, TABLE            ; HL = start of table
MVI A, 05H              ; A = 5 ( the pattern we want)
ADD L                   ; Add to low byte
MOV L, A                ; L = L + 5 (point to 5th entry)
MVI A, 00H
ADC H                   ; H = H + carry
MOV A, M                ; A = pattern for "5"
STA 2200H               ; Store the pattern
HLT


TABLE: DB   3FH,    06H,    5BH,    4FH,    66H,    6DH,    7DH,    07H,    7FH,    6FH
;           0       1       2       3       4       5       6       7       8       9


; REAL WORLD: 7-segment display, character generator


```

### USE CASE 8: DELAY GENERATION (Waiting time)

Used in: LED blinking, timing, keyboard debouncing

```asm

; CREATE APPROXIMATE 1-SECOND DELAY

DELAY:  MVI B, 0FFH         ; Outer Loop counter (255)
OUTER:  MVI C, 0FFH         ; Inner Loop counter (255)
INNER:  DCR C               ; C--
        JNZ INNER           ; Inner Loop until zero
        DCR B               ; B--
        JNZ OUTER           ; Outer Loop until zero
        RET


; REAL WORLD: LED blinking, waiting time, switch debouncing


```

### USE CASE 9: SUBROUTINES (Functions)

Used in: Organized code, reusable functions

```asm

; MAIN PROGRAM

START:  CALL DELAY                  ; Wait
        CALL BEEP                   ; Beep
        CALL DISPLAY                ; Display
        JMP START                   ; Repeat

; SUBROUTINES

DELAY:  MVI B, OFFH                 ; Delay routine
LOOP1:  DCR B
        JNZ LOOP1
        RET

BEEP:   MVI A, 01H                  ; Buzzer on
        OUT 01H
        CALL DELAY                  ; Use same delay
        MVI A, 00H                  ; Buzzer off
        OUT 01H
        RET


DISPLAY:    LXI H, MSG                 ; Display message
            CALL PRINT
            RET

; REAL WORLD: Every organized program!


```

### USE CASE 10: I/O OPERATIONS (Input/Output)

Used in: Sensores, switches, LEDS

```asm

; READ SWITCH, TURN ON LED

CHECK:  IN 00H              ; Read switch (Port 00)
        ANI 01H             ; Check if pressed (bit 0)
        JZ CHECK            ; If not pressed, repeat


        MVI A, O1H          ; Turn on LED
        OUT 01H             ; Send to Port 01

        CALL DELAY          ; Wait

        MVI A, 00H          ; Turn off LED
        OUT 01H
        HLT

; REAL WORLD: Push button, LED indicators, sensor reading


```

## TOP PROGRAMMING PATTERNS

These are the used patterns for the 8085 microprocessor. The patterns are used in different scenarios to perform specific tasks.

### Pattern 1: INITIALIZATION (Setup)

```asm

LXI H, 2000H        ; Set memory pointer
MVI C, 0AH          ; Set counter
XRA A               ; Clear accumulator
MVI B, OOH          ; Clear B register


```

### Pattern 2: LOOP (Repeat)

```asm

LOOP:   [do something here]
        DCR C
        JNZ LOOP

```

### Pattern 3: IF-THEN-ELSE (Conditional)

```asm

CPI 05H             ; Compare with 5
JZ EQUAL            ; If equal
JNZ NOT_EQUAL       ; If not equal

EQUAL: [if it's 5]

```

### Pattern 4: ARRAY ACCESS (List)

```asm

LXI H, ARRAY            ; Pointer to array
MOV A, M                ; Get first element
INX H                   ; Move to second
MOV B, M                ; Get second


```

### Pattern 5: STORE RESULT (Save)

```asm

STA 3000H               ; Store A
SHLD 3001H              ; Store HL


```

## CHEAT SHEET - MOST COMMON USED INSTRUCTIONS

| Instruction | What it's for                          | Example      |
| ----------- | -------------------------------------- | ------------ |
| MOV         | Move data from one location to another | MOV A, B     |
| MVI         | Move this value into memory            | MVI A, 0FFH  |
| LXI         | Load the Index Register                | LXI H, 2000H |
| ADD         | Add two values                         | ADD B        |
| SUB         | Subtract two values                    | SUB B        |
| INX         | Increment the Index Register           | INX H        |
| DCR         | Decrement a value                      | DCR C        |
| CMP         | Compare two values                     | CMP B        |
| LDA         | Load the Accumulator                   | LDA 2000H    |
| STA         | Store the Accumulator                  | STA 2000H    |
| CALL        | Call a specific location               | CALL 2000H   |
| RET         | Return from a specific location        | RET          |
| HLT         | Halt the program                       | HLT          |

## References

- [Learn8085.com - 8085 Assembly Language](https://www.learn8085.com/8085-assembly-language/)
- [8085.org - 8085 Assembly Language](http://8085.org/8085-assembly-language/)
