# First Find

## Description
Unzip this archive and find the file named 'uber-secret.txt'

## Write-up

flag: picoCTF{f1nd_15_f457_ab443fd1}

Je fais exactement ce que dit la description. 

La commande unzip me donne le détail de ce qui est décompressé. 
Je repère le chemin vers le fichier `uber-secret`.
Il ne me reste qu'à l'afficher. 

```bash
 unzip files.zip
Archive:  files.zip
   creating: files/
   creating: files/satisfactory_books/
   creating: files/satisfactory_books/more_books/
  inflating: files/satisfactory_books/more_books/37121.txt.utf-8
  inflating: files/satisfactory_books/23765.txt.utf-8
  inflating: files/satisfactory_books/16021.txt.utf-8
  inflating: files/13771.txt.utf-8
   creating: files/adequate_books/
   creating: files/adequate_books/more_books/
   creating: files/adequate_books/more_books/.secret/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/
 extracting: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
  inflating: files/adequate_books/more_books/1023.txt.utf-8
  inflating: files/adequate_books/46804-0.txt
  inflating: files/adequate_books/44578.txt.utf-8
   creating: files/acceptable_books/
   creating: files/acceptable_books/more_books/
  inflating: files/acceptable_books/more_books/40723.txt.utf-8
  inflating: files/acceptable_books/17880.txt.utf-8
  inflating: files/acceptable_books/17879.txt.utf-8
  inflating: files/14789.txt.utf-8

 cat files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
```
