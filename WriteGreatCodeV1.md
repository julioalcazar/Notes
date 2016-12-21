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
  
  
___Adding Binary Values___  

* 0 + 0 = 0
* 0 + 1 = 1
* 1 + 0 = 1
* 1 + 1 = 0 with carry
* Carry + 0 + 0 = 1
* Carry + 0 + 1 = 0 with carry
* Carry + 1 + 0 = 0 with carry
* Carry + 1 + 1 = 1 with carry

___Subtracting Binary Values___  
* 0 - 0 = 0
* 0 - 1 = 1 with a borrow
* 1 - 0 = 1
* 1 - 1 = 0
* 0 - 0 - borrow = 1 with a borrow
* 0 - 1 - borrow = 0 with a borrow
* 1 - 0 - borrow = 0
* 1 - 1 - borrow = 1 with a borrow
 
___Multiplying Binary Values___  
* 0 x 0 = 0
* 0 x 1 = 0
* 1 x 0 = 0
* 1 x 1 = 1

___Logical Operations on Bits___  

AND:  
* 0 and 0 = 0
* 0 and 1 = 0
* 1 and 0 = 0
* 1 and 1 = 1

OR:  
* 0 or 0 = 0
* 0 or 1 = 1
* 1 or 0 = 1
* 1 or 1 = 1

XOR:  
* 0 xor 0 = 0
* 0 xor 1 = 1
* 1 xor 0 = 1
* 1 xor 1 = 0

___Floating-Point Arithmetic___  
Comparing floating-point numbers is very dangerous. Given the inaccuracies present in any computation (including converting an input string to a floating-point value), you should never compare two floating-point values to see if they are equal.  
The standard way to test for equality between floating-point numbers is to determine how much error (or tolerance) you will allow in a comparison, and then check to see if one value is within this error range of the other. The straightforward way to do this is to use a test like the following.  
*  if( (Value1 >= (Value2 − error)) and (Value1 <= (Value2 + error)) then...  
A more efficient way to handle this is to use a statement of the form:  
*  if( abs(Value1 − Value2) <= error ) then . . .  

___Character Representation___  
**ASCII Character Set:** The ASCII (American Standard Code for Information Interchange) character set maps 128 characters to the unsigned integer values 0..127  
* The ASCII character set is divided into four groups of 32 characters. The first 32 characters, ASCII codes 0x00 through 0x1F (0 through 31), form a special set of nonprinting characters called the control characters.  
* The second group of 32 ASCII character codes comprises various punctuation symbols, special characters, and the numeric digits.  
* The third group of 32 ASCII characters contains the uppercase alphabetic characters.
* The fourth and final group of 32 ASCII character codes represents the lowercase alphabetic symbols, five additional special symbols, and another control character (delete).  
  
If you convert the codes for the upper and lowercase characters to binary, you will notice that the uppercase symbols differ from their lowercase equivalents in exactly one bit position. The only place these two codes differ is in bit five. Uppercase alphabetic characters always contain a zero in bit five; lowercase alphabetic characters always contain a one in bit five.  

**EBCDIC Character Set:** an acronym that stands for Extended Binary Coded Decimal Interchange Code. BCDIC is that it is not a single character set; rather, it is a family of character sets.  

**Double-Byte Character Sets:** A typical double-byte character set utilizes the standard ASCII character set along with several additional characters in the range $80..$FF.  

**Unicode Character Set:** Unicode uses a 16-bit word to represent each character.  

___Character Strings___
**Zero-Terminated Strings**  
**Advantages**  
*  Zero-terminated strings can represent strings of any practical length with only one byte of overhead (two bytes in Unicode).
*  Given the popularity of the C/C++ programming languages, highperformance string processing libraries are available that work well with zero-terminated strings.  
*  Zero-terminated strings are easy to implement. Indeed, except for dealing with string literal constants, the C/C++ programming languages don’t provide native string support. As far as the C and C++ languages are concerned, strings are just arrays of characters. That’s probably why C’s designers chose this format in the first place — so they wouldn’t have to clutter up the language with string operators.  
*  This format allows you to easily represent zero-terminated strings in any language that provides the ability to create an array of characters.  

**Disadvantages**  
*  String functions often aren’t very efficient when operating on zeroterminated strings. Many string operations need to know the length of the string before working on the string data. The only reasonable way to compute the length of a zero-terminated string is to scan the string from the beginning to the end. The longer your strings are, the slower this function runs. Therefore, the zero-terminated string format isn’t the best choice if you need to process long strings.
*  Though this is a minor problem, with the zero-terminated string format you cannot easily represent any character whose character code is zero (such as the ASCII NUL character).  
*  With zero-terminated strings there is no information contained within the string data itself that tells you how long a string can grow beyond the terminating zero byte. Therefore, some string functions, like concatenation, can only extend the length of an existing string variable and check for overflow if the caller explicitly passes in the maximum length.

**Length-Prefixed Strings**  
**Seven-Bit Strings**  
An interesting string format that works for 7-bit codes like ASCII involves using the Hight bit to indicate the end of the string. All but the last character code in the string would have their HO bit clear (or set, your choice) and the last character in the string would have its HO bit set (or clear, if all the other HO bits are set).
This 7-bit string format has several disadvantages:
*  You have to scan the entire string in order to determine the length of the string.
*  You cannot have zero-length strings in this format.
*  Few languages provide literal string constants for 7-bit strings.
*  You are limited to a maximum of 128 character codes, though this is fine when using plain ASCII.  

**HLA Strings**  
The HLA string format uses a 4-byte length prefix, allowing character strings to be just over four billion characters long (obviously, this is far more than any practical application will use). HLA also sticks a zero byte at the end of the character string data, so HLA strings are upward compatible with string functions that reference (but do not change the length of) zeroterminated strings. The additional four bytes of overhead in an HLA string contain the maximum legal length for that string. Having this extra field allows HLA string functions to check for string overflow, if necessary.
