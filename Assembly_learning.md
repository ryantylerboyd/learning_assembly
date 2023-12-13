##Learning assembly
##SETTING UP DOSBOX AND 8086_ASSEMBLER
#Step 1:
Go to this website and download MASM aka 8086_assembler
https://workupload.com/start/jjLjjKFw
#Step 2:
Next download DOSBOX
https://sourceforge.net/projects/dosbox/files/latest/download
#Step 3:
Install DOSBOX directly into your C Drive
	(For windows)=> C:\
#Step 4:
Next you want to add a directory to your C:\ drive called 8086
When you installed 8086_assembler you want to move all these files from that folder into the 8086 located in the C:\ drive.
	(C:\8086\[files located here])
	Here is an example of the list of files you should see in the 8086 folder now locaded at C:\8086
	BIN2HEX
	DEBUG
	EDIT
	EXE2BIN
	LINK
	MASM
	TASM
	TD
	(there might be others but this is the main files)
#Step 5:
Install DOSBOX into the C Drive C:\
#DONE
You have now finished installing the required files. Read MY FIRST PROGRAM to run your first program


##MY FIRST PROGRAM
All of this is dealing with the OSBOX terminal. If i say "in the terminal" or anything dealing with the terminal use this as a reference.

#Step 1:
Open DOSBOX
#Step 2:
In the DOSBOX terminal type in
	mount c C:\8086
	This mounts DOSBOX to the working assembler directory. So you can run assembler programs on a 64bit computer through DOSBOX
	TYPE C:
#Step 3:
In the C:\8086 Directory,
	create a file called helloworld.asm
	(please google an example file. I dont want to take up so many lines with a hello world).
	Save the file with the helloworld code.
#Step 4:
In the terminal (OSBOX)
	Type: masm helloworld.asm
It should come out like this:
	0 Warning Errors
	0 Severe Errors
If not you have an issue with your code.
#Step 5;
In the terminal (OSBOX)
	Type: link helloworld
When you build a project containing one or more Assembler modules, the Assembler Compiler first creates an object code file (.obj) for each module. Next, you can either have the Assembler compiler automatically link the object code file into an executable load module (.390) or you can run a separate linker process that combines several object modules into a single linked load module. The link process uses its own link file (.lin) containing link commands. The Assembler automatically searches for external references in CALL commands in the object code files and includes additional object code files as necessary to resolve the external references.

Linking modules when you build the project is known as static linking. You can also link modules dynamically at execution time, when external references in LINK or LOAD commands are resolved. 
#Step 6;
In the terminal (OSBOX)
	Type: helloworld.exe

##FIRST PROGRAM SIMPLIFIED
In the DOSBOX terminal type in
	mount c C:\8086
	TYPE c:
In the C:\8086 Directory,
	create a file called helloworld.asm
In the terminal (OSBOX)
	Type: masm helloworld.asm
In the terminal (OSBOX)
	Type: link helloworld
In the terminal (OSBOX)
	Type: helloworld.exe


##Comments
; before the line creates a comment

##Types of intruction
numonic os the name
#mov, sub, int
mov => preforms a move
sub => preforms a subtraction
int => preforms an inturrupt

#mul, div
mul => mutiplies aginst the eax register
div => Divideds aginst the eax register

EXAMPLES OF subtraction
mov ebx, 42 ;this means that ebx is now equal to 42
sub ebx, 29 ;this will subtract 29 from ebx leaving you with 13

EXAMPLE 2
mov ebx, 123	; ebx = 123
mov eax, ebx	; eax = ebx
add ebx, ecx	; ebx += ecx
sub ebx, edx	; ebx -= edx
mul ebx			; eax *= ebx
div edx			; eax /= edx    aka eax/edx

##Data segment
.data => In computing, a data segment (often denoted .data) is a portion of an object file or the corresponding address space of a program that contains initialized static variables, that is, global variables and static local variables. The size of this segment is determined by the size of the values in the program's source code, and does not change at run time. 