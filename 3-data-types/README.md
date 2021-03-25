# int (1 sign bit + 31 data bits) keyword in C

In C programming language a most common keyword `int` is used to define any positive or negative integer. But there is a difference between an integer and the numbers which can be represented with the help of the keyword `int`. Not every integer can be represented with the keyword `int`. According to MinGW the size of one `int` is 4 bytes which is equal to 32 bits (1 byte=8 bits). It is still a myth somewhere that `int` can represent an integer or `int` is used to represent integers. Integer is a very vast category of numbers where as one `int` has limited and exact amount of memory (size of `int` is 4 bytes or 32 bits) to store what is being represented by it.

## SIGNED INTEGER

An `int` type variable in C language is able to store only numbers till `2147483647`. Beyond this number `int` fails to store precisely and even not correctly. `int` is a 32 bit data type. Whenever a number is being assigned to an `int` type variable, it is first converted to its binary representation (that is in 0’s and 1’s) then it is kept in memory at specific location. An `int` is actually 1 sign bit + 31 data bits, that is 31 bits are available for storing the number being assigned to a `int` type variable and 1 bit is reserved for maintaining the sign of the number which is either + or – . The sign is also represented by binary digits, 0 for positive sign and 1 for negative sign. 

Let us understand this by an example. 
### Example – Consider, 

```c
int num=2147483647;
```

At this point first `2147483647` will be converted into its binary form which is equal to: 
`1111111111111111111111111111111`. 

`1111111111111111111111111111111` is a 31 digit binary number which will be assigned to variable num’s right most 31 bits and the 32nd bit will have a `zero(0)` as the number being assigned to variable num is a positive number. If we try to store any number greater than `2147483647` into an `int` type variable then we will lose information.

## UNSIGNED INTEGER

In the case of an unsigned integer, only positive numbers can be stored. In this datatype, all the 32 bits will be reserved for the storage of data.  Therefore, the maximum value that can be stored is `4294967295`. The format specifier for unsigned integer is `%u`.

### CALCULATION OF MAXIMUM VALUE THAT CAN BE STORED IN UNSIGNED INTEGER

```
(11111111111111111111111111111111)₂ = (1 × 2³¹) + (1 × 2³⁰) + (1 × 2²⁹) + (1 × 2²⁸) + (1 × 2²⁷) + (1 × 2²⁶) + (1 × 2²⁵) + (1 × 2²⁴) + (1 × 2²³) + (1 × 2²²) + (1 × 2²¹) + (1 × 2²⁰) + (1 × 2¹⁹) + (1 × 2¹⁸) + (1 × 2¹⁷) + (1 × 2¹⁶) + (1 × 2¹⁵) + (1 × 2¹⁴) + (1 × 2¹³) + (1 × 2¹²) + (1 × 2¹¹) + (1 × 2¹⁰) + (1 × 2⁹) + (1 × 2⁸) + (1 × 2⁷) + (1 × 2⁶) + (1 × 2⁵) + (1 × 2⁴) + (1 × 2³) + (1 × 2²) + (1 × 2¹) + (1 × 2⁰) = (4294967295)₁₀
```