##General Prupose Registers
AX- The accumulator register
	Divided into AH and AL
BX - The base address register
	Divided into BH and BL
CX - The count register 
	Divided into CH and CL
DC - The data Register
	Divided into DH and DL
SI - source index register
DL - Destination index Register
BP - Base Pointer
SP - Stack Pointer
#FIRST 4 Registers (AX, BX, CX, DX)
Made of two separate 8 bit registers
	Example[1]
		AX can be represented as
		AX=AH+AL BX=BH+BL
		AX(16bit)=AH(8bit)+AL(8bit)
	Example[1.1]
		AX= 00110000 00111001b
		AH = 00110000b
		AL = 00111001b


##Segment Registers
CS - Points at the segment containing the current program
DS - Generally Points at segment where variables are defined
ES - Extra segment register, its up to a coder to devine its usage
SS - Points at the segment containing the Stack

##Types and Variables
DB (Define Byte)
DW (Define Word)
DD (Define Doubleword)
DQ (Define Quadword)

EXAMPLE[1]
VAR_NAME TYPE VALUE
A DB 9
MESSAGE DB 'HELLOWROLD'

VAR DW 1122H

VAR = Variable name
DW = Define Word
1122H = Allocation amount

#String in Assembly Language
Example String [1] = STR1 DB "Hello World"
Example String [1] = STR2 DB "Hello World",'$'  //$ For End Of String
Example String [1] = STR3 DB 10,13,"Hello World",'$'  //10,13 For New Line

##Arrays In 8086
Name Type Value
a DB 1h,2h,3Fh,7Fh
b DW 1111h,2222h,3333h

#Accessing Value From array:
a db 22h,23h,24h,25h

a[0] = 22 | a[1] = 23 | a[2] = 24 | a[3] = 25
Example [1]
	MOV AL, a[2]
	OR
	MOV SI, 2
	MOV AL, a[SI]

#Array Declaration Using DUP
DUP or dup stands for duplicate
Example[1]
	x DB 3DUP(7)
	Is the same as
	x DB 7,7,7
Example[2]
	y DB 3DUP(5,6)
	Is the same as
	Y DB 5,6,5,6,5,6

##MOV INSTRUCTION IN 8086
MOV = copieds the second operand called source to the first operand called destination
MOV AX, 7

#TYPES OF OPPERAND SUPPORTED
MOV REG, MEMORY //MOVES MEMORY TO THE REGISTER
MOV MEMORY, REG
MOV REG, REG
MOV MEMORY, IMMEDIATE
MOV REG, IMMEDIATE
NOTE: MOV MEM, MEM IS NOT SUPPORTED

REG: AX,BX,AH,AL,CH,CL,CX,DI,SI
IMMEDIATE: 7, -11,4FH (CONSTANT VALUE)
MEMORY [BX] OR [BX+SI]+DISPLACEMENT 

#MEMORY
Combination Of (BX,SI,DI,BP) REGISTERS INSIDE [] CAN BE USED TO ACCESS A MEMORY
BX SI + DISPLACEMENT
DP DI + DISPLACEMENT

eXAMPLE [BX+SI] OR [SI] OR [BP+DI]+DISPLACEMENT
Example[1]
MOV AX, BX
MOV [BX], AX 
MOV AX, [BX]
MOV [BX+SI], 5
MOV AX, 5

##Arithmetic Operations
#ADD instruction
#SUB instruction
#Processor Status Register or Flags

1. ADD:Addition
Syntax: ADD destination, source
Results is stored in destination
Example[1]
	Suppose AX = 11H and BX =14H
	ADD AX, BX; = AX = 25H

#These kinds of Operands are supported
Destination, Source
REG, REG // ADD AX, BX
Memory, REG // ADD [BX], AX
REG, Memory // ADD AX, [BX]
Memory, Immediate // ADD [BX], 7
REG, Immediate // Add CL, 40H

#REGISTER EXAMPLE IMPORTANT
Example[2]
MOV AX, 11H
MOV BX, 14H
ADD AX, BX

AX=AH+AL
AH=00000000
AL=00000000
BX=BH+BL
BX=00000000
BL=00000000

MOV AX, 11H
AH=00000000
AL=00010001

MOV BX,14H
BH=00000000
BL=00010100

ADD AX, BX
00100101 = 25H
AH=00000000
AL=00100101

2. SUB:Subtraction
Example[1]
MOV CH,22H
SUB CH, 11H
(CH IS NOW 11H)

#PROCESSOR STATUS REGISTER OR FLAGS
[15][14][13][12][11][10][9][8][7][6][5][4][3][2][1][0]
11=(OF) OverFlow
10=(DF) Direction Flag
9=(IF) Intrrupt Enable Flag
8=(TF) Trap Flag
7=(SF) Sign Flag
6=(ZF) Zero Flag
4=(AF) Auxillary Carry Flag
2=(PF) Parity Flag
0=(CF) Carry Flag

You set the flag with a 1 or zero
So the value will be set between 0 and 255
Example[1]
	MOV CH, 15H
	SUB CH, 12H
FLAGS CHANGES IN THE FOLLOWING MANNER:
Z=1(RESULT IS ZERO) //Z FLAG IS SET TO 1, C=0
Example[2]
	MOV CH,21H
	SUB CH, 11H
	Z=0(RESULT NOT ZERO),C=0(NO CARRY),S=0(RESULT NOT NEGATIVE)

3. MUL:MULTIPLICATION