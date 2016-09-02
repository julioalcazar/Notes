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
