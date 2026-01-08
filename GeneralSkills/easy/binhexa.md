# binhexa

## Description
How well can you perfom basic binary operations?
nc titan.picoctf.net <port>

## Write-up

flag: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_675602ae}

```bash

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 01100011
Binary Number 2: 01000010


Question 1/6:
Operation 1: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00100001
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 11000111
Incorrect. Try again
Enter the binary result: 11000110
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01100011
Correct!

Question 4/6:
Operation 4: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01000010
Incorrect. Try again
Enter the binary result: 1100110000110
Correct!

Question 5/6:
Operation 5: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01000010
Correct!

Question 6/6:
Operation 6: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10100101
Correct!

Enter the results of the last operation in hexadecimal: A5

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_675602ae}

```
