# Binary Search

## Description

Want to play a game? 
As you use more of the shell, you might be interested in how they work! 
Binary search is a classic algorithm used to quickly find an item in
a sorted list. Can you find the flag? You'll have 1000 possibilities
and only 10 guesses. Cyber security often has a huge amount of data to 
look through - from logs, vulnerability reports, and forensics. Practicing
the fundamentals manually might help you in the future when you have to
write your own tools! You can download the challenge files here:

    challenge.zip

## writeup

flag:picoCTF{g00d_gu355_bee04a2a} 

C'est littéralement un algorithme de recherche binaire.
Comme je connais déjà le principe, c'est plus évident.

```bash

Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 125
Lower! Try again.
Enter your guess: 62
Lower! Try again.
Enter your guess: 31
Lower! Try again.
Enter your guess: 15
Lower! Try again.
Enter your guess: 7
Lower! Try again.
Enter your guess: 3
Congratulations! You guessed the correct number: 3
Here's your flag: picoCTF{g00d_gu355_bee04a2a}
Connection to atlas.picoctf.net closed.

```


