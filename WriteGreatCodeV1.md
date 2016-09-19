#Write Great Code Volume I : Understanding the Machine  
  
___Characteristics of Great Code___  
* Uses the CPU efficiently (which means the code is fast)
* Uses memory efficiently (which means the code is small)
* Uses system resources efficiently
* Is easy to read and maintain
* Follows a consistent set of style guidelines
* Uses an explicit design that follows established software engineering conventions
* Is easy to enhance
* Is well-tested and robust (meaning that it works)
* Is well-documented

___C++ Representation of Numbering System___  
* Hexadecimal base by prefixing a "0x" eg: 0xdead 
* Octal base by prefixing a numeric string with a zero eg: 0123 = 83.
  
___Two's complement___  
__Property :__ Two's complement representation allows the use of binary arithmetic operations on signed integers, yielding the correct 2's complement results.  
__Positive Numbers :__ Positive 2's complement numbers are represented as the simple binary.  
__Negative Numbers :__ Negative 2's complement numbers are represented as the binary number that when added to a positive number of the same magnitude equals zero.  
__Algorithm:__  
1. Invert all the bits in the number, that is, change all the zeros to ones and all the ones to zeros.  
2. Add one to the inverted result (ignoring any overflow).  

___Useful Properties of Binary Numbers___  
1. If bit position zero of a binary (integer) value contains one, the number is an odd number; if this bit contains zero, then the number is even.  
2. If the LO n bits of a binary number all contain zero, then the number is evenly divisible by 2^n.  
3. If a binary value contains a one in bit position n, and zeros everywhere else, then that number is equal to 2^n.  
4. If a binary value contains all ones from bit position zero up to (but not including) bit position n, and all other bits are zero, then that value is equal to (2^n)-1.  
5. Shifting all the bits in a number to the left by one position multiplies the binary value by two.  
6. Shifting all the bits of an unsigned binary number to the right by one position effectively divides that number by two (this does not apply to signed integer values). Odd numbers are rounded down.  
7. Multiplying two n-bit binary values together may require as many as 2*n bits to hold the result.  
8. Adding or subtracting two n-bit binary values never requires more than n+1 bits to hold the result.  
9. Inverting all the bits in a binary number (that is, changing all the zeros to ones and all the ones to zeros) is the same thing as negating (changing the sign) of the value and then subtracting one from the result.  
10. Incrementing (adding one to) the largest unsigned binary value for a given number of bits always produces a value of zero.  
11. Decrementing (subtracting one from) zero always produces the largest unsigned binary value for a given number of bits.  
12. An n-bit value provides 2^n unique combinations of those bits.  
13. The value (2^n)-1 contains n bits, each containing the value one.  


|  n | 2n     |
|:---|:-------|
| 0  | 1      |
| 1  | 2      |
| 2  | 4      |
| 3  | 8      |
| 4  | 16     |
| 5  | 32     |
| 6  | 64     |
| 7  | 128    |
| 8  | 256    |
| 9  | 512    |
| 10 | 1,024  |
| 11 | 2,048  |
| 12 | 4,096  |
| 13 | 8,192  |
| 14 | 16,384 |
| 15 | 32,768 |
| 16 | 65,536 |

___Binary-Coded Decimal (BCD) Representation___  
The binary-coded decimal (BCD) format, as its name suggests, encodes decimal values using a binary representation.  
BCD values consist of a sequence of nibbles, with each nibble representing a value in the range 0..9. Of course, you can represent values in the range 0..15 using a nibble; the BCD format, however, uses only 10 of the possible 16 values. Each nibble represents a single decimal digit in a BCD value, so with a single byte we can represent values containing two decimal digits (0..99). With a word, we can represent values having four decimal digits (0..9999). Likewise, a double word can represent up to eight decimal digits.  

___Fixed-Point Representation___  
To represent a real number in computers (or any hardware in general), we can define a fixed point number type simply by implicitly fixing the binary point to be at some position of a numeral.  

___Scaled Numeric Formats___  
  
  
