# Data types, Variables and Arrays

Java is a strongly typed language.

Java has 8 primitive types which are grouped in four groups:
1. Integers - byte, short, int and long
2. Floating-point numbers - float, double
3. Characters - char
4. Boolean - bool

Although Java is otherwise completely object-oriented language, primitives data types are not. They are kept as it 
is for performance efficiency. And these primitive types becomes the basis for all other data types. 

Because of Java's portability, all the data types have strict defined ranges 

Java doesn't support unsigned or only positive numbers. 


| Name  | width | range           |
|-------|-------|-----------------|
| long  | 64    |                 |
| int   | 32    |                 |
| short | 16    | -32768 to 32767 |        
| byte  | 8     | -128 to 127     |
    

byte - useful when working with raw binary data or stream of data from network or file.

integer - commonly employed to loops and indexes of array. byte and shorts are also automatically promoted to int 
when expression is evaluated. 

double - is best choice. modern processors are optimised for the same. sin, cos all math functions return values in 
double. (64 bits - 8 bytes)

characters - 16bit
supports UNICODE - 16bits (ASCII - 8bits are better in performance but unicode supports global portability.)
character can hold an int value as well and arithmetic operations can be applied on that.

- Octal -> starts with 0 (0 to 7 digits). Example: 0273 values to 187

- Hexadecimal -> starts with 0x (0 to 7 digits). Example: 0x1F values to 31

- long value can be assigned to integer as long as it within boundaries. int value can be assigned to long any time. 

- literal assignment using binary (starts with 0b or 0B) 

underscores are allowed in literals Example - 1_00_000 (at compilation time, these underscores are removed. its just 
for readability) Cannot come in beginning or at end. Also allowed in decimal point for float or double.

String are not arrays of characters like in c or c++. Strings are actually object types. 