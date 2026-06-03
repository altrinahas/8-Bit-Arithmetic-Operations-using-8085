# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.
Apparatus Required:
•	Laptop with internet connection
## Algorithm:
## For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
## For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.
## For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).
## For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.
## Program:

```asm
; ---------- ADDITION ----------
LDA 4150H
MOV B,A
LDA 4151H
ADD B
STA 4152H

; ---------- SUBTRACTION ----------
LDA 4150H
MOV B,A
LDA 4151H
MOV C,A
MOV A,B
SUB C
STA 4153H

; ---------- MULTIPLICATION ----------
MVI A,00H
MVI D,00H
LXI H,0020H
MOV B,M
INX H
MOV C,M
MUL_LOOP: ADD B
JNC NO_CARRY
INR D
NO_CARRY: DCR C
JNZ MUL_LOOP
STA 0022H
MOV A,D
STA 0023H

; ---------- DIVISION ----------
LXI H,0020H
MOV A,M
INX H
MOV C,M
MVI D,00H
DIV_LOOP: CMP C
JC DIV_END
SUB C
INR D
JMP DIV_LOOP
DIV_END: STA 0025H
MOV A,D
STA 0024H

HLT
```
## Output:
<img width="679" height="348" alt="image" src="https://github.com/user-attachments/assets/7260de84-425f-459d-9dd2-2c8efc7e90ba" />
<img width="663" height="311" alt="image" src="https://github.com/user-attachments/assets/c86bc409-b143-4527-82cb-a556c2b2dad9" />
<img width="664" height="308" alt="image" src="https://github.com/user-attachments/assets/af9aad02-282d-44c0-a6aa-a10c75992028" />
<img width="662" height="315" alt="image" src="https://github.com/user-attachments/assets/6a1c55f2-9ec1-4434-aae2-5b1032cac3bc" />


## ➤ Final Output Summary  

| Operation       | Input (Example) | Result (Hex) | Result (Decimal) |
|-----------------|-----------------|--------------|------------------|
| Addition        | 10, 2           | 0CH          | 12               |
| Subtraction     | 10, 2           | 08H          | 8                |
| Multiplication  | 10 × 2          | 14H          | 20               |
| Division        | 10 ÷ 2          | 05H / 00H    | 5 Quotient / 0 Remainder |
## Result:

The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
