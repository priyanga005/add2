; Assume BUFFER_1, BUFFER_2, and BUFFER_3 are predefined memory locations
; Each buffer holds 100 samples of signal data

MOV     R0, #BUFFER_1       ; Load the address of BUFFER_1 into R0
MOV     R1, #BUFFER_2       ; Load the address of BUFFER_2 into R1
MOV     R2, #BUFFER_3       ; Load the address of BUFFER_3 into R2
MOV     R3, #0              ; Initialize index register (R3 = 0)

LOOP:
    LDR     R4, [R0, R3]    ; Load value from BUFFER_1 at index R3 into R4 (indirect addressing)
    LDR     R5, [R1, R3]    ; Load value from BUFFER_2 at index R3 into R5 (indirect addressing)
    ADD     R6, R4, R5      ; Add R4 and R5, result in R6
    STR     R6, [R2, R3]    ; Store the result into BUFFER_3 at index R3 (indirect addressing)

    ADD     R3, R3, #1      ; Increment the index (R3)
    CMP     R3, #100        ; Compare index with 100 (end of buffer)
    BLT     LOOP            ; If index < 100, repeat the loop

; End of the program
