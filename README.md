# Mona-Cheat-Sheet

Main Project Page -> github.com/corelan/mona

Download the file and save it to this typical location ->

C:\Program Files\Immunity Inc\Immunity Debugger\PyCommands

BASIC USAGE :

!mona in the input box and press enter

For more information = Open log window (ALT-L)

For Help options ->

!mona help <command>

Updating Mona ->

!mona update [-http]        #if default https doesn't work

!mona update -t release/trunk     #Switch between trunk and stable release

SETUP DEBUGGER ENVIRONMENT :

Working folder ->

Writing output to application specific folders

!mona config -set workingfolder C:\somefolder\[%p] #process name

!mona config -set workingfolder C:\somefolder\[%i] #process ID

This config param is written into a file called 'mona.ini'

Exclude modules ->

Exclude modules from search operations

!mona config -set excluded_modules "module1.dll,module2.dll"

!mona config -add excluded_modules "module3.dll"

author ->

Set author variable

!mona config -set author darthvad3r

GLOBAL OPTION :

option -n -> all modules that start with a null byte will be skipped

option -o -> ignore OS module from search operation

option -p -> takes only one numeric argument, it allows to limit the number of results to return

option -m -> specify the module to perform search operation on; can also use *

option -cm -> set a critera(c) a module(m) should comply with to get inculded in search

[Available criteria = aslr, rebase, safeseh, nx, os]

option -cp -> set a critera(c) a pointer(p) should match

[Available criteria = unicode, ascii, asciiprint, upper, lower, uppernum, lowernum,  numeric, alphanum, nonull, startswithnull]

option -cpb -> specify bad characters for pointers (like '\x00\xoa\x0z')

option -x -> set the desired access level of the resulting pointers

[Available values = *, R, RW, RX, RWX, W, WX, X]

OUTPUT FILES :

Look into the original resource page

COMMANDS :

a -> alias for seh

assemble -> convert one or more assembly language into opcode

bf -> set breakpoint on exported or imported functions of selected module

bp -> set breakpoint on a given address, which will be triggered if the address is read from or written to

bytearray -> finds bad chars

compare -> compare bytes in memry

dump -> dumps block of bytes from memory to file

egg -> creates an egghunter routing

filecompare -> compare output of two systems

find -> find strings or pointers

findmsp -> find all instance information to a cyclic pattern in memory, registers, etc.

    >>> IMP REQ : HAVE TO USE A CYCLIC PATTERN TO TRIGGER A CRASH <<<

    | Locations where the cyclic pattern can be found (looks for the first bytes of a pattern) and how long that pattern is

    | Registers that are overwritten with 4 byte of a cyclic pattern and the offset in the pattern to overwrite the register

    | Registers that point into a cyclic pattern, the offset, and the remaining size of the pattern

    | SEH records overwritten with 4 bytes of a cyclic, offset, and size

    | Pointers on the current thread stack, into a cyclic pattern (offset + size)

    | Parts of a cyclic pattern on the stack, the offset from the begin of the pattern and the size of the pattern

findwild -> perform wildcard searches in memory

getpc -> outputs 3 diff GetPC routines

getiat -> dump contents of IAT of selected modules

header -> read a file and output the contents of the file in such a way it can be used an exploit

heap -> dump lookaside list and freelists entries on XP

help -> provides info about command

info -> shows info about a given pointer

j -> alias of jmp

jmp -> search for pointers that will lead to execute the code located at the address pointed by a given register

jop -> gadgets that can be used in a JOP payload

jseh -> alias for seh

modules -> shows information about loaded modules

noaslr -> shows information about loaded modules with aslr=false

nosafeseh -> shows information about loaded modules with safeseh=false

nosafesehaslr -> shows information about loaded modules with safeseh=false,aslr=false

offset -> distance between 2 addresses

p -> alias for seh, search for non safeseh and non rebase modules

p1 -> alias for seh, search for non aslr, non safeseh and non rebase modules

p2 -> search all loaded modules

pattern_create -> produce cyclic pattern of a given size and write to pattern.txt

pattern_offset -> locate the given 4 bytes in cyclic pattern and return the  position of thos 4 bytes in the pattern

pc -> alias for pattern_create

po -> alias for pattern_offset

rop -> look for gadgets in non aslr, non rebase and non OS modules

ropfunc -> locate pointers to interesting functions in terms of bypassing DEP

seh -> search for pointers to routines that will lead to code execution in SEH overwrite exploit

stackpivot -> search for gadgets that will result in pivoting back into the stack, at a given offset from the current value of ESP

stacks -> list stack information for each thread in the application

suggest -> auto runs findmasp and then take that info to suggest exploit skeleton

skeleton -> creates and empty metasploit skeleton module for a given type of exploit using cyclic pattern as payload
