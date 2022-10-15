## (Competition name)

### Binary purpose

Basic crackme behavior ; waiting for input and checking it

### Static

- Binary is stripped

- Some anti-analysis are setup : call with offset to confuse decompiler ; ptrace anti-debug (block anything to attach to the process)

#### `main`

- 0 Filling 192 array

- Calling some value making the debugger fail

- Check the flag value with `check_flag` and show result based on ret value

#### `check_flag`

- Contains anti-decompile instructions

- Checking the size of flag and call another function  `check_flag_value` (no argument passed although it should)

- No return direct call to `print_win`

#### `check_flag_value`

- 

#### `print_win`

- Informs user they won

### Dynamic




