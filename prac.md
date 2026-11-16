# To find whether the first number is greater than, equal to, or smaller than the second number.
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM1 DB 10H
    NUM2 DB 20H   
    
    MSG1 DB 'First Number is Greater$'
    MSG2 DB 'Both Numbers are Equal$'
    MSG3 DB 'First Number is Smaller$'
    
.CODE
MAIN PROC
    MOV AX,@DATA
    MOV DS,AX
    MOV ES,AX
    
    MOV AL,NUM1
    MOV BL,NUM2   
    CMP AL,BL
    
    JE EQUAL
    JG GEATER
    JL LESS
    
    GEATER:
        LEA DX,MSG1 
        MOV AH, 09H
        INT 21H
        JMP EXIT    
   
    EQUAL:
        LEA DX,MSG2
        MOV AH,09H
        INT 21H
        JMP EXIT
   
    LESS:
        LEA DX,MSG3
        MOV AH,09H
        INT 21H
        JMP EXIT
    
    EXIT:
        MOV AH,4CH
        INT 21H
MAIN ENDP
END MAIN   -->
               
# Find the Smallest Number Among Three Numbers
<!-- .MODEL SMALL
.STACK 100H
.DATA
    NUM1 DB 35H
    NUM2 DB 15H
    NUM3 DB 25H

    MSG1 DB 'NUMBER 1 IS SMALLEST$'
    MSG2 DB 'NUMBER 2 IS SMALLEST$'
    MSG3 DB 'NUMBER 3 IS SMALLEST$'

.CODE
MAIN PROC

    MOV AX,@DATA
    MOV DS,AX

    MOV AL,NUM1
    MOV BL,NUM2

    CMP AL,BL
    JL CHECK3
    MOV AL,BL

CHECK3:
    MOV BL,NUM3
    CMP AL,BL
    JL NUMBER1
    JG NUMBER3

    ; If equal, AL and NUM3 are equal.
    JMP NUMBER1

NUMBER1:
    LEA DX,MSG1
    MOV AH,09H
    INT 21H
    JMP EXIT

NUMBER3:
    LEA DX,MSG3
    MOV AH,09H
    INT 21H
    JMP EXIT

EXIT:
    MOV AH,4CH
    INT 21H

MAIN ENDP
END MAIN -->

# Find the Largest Number Among Three Numbers
<!-- .MODEL SMALL
.STACK 100H
.DATA
    NUM1 DB 25H
    NUM2 DB 35H
    NUM3 DB 33H
    
    MSG1 DB 'NUMBER 1 IS BIG$'
    MSG2 DB 'NUMBER 2 IS BIG$'
    MSG3 DB 'NUMBER 3 IS BIG$'
    
.CODE
MAIN PROC
    MOV AX,@DATA
    MOV DS,AX
    MOV ES,AX
    
    MOV AL,NUM1
    MOV BL,NUM2
    CMP AL,BL
    JG CHECK   
    MOV AL, BL
    
    CHECK:
        MOV BL, NUM3
        CMP AL,BL
        JG RESULT
        MOV AL,BL  
    
    RESULT:
        CMP AL,NUM1
        JE NUM1M
        
        CMP AL,NUM2
        JE NUM2M
        
        CMP AL,NUM3
        JE NUM3M
        
    NUM1M:
        LEA DX,MSG1
        MOV AH,09H
        
        INT 21H
        JMP EXIT   
    NUM2M:
        LEA DX,MSG2
        MOV AH,09H
        
        INT 21H
        JMP EXIT    
        
    NUM3M:
        LEA DX,MSG3
        MOV AH,09H
        
        INT 21H
        JMP EXIT
        
    EXIT:
        MOV AH,4CH
        INT 21H    
MAIN ENDP
END MAIN -->

# EVEN ODD
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM1 DB 36H
    
    MSG1 DB 'THIS NMBR IS EVEN$'
    MSG2 DB 'THIS NMBR IS ODD$'
    
.CODE
MAIN PROC
    MOV AX,@DATA
    MOV DS,AX
    
    MOV AL,NUM1
    AND AL,01H
    JZ EVEN
    
    ODD:
        LEA DX,MSG2
        MOV AH,09H
        INT 21H
        JMP EXIT
    EVEN:
        LEA DX,MSG1
        MOV AH,09H
        INT 21H
        JMP EXIT
    EXIT:  
        MOV AH,4CH
        INT 21H
MAIN ENDP
END MAIN -->

# POSITIVE NEGATIVE ZERO
<!-- .MODEL SMALL
.STACK 100H    

.DATA
    NUM1 DB 34H  
    CHECK DB 0H
    
    MSG1 DB 'THIS IS POSITIVE NUMBER$' 
    MSG2 DB 'THIS IS NEGATIVE NUMBER$'
    MSG3 DB 'THIS IS ZERO$'     
    
    
.CODE
MAIN PROC
    MOV AX,@DATA
    MOV DS,AX
    
    MOV AL,NUM1
    MOV BL,CHECK
    
    CMP AL,BL
    JG POSITIVE
    JL NEGATIVE
    JE ZERO
    
    POSITIVE:
        LEA DX,MSG1
        MOV AH,09H
        INT 21H
        JMP EXIT    
    NEGATIVE:
        LEA DX,MSG2
        MOV AH,09H
        INT 21H
        JMP EXIT 
    ZERO:
        LEA DX,MSG3
        MOV AH,09H
        INT 21H
        JMP EXIT 
    
    EXIT:  
        MOV AH,4CH
        INT 21H
