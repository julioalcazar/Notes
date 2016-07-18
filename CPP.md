#My C++ Notes
**Loops**  
 1. The while loop.
 2. The do-while loop.
 3. The for loop
 4. The Range-Based for Loop

``` cpp
//Range-Based for Loop Sample  
std::array<int, 4> arr = {1, 2, 3, 4};
for (int i : arr) 
{
   std::cout << i << std::endl;
}
``` 
  
**Strings**
 1. C Style string (char array)
 2. C++ strings
 3. Nonstandard strings (CString MFC)
  
**Switch:** Can only compare between a variable and a constant, but not variable and variable.
``` cpp
switch (someItem) 
{
case 1:
   // Code to do something
   break;
case 2:
   // Code to do something else
   break;
default:
   // Code to give an error message
   break;
}
```
  
**\\n vs endl:** endl forces flush (write data from buffer to stream).
You can’t pass an array by value, pass by address.

``` cpp
void somefunction(int arg[], int size)
{
   ...
}

int main()
{
   int arr[50];
   somefunction(arr, (sizeof(arr)/sizeof(*arr))); //Only works if array is created in same scope
}
``` 
  
**Wild pointer:** Pointer that have not been initialized.  
**Using:** Never put a using directive or using declaration in a header file, otherwise you force it on everyone that is including your header. Variables
  
**New vs Malloc**  
 1. **new & delete:** call constructor and destructor.  
    **malloc & free:** do not call contractor or destructor.  

 2. **new:** can call other default constructors.  
    **malloc:** can’t call constructors.  
  
 3. **new:** no casting needed  
    **malloc:** returns a void\* type casting is a must  

 4. **realloc**: can be used with malloc & free  

**Literals**  
- Literals are used to write numbers or strings in your code.  
- Decimal literal, for example: 123  
- Octal literal, for example: 0173  
- Hexadecimal literal, for example: 0x7B  
- Binary literal, for example: 0b1111011 (C++14)  
- A floating point value: 3.14f  
- A double floating point value: 3.14  
- A single character: ‘a’  
- A zero-terminated array of characters: “character array”  

``` cpp
//C++14
auto string1 = "Hello World"; // string1 will be a const char*
auto string2 = "Hello World"s; // string2 will be an std::string
``` 
  
**Std::String**
The following functions are available to convert numerical values into strings:
``` cpp
string to_string(int val);
string to_string(unsigned val);
string to_string(long val);
string to_string(unsigned long val);
string to_string(long long val);
string to_string(unsigned long long val);
string to_string(float val);
string to_string(double val);
string to_string(long double val);
```

Converting in the other direction is done by the following

``` cpp
int stoi(const string& str, size_t *idx=0, int base=10);
long stol(const string& str, size_t *idx=0, int base=10);
unsigned long stoul(const string& str, size_t *idx=0, int base=10);
long long stoll(const string& str, size_t *idx=0, int base=10);
unsigned long long stoull(const string& str, size_t *idx=0, int base=10);
float stof(const string& str, size_t *idx=0);
double stod(const string& str, size_t *idx=0);
long double stold(const string& str, size_t *idx=0);
``` 

**Raw String Literals**
Raw string literals are string literals that can span across multiple lines of code, that don’t require escaping of embedded double quotes

``` cpp
string str = "Hello "World"!"; // Error!
```
With a normal string you have to escape the double quotes as follows:
``` cpp
string str = "Hello \"World\"!";
``` 
With a raw string literal you can avoid the need to escape the quotes. he raw string literal starts with R"( and ends with )".

``` cpp
string str = R"(Hello "World"!)";
string str = R"(Line 1
Line 2 with \t)";
``` 
Output
``` 
string str = R"(Hello "World"!)";
string str = R"(Line 1
Line 2 with \t)";
``` 

**Comments**
``` cpp
/*
* Author: marcg
* Date: 110412
* Feature: PRD version 3, Feature 5.10
*
* Date   | Change
*--------+--------------------------------------------------
* 110413 | REQ #005: <marcg> Do not normalize values.
* 110417 | REQ #006: <marcg> use nullptr instead of NULL.
*/
```

**Enumerated Types**
``` cpp
enum PieceType 
{ 
   PieceTypeKing,
   PieceTypeQueen,
   PieceTypeRook,
   PieceTypePawn
};

``` 
Behind the scenes, an enumerated type is just an integer value. The real value of PieceTypeKing is zero.

**Strongly Typed Enumerations**
    Enumerations as explained above are not strongly typed, meaning they are not type-safe. They are always interpreted as integers, and thus you can compare enumeration values from completely different enumeration types. The enum class solves these problems.

``` cpp
enum class MyEnum
{
   EnumValue1,
   EnumValue2 = 10,
   EnumValue3
};
``` 
The enumeration values are not automatically converted to integers, which means the following is illegal:

