# MyKey

## Analysis

- ELF 64 non stripped 

- Need a flag

## Static

### r2

- Functions : 
  
  - powermod : Doing power and modulos dividing i each time (right shift) 
  
  - main : Checking the number of arguments and the return value of check_key
  
  - check_key

- Objects  ; all used in check_key
  
  - obj.UNIMPORTANT_FLAG : seems like array ; contains values looking like hash (used to check output from powermod)
  
  - obj.IMPORTANT_VAR2 : very big integer value

## Dynamic

- ltrace : call to strlen ; hashing something

- strace : nothing spotted
