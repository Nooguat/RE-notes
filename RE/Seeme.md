# Seeme

## Context

- C code; regular file 

- When compiled nothing unusual

- When run doesnt print out the same text as in the source code

## Static

##### r2

handling arguments (2) ?

Found two strings ; encrypted ? `P67ANY$QU3STV0IC25!WM14`  `HGDWIFkviEp$!zc$9!!xg#$`

Program can be splited in 2 parts :  __initializing strings__ using multiple techniques and then call to 6 functions which seems to set the __value of the string to output__. Default is `**pooof** Now you don't !` ? (string not present in the file)

##### Functions purpose

- fix_bytes() : Running n times (to find); seems to order by value using XOR operation (funny)

- deprecated() : copies string (being actually deprecated...)

- merge_bytes() : XOR two strings 

##### Control Flow

- Decode functions are called twice ? 

- Everything is working around XOR operation

## Dynamic

- nothing useful from `[ls]trace` 
- Debugger gives the solution ; db between the two decode parts