``` cpp
if (MyEnum::EnumValue3 == 11) {...}
```

**Alternative Function Syntax**
 The following example demonstrates the alternative function syntax. The auto keyword in this context has the meaning of starting a function prototype using the alternative function syntax
``` cpp
auto func(int i) -> int
{
   return i + 2;
}
```

**auto Keyword**

The auto keyword has four completely different meanings.
1. The first meaning is to tell the compiler to automatically deduce the type of a variable at compile time.
``` cpp
auto x = 123; // x will be of type int
```

2. The second use of the auto keyword is for the alternative function syntax.
``` cpp
auto func(int i) -> int
{
   return i + 2;
}
```

3. The third use of the auto keyword is for function return type deduction
``` cpp
auto divideNumbers(double numerator, double denominator)
{
   if (denominator == 0) { /* ... */ }
   return numerator / denominator;
}
```

4. Fourth use of auto is for generic lambda expressions


**const Keyword**
If the word const appears to the left of the asterisk, what’s pointed to is constant; if the word const appears to the right of the asterisk, the pointer itself is constant; if const appears on both sides, both are constant
``` cpp
char greeting[]="Hello";
char *p = greeting;       //Non-const pointer, non-const data
const char *p = greeting; //Non-const pointer, const data
char* const p = greeting; //Const pointer, non-const data
const char* const p = greeting //const pointer, const data

void f1(const Widget *pw); //f1 takes a pointer to a constant Widget object
void f2(Widget const *pw); //f2 so does f2
```

**decltype Keyword**
 The decltype keyword takes an expression as argument, and computes the type of that expression
``` cpp
int x = 123;
decltype(x) y = 456;
```
In this example, the compiler deduces the type of y to be int because that’s the type of x. Like the auto keyword for the alternative function syntax, the decltype keyword doesn’t seem to add much value on first sight. However, in the context of templates, discussed in Chapter 11 and 21, auto and decltype become pretty powerful.

Using auto to deduce the type of an expression strips away reference qualifiers and const qualifiers. decltype does not strip those but might cause code duplication.
``` cpp
const string message = "Test";
const string& foo()
{
   return message;
}
```

You can call foo() and store the result in a variable with the type specified as auto as follows:
``` cpp
auto f1 = foo();
```
 
Because auto strips reference and const qualifiers, f1 is of type string, and thus a copy is made. If you want f1 to be a const reference, you can explicitly make it a reference and mark it const as follows:
``` cpp
const auto& f1 = foo();
```

An alternative solution is to use decltype, which does not strip anything:
``` cpp
decltype(foo()) f2 = foo();
```

The solution in C++14
``` cpp
decltype(auto) f3 = foo();
```

**Advantages/Disadvantages C-Style Strings**
**Advantages:**
- They are simple, making use of the underlying basic character type and array structure.
- They are lightweight, taking up only the memory that they need if used properly.
- They are low level, so you can easily manipulate and copy them as raw memory.
- They are well understood by C programmers — why learn something new?

**Disadvantages:**
- They require incredible efforts to simulate a first-class string data type.
- They are unforgiving and susceptible to difficult-to-find memory bugs.
- They don’t leverage the object-oriented nature of C++.
- They require knowledge of their underlying representation on the part of the programmer.

**Big-O**

| ALGORITHM COMPLEXITY  | BIG-O NOTATION  | EXPLANATION | EXAMPLE ALGORITHMS |
| --------------------- |:---------------:|:----------- |:------------------ |   
| Constant              | O(1)            | Running time is independent of input size. | Accessing a single element in an array |  
| Logarithmic           | O(log n)        | The running time is a function of the logarithm base 2 of the input size. | Finding an element in a sorted list using binary search |  
| Linear                | O(n)            | The running time is directly proportional to the input size. | Finding an element in an unsorted list |  
| Linear Logarithmic    | O(n log n)      | The running time is a function of the linear times the logarithmic function of the input size.  | Merge sort |  
| Quadratic             | O(n2)           | The running time is a function of the square of the input size. | A slower sorting algorithm like selection sort |  
| Exponential           | O(2n)           | The running time is an exponential function of the input size. | Optimized traveling salesman problem |  


**Access Specifiers**

| ACCESS SPECIFICATION | MEANING |  WHEN TO USE| 
| -------------------- |:------- |:----------- |
| public | Any code can call a public member function or access a public data member of an object. |  Behaviors (methods) that you want clients to use. Access methods for private and protected data members. |  
| protected | Any member function of the class can call protected member functions and access protected data members. Member functions of a derived class can access protected members of a base class. |  “Helper” methods that you do not want clients to use.|  
| private | Only member functions of the class can call private member functions and access private data members. Member functions in derived classes cannot access private members from a base class. |  Everything should be private by default, especially data members. You can provide protected getters and setters if you only want to allow derived classes to access them, and provide public getters and setters if you want clients to access them.|  


``` cpp
```
