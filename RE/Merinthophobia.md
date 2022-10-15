### Context

- Imaginary CTF challenge edition 14 

- Merinthophobia is the fear of being tied up / bound

- ROP based binary

### Static

- Found 3 objects command is : `f~obj`
  
  - <mark>obj.rooNobool</mark> : contains the false flag
  
  - <mark>obj.roocursion</mark> : contains the first addr pushed in main
  
  - <mark>obj.rooYay</mark> : contains the big encoded string

- Instructions are stocked between functions between offset `0x00401140` and `0x00401169`
  
  - Almost only `pop` and `ret` instructions ; only one `cmp` with `cmove`
  
  - **Those instructions are used to manipulate registers ; specifically `rsp` and `rbp` to modify the stack content ; example at `0x00401165`**
  
  - The `cmp cmove` block is used to check if the character is valid ; else its calling syscall with 60 as argument ; which is exit value
  
  - Password is made from the differents strings in the binary to create a flag offsets are given by the stack values / modifications

- Only 3 functions ; no direct call to the 2 last
  
  - `main` : only contains a `memcpy` instruction and returns
    
    - Value is written to rbp ; poped after (value is "AAAAAAAA")
      
      - _Recall : pop loads value from the top of the stack and place it in register ; increase stack pointer (rdi)_
    
    - Value is poped a 2nd time with the ret instruction ; which means we go to `0x00401141` . **This should have been spotted with the PIE disabled** 
  
  - `rooVoid` : calling syscall at the start of function and then poping values from  registers
    
    - _Recall : syscall gets its input value form rdx_
    
    - Tracking calls to rooVoid 
  
  - `rooScientist` : while loop (arg2 time) doing some XOR based on the value of counter (%2)

- Lots of strings in .data almost composed with only *, B,  { characters
  
  - Removed those characters from data ; obtained this string.
    
    ```md
    jctf{why_w0uld_ANYONE_like_rev_it&
    #39;s_so_frustrating!!!.AAAAAAAAA..#^bC1n....6&
    amp;#39;n$F#M.nh.......C..a.Pt.C...(j.a..t..a.X).e..a.
    (j.e.#.a.t.~...a.p..e..a.7j.e.#.a.t.~...a..e..a.4j.e.#.
    a.t.~...a.:+.e..a.9j.e.#.a.t.~...a.:+.e..a.8j.e.#.a.t.~
    ...a.[).e..a.>j.e.#.a.t.~...a..e..a.2j.e.#.a.t.~
    ...a.m..e..a.-j.e.#.a.t.~...a..e..a..e.#.a.t.~...a..e..
    a./j.e.#.a.t.~...a.p..e..a.:j.e.#.a.t.~...a.1).e..a.0j.
    e.#.a.t.~...a.f..e..a..e.#.a.t.~...a.f..e..a.)j.e.#.a.
    t.~...a.n..e..a.1j.e.#.a.t.~...a.m).e..a.5j.e.#.a.t.~..
    .a.f).e..a.3j.e.#.a.t.~...a.x(.e..a..j.e.#.a.t.~...a..e
    ..a.6j.e.#.a.t.~.....E....cneE7n%E.nh...6n6&#39;n$F
    ....#Mc....C..a
    ```

- Nothing interesting trying to XOR the .data string block to the 2 known values from `rooScientist`

### Dynamic

- Asking for password 

- nothing interesting from `lstrace` and `strace`

- Password is get one by one character by breakpiont the `cmp` 

##### Debugger

- As lot of manipulation on the rbp value is done; reading the stack is mandotary : `pxw @ (dr rsp)` () are ``

- `drr` prints the register values understood by radare

- `dmh` prints the sections in the heap memory
