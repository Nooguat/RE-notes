Imaginary CTF

## Static

ELF x86 ; written in cpp

Description : `The answer is out there and it's looking for you`



#### radare2

- Found `srand` call ; seed stay constant : 0x1337
- **140** functions are declared in static; **37** in dynamic ?
- Multiple `call`s are made on bare address ; which are also calling addr like that 
- `afll size~fcn[14]:140..150` : get the 10 biggest functions in file with result : 
  
  
  `fcn.00003dff
  fcn.00002988
  fcn.0000490a
  fcn.00003d38
  fcn.00002bbe
  fcn.00002cb4
  fcn.00004bd4
  fcn.00002d9e
  fcn.00002f6c
  fcn.0000313c`

#### Ghidra

- Some functions are not leading anywhere (calling other functions that are only returning their argument)

- Can list the functions by size in Ghidra (lol)

- Found another pair of function; same code with differents arguments (and not the same return value)

- ## Dynamic

    no echo when run with/without args but a file is generated : `output.txt`

    strace analysis : `missing file : flag.txt`

        After creating ; something comes up in `output.txt`

- The input value seems to be copied two times; no overwrite

##### Input fuzzing

- Reverse input : not giving out primary input (non reciproque)

- Output only depends on the input

- No reduction factor ;  output is the same size as input

- Maybe something with non ASCII characteres; more chaotic output

 

   
