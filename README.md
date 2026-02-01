# C-
## Struct
Help us to create a user defined datatye of different size.\
We can not give value to any variable in structure \
we can make array of variable length eg(char ch[6])\
Indexing starts from zero 


## Size of different data types
int-2 byte\
float-4 byte\
char- 1 byte\
pointer variable-2 byte

## Nested Structure 
we can call a struct in another struct 

## Use of different symbols
### *
  eg( * a  ) value in a , (int* a) this means a is pointer variable 
### &
  eg(&b) means address of b
### →
 eg(p→c) means *p.a
### ++
only moves 1 byte at once\ 
++ before a variable will do incriment defore the operation or initialisation and after the variable will be initisized after gaining the value 
### -- 
works similar to ++ and it's function is to decrease 1 byte 


## How to assign value to variables defined in struct
* we can not assign value directly in struct so we write valued in(let struct b)\
*eg- struct b s1={abc,1 , 1.3 etc.}\
*in {}write valued according to data type defined in struct

## Output of different data type 
For output of any datatype we use 
### %S for output in string
eg- print(%s, P[0]i)
### %d for integer (int)
eg- print(%d, P[0]i)
### %c for char
eg- print(%c, P[0]i)
## Pointer
Pointer will move with the size of struct at once\
for eg if struct is if size 6 so pointer will move from 1000 to 1006 and then to 1012
## Alias name 
We can name our struct as a single variable by using →type def\
eg→ type def struct S1 {\
                char a\
                int b\
                }t;
 