MAIN ENDP
END MAIN -->

# 2TA NMBR ADD KORSI
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM1 DB 25H
    NUM2 DB 15H
    RESULT DB ?

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV AL, NUM1
    ADD AL, NUM2

    MOV RESULT, AL

    MOV AH, 4CH
    INT 21H
MAIN ENDP
END MAIN -->

# 2TA NMBR SUB KORSI
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM1 DB 36H
    NUM2 DB 15H
    RESULT DB ?

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV AL, NUM1
    SUB AL, NUM2

    MOV RESULT, AL

    MOV AH, 4CH
    INT 21H
MAIN ENDP
END MAIN -->

!user input

<!-- .MODEL SMALL
.STACK 100H

.DATA
    MSG1 DB 'ENTER FIRST NUMBER: $'
    MSG2 DB 0DH,0AH,'ENTER SECOND NUMBER: $'
    MSG3 DB 0DH,0AH,'SUBTRACTION RESULT: $'

    NUM1 DW ?
    NUM2 DW ?
    RESULT DW ?

.CODE
MAIN PROC
    MOV AX,@DATA
    MOV DS,AX

    ; First Number Input
    LEA DX,MSG1
    MOV AH,09H
    INT 21H

    CALL INPUT
    MOV NUM1,AX

    ; Second Number Input
    LEA DX,MSG2
    MOV AH,09H
    INT 21H

    CALL INPUT
    MOV NUM2,AX

    ; Subtraction
    MOV AX,NUM1
    SUB AX,NUM2
    MOV RESULT,AX

    ; Display Result
    LEA DX,MSG3
    MOV AH,09H
    INT 21H

    MOV AX,RESULT
    CALL DISPLAY

    ; Exit
    MOV AH,4CH
    INT 21H

; =================================
; INPUT PROCEDURE (4 DIGIT)
; =================================

INPUT PROC
    XOR BX,BX

READ:
    MOV AH,01H
    INT 21H

    CMP AL,0DH
    JE DONE

    SUB AL,30H
    MOV CL,AL

    MOV AX,BX
    MOV DX,10
    MUL DX

    XOR CH,CH
    MOV BL,CL
    XOR BH,BH
    ADD AX,BX
    MOV BX,AX

    JMP READ

DONE:
    MOV AX,BX
    RET
INPUT ENDP

; =================================
; DISPLAY PROCEDURE
; =================================

DISPLAY PROC
    MOV BX,10
    XOR CX,CX

CONVERT:
    XOR DX,DX
    DIV BX
    PUSH DX
    INC CX

    CMP AX,0
    JNE CONVERT

PRINT:
    POP DX
    ADD DL,30H
    MOV AH,02H
    INT 21H
    LOOP PRINT

    RET
DISPLAY ENDP

MAIN ENDP
END MAIN -->

# FACTORIAL
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM DB 5
    RESULT DW ?

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV CL, NUM
    MOV AX, 1

    FACT:
        MUL CL
        DEC CL
        JNZ FACT

    MOV RESULT, AX

    MOV AH, 4CH
    INT 21H

MAIN ENDP
END MAIN -->

# ADD N NUMBER
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM DB 10
    
.CODE
MAIN PROC
    MOV AX,@DATA
    MOV DS,AX
    
    MOV AL,NUM
    MOV BL,0
    
    FACT:
        ADD BL,AL
        DEC AL
        JNZ FACT
        
    MOV DL,BL
    
    MOV AH,4CH
    INT 21H
MAIN ENDP
END MAIN -->

# MUL / DIV
<!-- .MODEL SMALL
.STACK 100H

.DATA
    NUM1 DB 05H
    NUM2 DB 04H
    RESULT DW ?

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV AL, NUM1
    MOV CL, NUM2

    MUL CL

    MOV RESULT, AX

    MOV AH, 4CH
    INT 21H

MAIN ENDP
END MAIN

.MODEL SMALL
.STACK 100H
.DATA
    NUM1 DB 20H
    NUM2 DB 04H

    QUOTIENT DB ?
    REMAINDER DB ?

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV AL, NUM1
    MOV AH, 00H

    MOV CL, NUM2

    DIV CL

    MOV QUOTIENT, AL
    MOV REMAINDER, AH

    MOV AH, 4CH
    INT 21H

MAIN ENDP
END MAIN -->

# write an assembly language program to add a data byte located at offset0500h in the 2000h segment to another data byte at 0600h in the same segment and store the result at 0700h
<!-- .MODEL SMALL
.STACK 100H

.CODE
MAIN PROC

    MOV AX, 2000H
    MOV DS, AX

    MOV SI, 0500H
    MOV AL, [SI]

    MOV SI, 0600H
    ADD AL, [SI]

    MOV SI, 0700H
    MOV [SI], AL

    MOV AH, 4CH
    INT 21H

MAIN ENDP
END MAIN -->

