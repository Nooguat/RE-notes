# Aibophobia

- Meaning the fear of palindrome

## Caracteristics

- x86 64

- pic is enabled

## Binary purpose

## Control flow

Binary is encrypting the flag using a secret given to the user. Then check the flag against function to assert the validity of flag

### Static

srand is imported

#### `main`

- 1st loop : zeroing some space ? (99 iterations)

- 2nd loop : calling rand; shifting and sum operations flag generation (49 iterations)

- 3rd loop : filling string (running until \0 byte)

- 4th loop : waiting for user input until counter is 0 (value is stringlen + counter)

#### `sym.check`

- Calling `obj,encrypted_flag`

#### `sym.PrintFlag`

#### `sym.next`

### Dynamic


