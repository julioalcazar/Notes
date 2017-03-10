#My C++ Notes
**Loops**  
 1. The while loop.
 2. The do-while loop.
 3. The for loop
 4. The Range-Based for Loop

``` cpp
//Range-Based for Loop Sample  
std::array<int, 4> arr = {1, 2, 3, 4};
for (int i : arr) {
   std::cout << i << std::endl;
}
``` 
  
**Strings**
 1. C Style string (char array)
 2. C++ strings
 3. Nonstandard strings (CString MFC)
  
**Switch:** Can only compare between a variable and a constant, but not variable and variable.
``` cpp
switch (someItem) {
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
void somefunction(int arg[], int size) {
   ...
}

int main() {
   int arr[50];
   somefunction(arr, (sizeof(arr)/sizeof(*arr))); //Only works if array is created in same scope
}
``` 
  
**Wild pointer:** Pointer that have not been initialized.  
**Using:** Never put a using directive or using declaration in a header file, otherwise you force it on everyone that is including your header.  
  
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
- A zero-terminated array of characters: "character array"  

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
enum PieceType  { 
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
enum class MyEnum {
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
auto func(int i) -> int {
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
auto func(int i) -> int {
   return i + 2;
}
```

3. The third use of the auto keyword is for function return type deduction
``` cpp
auto divideNumbers(double numerator, double denominator) {
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
const string& foo() {
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
| protected | Any member function of the class can call protected member functions and access protected data members. Member functions of a derived class can access protected members of a base class. |  "Helper" methods that you do not want clients to use.|  
| private | Only member functions of the class can call private member functions and access private data members. Member functions in derived classes cannot access private members from a base class. |  Everything should be private by default, especially data members. You can provide protected getters and setters if you only want to allow derived classes to access them, and provide public getters and setters if you want clients to access them.|  


**The Compiler will generate the following by default**
 1. Default constructor
 2. Copy constructor
 3.	Copy assignment operator
 4.	Default destructor

**When You Need a Default Constructor**
Consider arrays of objects. The act of creating an array of objects accomplishes two tasks: It allocates contiguous memory space for all the objects and it calls the default constructor on each object. C++ fails to provide any syntax to tell the array creation code directly to call a different constructor. For example, if you do not define a default constructor for the SpreadsheetCell class, the following code does not compile:
``` cpp
SpreadsheetCell cells[3]; // FAILS compilation without default constructor
SpreadsheetCell* myCellp = new SpreadsheetCell[10]; // Also FAILS
```
You can circumvent this restriction for stack-based arrays by using initializers like these:  
``` cpp
SpreadsheetCell cells[3] = {SpreadsheetCell(0), SpreadsheetCell(23),
SpreadsheetCell(41)};
```
However, it is usually easier to ensure that your class has a default constructor if you intend to create arrays of objects of that class. If you haven’t defined your own constructors, the compiler will automatically create a default constructor for you. This compiler-generated constructor is discussed in a next section. A default constructor is also required for classes that you want to store in an STL container like std::vector.  Default constructors are also useful when you want to create objects of that class inside other classes, which is shown later in this chapter under the section Constructor Initializers.  

**Using default constructors**
Unfortunately, the line attempting to call the default constructor will compile. The line following it will not compile. The problem is that your compiler thinks the first line is actually a function declaration for a function with the name myCell that takes zero arguments and returns a SpreadsheetCell object. When it gets to the second line, it thinks that you’re trying to use a function name as an object!
``` cpp
SpreadsheetCell myCell(); // WRONG, but will compile.
myCell.setValue(6); // However, this line will not compile.
cout << "cell 1: " << myCell.getValue() << endl;
```

**Explicitly Defaulted Constructors**
This allows you to write the class definition as follows without the need to implement it in the implementation file.  
``` cpp
class MyClass {
public:
   MyClass() = default;
   MyClass(int i);
};
```

**Explicitly Deleted Constructors**
C++11 also supports the concept of explicitly deleted constructors. For example, you can define a class for which you do not want to write any constructors and you also do not want the compiler to generate the default constructor.
``` cpp
class MyClass {
public:
   MyClass() = delete;
};
```
**Initialization list (ctor-initializer)**
Must be used with the following

| DATA TYPE | EXPLANATION | 
| --------- |:----------- |
| const data members |You cannot legally assign a value to a const variable after it is created. Any value must be supplied at the time of creation.|
| Reference data members | References cannot exist without referring to something. |
| Object data members for which there is no default constructor | C++ attempts to initialize member objects using a default constructor. If no default constructor exists, it cannot initialize the object. |
| Object data members for which there is no default constructor | C++ attempts to initialize member objects using a default constructor. If no default constructor exists, it cannot initialize the object. |
| Superclasses without default constructors | No default constuctors to call and create the object |

**Default copy constructor**
Given a set of member variables, called m1, m2, ... mn, the compiler-generated copy constructor can be expressed as:
``` cpp
classname::classname(const classname& src) :
   m1(src.m1), m2(src.m2), ... mn(src.mn) { }
```
**When the copy constructor Is called**
 1.	pass-by-value
 2.	Whenever you return an object from a function or method.

**Calling the copy constructor explicitly**  
You can use the copy constructor explicitly
``` cpp
SpreadsheetCell myCell3(myCell2); 
// myCell3 has the same values as myCell2
```

**Initializer-List Constructors**
An initializer-list constructor is a constructor with ``` std::initializer_list<T> ``` as fi rst argument, without any additional arguments or with additional arguments having default values. Before you can use the ``` std::initializer_list<T> ``` template you need to include the ``` <initializer_list> ``` header.
``` cpp
class PointSequence {
public:
   PointSequence(initializer_list<double> args) {
      if (args.size() % 2 != 0) {
         throw invalid_argument("initializer_list should " "contain even number of elements.");
      }

      for (auto iter = args.begin(); iter != args.end(); ++iter)
         mVecPoints.push_back(*iter);
   }
   
   void dumpPoints() const {
      for (auto citer = mVecPoints.cbegin();
         citer != mVecPoints.cend(); citer += 2) {
         cout << "(" << *citer << ", " << *(citer+1) << ")" << endl;
      }
   }
protected:
   vector<double> mVecPoints;
};

PointSequence p1 = {1.0, 2.0, 3.0, 4.0, 5.0, 6.0};
p1.dumpPoints();
try {
   PointSequence p2 = {1.0, 2.0, 3.0};
} 
catch (const invalid_argument& e) {
   cout << e.what() << endl;
}
```

**In-Class member initializers**
Before C++11, only static const integral member variables could be initialized in the class definition.
``` cpp
#include <string>
class MyClass {
protected:
   static const int kI1 = 1; // OK
   static const std::string kStr = "test"; // Error: not integral type
   static int sI2 = 2; // Error: not const
   const int kI3 = 3; // Error: not static
};
```

**Delegating Constructors**
Delegating constructors allow constructors to call another constructor from the same class. However, this call cannot be placed in the constructor body; it should be in the constructor initializer.
When this string constructor (the delegating constructor) is called, it will fi rst delegate the call to the target, double constructor. When the target constructor returns, the body of the delegating constructor will be executed.
``` cpp
SpreadsheetCell::SpreadsheetCell(const string& initialValue)
: SpreadsheetCell(stringToDouble(initialValue)) {
}
```

**Copy constructor**
If you only define A copy constructor only, no default constructor generated by the compiler. As long as you don’t define a copy constructor explicitly, the compiler creates one for you. On the other hand, as soon as you define any constructor, the compiler stops generating a default constructor.

**Destruction**
Objects on the stack are destroyed in the reverse order of their declaration Objects on the stack are destroyed in the reverse order of their declaration. In the following code fragment, myCell2 is allocated before anotherCell2, so anotherCell2 is destroyed before myCell2
``` cpp
{
   SpreadsheetCell myCell2(4);
   SpreadsheetCell anotherCell2(5); // myCell2 constructed before anotherCell2
} // anotherCell2 destroyed before myCell2
```
**Assignment Operator**
``` cpp
class SpreadsheetCell
{
public:
   // Remainder of the class definition omitted for brevity
   SpreadsheetCell& operator=(const SpreadsheetCell& rhs);
   // Remainder of the class definition omitted for brevity
};
```

Your assignment operator shouldn’t prohibit self-assignment, but also shouldn’t perform a full assignment if it happens. Thus, assignment operators should check for self-assignment at the beginning of the method and return immediately.
``` cpp
SpreadsheetCell& SpreadsheetCell::operator=(const SpreadsheetCell& rhs)
{
   if (this == &rhs) 
   {
      return *this;
   }
}
```

**Distinguishing Copying from Assignment**
The following constructed with the copy constructor, because this is a declaration
``` cpp
SpreadsheetCell myCell(5);
SpreadsheetCell anotherCell(myCell);
SpreadsheetCell aThirdCell = myCell;
```
However:
``` cpp
anotherCell = myCell; // Calls operator= for anotherCell.
```
Here anotherCell has already been constructed, so the compiler calls operator=

**Objects as Return Values**
``` cpp
SpreadsheetCell myCell2(5);
string s1;
s1 = myCell2.getString();
```
When getString() returns mString, the compiler actually creates an unnamed temporary string object by calling a string copy constructor. When you assign this result to s1, the assignment operator is called for s1 with the temporary string as a parameter. Then, the temporary string object is destroyed. Thus, the single line of code invokes the copy constructor and the assignment operator (for two different objects).
Consider this code:
``` cpp
SpreadsheetCell myCell3(5);
string s2 = myCell3.getString();
```
In this case, getString() still creates a temporary unnamed string object when it returns mString. But now s2 gets its copy constructor called, not its assignment operator. With move semantics from C++11, the compiler can use a move constructor instead of a copy constructor to return mString from getString(). This is much more efficient.

**2D Array allocation and Visualization**
``` cpp
Spreadsheet::Spreadsheet(int inWidth, int inHeight) : 
mWidth(inWidth), mHeight(inHeight) {
   mCells = new SpreadsheetCell* [mWidth];
   for (int i = 0; i < mWidth; i++) {
      mCells[i] = new SpreadsheetCell[mHeight];
   }
}
```
The resultant memory for a Spreadsheet called s1 on the stack with width four and height three is shown
![Memory](https://github.com/amroibrahim/Notes/blob/master/Images/CPP/Memory1.png)  

**Assignment operators must free memory first**
![Memory](https://github.com/amroibrahim/Notes/blob/master/Images/CPP/Memory2.png)  

Not only do the mCells pointers in s1 and s2 point to the same memory, but also you have orphaned the memory to which mCells in s1 previously pointed. That is why in assignment operators you must fi rst free the memory referenced by the left-hand side, and then do a deep copy. (Whenever you have dynamically allocated memory in a class, you should write your own copy constructor and assignment operator to provide a deep copy of the memory.)

**Assignment operator self-check**
The first lines of code in any assignment operator checks for self-assignment.
This self-assignment check is required, not only for effi ciency, but also for correctness. If the preceding self-assignment test was removed, the code will most likely crash on self-assignment, because the second step in the code deletes mCells for the left-hand side and afterwards copies mCells from the right-hand side to the left-hand side. In the case of self-assignment, both sides are the same, so during copying you would access dangling pointers.
``` cpp
Spreadsheet& Spreadsheet::operator=(const Spreadsheet& rhs) {
   // Check for self-assignment.
   if (this == &rhs) {
      return *this;
   }
   
   for (int i = 0; i < mWidth; i++) {
      delete [] mCells[i];
   }
   delete [] mCells;
   mCells = nullptr;
…
}
```

The assignment operator completes the "big 3" routines for managing dynamically allocated memory in an object: the destructor, the copy constructor, and the assignment operator.  Whenever you find yourself writing one of those methods you should write all of them. (Whenever a class dynamically allocates memory, write a destructor, copy constructor, and assignment operator.)

**Smart Pointers**
There are three smart pointer types in C++:
``` cpp
  std::unique_ptr
  std::shared_ptr
  std::weak_ptr
```
The unique_ptr is analogous to an ordinary pointer, except that it will automatically free the memory or resource when the unique_ptr goes out of scope or is deleted. A unique_ptr has sole ownership of the object pointed to. One advantage of the unique_ptr is that it simplifies coding where storage must be freed when an exceptional situation occurs. unique_ptr is a generic smart pointer that can point to any kind of memory. That’s why it is a template.  
  
shared_ptr allows for distributed "ownership" of the data. Each time a shared_ptr is assigned, a reference count is incremented indicating there is one more "owner" of the data. When a shared_ptr goes out of scope, the reference count is decremented. When the reference count goes to zero it means there is no longer any owner of the data, and the object referenced by the pointer is freed. You cannot store an array in a shared_ptr. Use std::make_shared<>() to create a shared_ptr.  
  
You can use weak_ptr to observe a shared_ptr without incrementing or decrementing the reference count of the linked shared_ptr.  
``` cpp
auto myCellp = make_unique<SpreadsheetCell>();
// Equivalent to:
unique_ptr<SpreadsheetCell> myCellp(new SpreadsheetCell());
```
**Static Data Members**
Static Data Members  are initialized to 0 by default. Static pointers are initialized to nullptr. (When using Static variable for assigning and ID to each class in constructor, remember to assign and ID in the copy constructor too (Page 182)
You should not copy the ID in the assignment operator. Once an ID is assigned to an object it should never change.)

**const Data Members**
const data members are usually static as well. You should use static const data members in place of global constants when the constants apply only to the class.

**Exception**
The destructor will not be called when you throw an exception from a constructor.

**Using ternary operator in constructor**  
``` cpp
Spreadsheet::Spreadsheet(int inWidth, int inHeight) :
mWidth(inWidth < kMaxWidth ? inWidth : kMaxWidth),
mHeight(inHeight < kMaxHeight ? inHeight : kMaxHeight) {
   mId = sCounter++;
   mCells = new SpreadsheetCell* [mWidth];
   for (int i = 0; i < mWidth; i++) {
      mCells[i] = new SpreadsheetCell[mHeight];
   }
}
```

**reference members**
You must initialize the reference member in constructors and copy constructor. Remember that after you have initialized a reference you cannot change the object to which it refers. Thus, you do not need to attempt to assign to references in the assignment operator.
There is an important difference between using a const reference versus a non-const reference. The const reference SpreadsheetApplication data member can only be used to call const methods on the SpreadsheetApplication object. If you try to call a non-const method through a const reference, you will get a compiler error.

**Static Const Functions**
You also cannot declare a static method const because it is redundant. Static methods do not have an instance of the class so it would be impossible for them to change internal values. const works by making it appear inside the method that you have a const reference to each data member.

**Method Overloading**
You can overload a method based on const. That is, you can write two methods with the same name and same parameters, one of which is declared const and one of which is not. The compiler will call the const method if you have a const object and the non-const method if you have a non-const object. 
Overloaded methods can be explicitly deleted, which can be used to disallow calling a member function with particular parameters. For example, suppose you have the following class:
``` cpp
class MyClass
{
public:
   void foo(int i);
};

MyClass c;
c.foo(123);
c.foo(1.23);
```
For the second line, the compiler will convert the double value (1.23) to an integer value (1) and then call foo(int i). The compiler might give you a warning, but it will perform this implicit conversion. You can prevent the compiler from performing this conversion by explicitly deleting a double instance of foo():
``` cpp
class MyClass
{
public:
   void foo(int i);
   void foo(double d) = delete;
};
```
With this change, an attempt to call foo() with a double will be flagged as an error by the compiler, instead of performing a conversion to an integer.

**Friends**
Friend classes and methods are easy to abuse; they allow you to violate the principle of abstraction by exposing internals of your class to other classes or functions. Thus, you should use them only in limited circumstances such as operator overloading because in that case you need access to protected and private members, as discussed in the next section.

**Operator overloading**
``` cpp
class SpreadsheetCell {
public:
   // Omitted for brevity
   const SpreadsheetCell operator+(const SpreadsheetCell& cell) const;
   // Omitted for brevity
};
```
Implicit Conversions: once you’ve written the operator+ shown earlier, not only can you add two cells together, you can also add a cell to a string, a double, or an int! You can prevent the implicit construction of a SpreadsheetCell from a string by marking that constructor with the explicit keyword.

``` cpp
class SpreadsheetCell {
public:
   SpreadsheetCell();
   SpreadsheetCell(double initialValue);
   explicit SpreadsheetCell(const string& initialValue);
   SpreadsheetCell(const SpreadsheetCell& src);
   SpreadsheetCell& operator=(const SpreadsheetCell& rhs);
   // Remainder omitted for brevity
};
```

``` cpp
aThirdCell = myCell + 4; // Works fine.
aThirdCell = myCell + 5.6; // Works fine.
aThirdCell = 4 + myCell; // FAILS TO COMPILE!
aThirdCell = 5.6 + myCell; // FAILS TO COMPILE!
```

You can get it to work if you replace the in-class operator+ with a global operator+ function that is not tied to any particular object. The function looks like this:
``` cpp
const SpreadsheetCell operator+(const SpreadsheetCell& lhs,
                                const SpreadsheetCell& rhs) {
   SpreadsheetCell newCell;
   newCell.set(lhs.mValue + rhs.mValue); // update mValue and mString.
   return newCell;
}
```

Note that the implementation of the global operator+ accesses protected data members of SpreadsheetCell objects. Therefore, it must be a friend function of the SpreadsheetCell class:
``` cpp
class SpreadsheetCell {
public:
   // Omitted for brevity
   friend const SpreadsheetCell operator+(const SpreadsheetCell& lhs,
      const SpreadsheetCell& rhs);
   //Omitted for brevity
};
```
In classes with more data members, it might be painful to compare each data member. However, once you’ve implemented == and <, you can write the rest of the comparison operators in terms of those two. For example, here is a defi nition of operator>= that uses operator<
``` cpp
bool operator>=(const SpreadsheetCell& lhs, const SpreadsheetCell& rhs) {
   return !(lhs < rhs);
}
```
**Using Interface and Implementation Classes (expose only public members)**
The basic principle is to define two classes for every class you want to write: the interface class and the implementation class. The implementation class is identical to the class you would have written if you were not taking this approach. The interface class presents public methods identical to those of the implementation class, but it only has one data member: a pointer to an implementation class object. The interface class method implementations simply call the equivalent methods on the implementation class object.
``` cpp
class SpreadsheetApplication; // Forward declaration
class SpreadsheetImpl {
public:
   SpreadsheetImpl(const SpreadsheetApplication& theApp,
      int inWidth = kMaxWidth, int inHeight = kMaxHeight);
   SpreadsheetImpl(const SpreadsheetImpl& src);
   ~SpreadsheetImpl();
   SpreadsheetImpl &operator=(const SpreadsheetImpl& rhs);
   void setCellAt(int x, int y, const SpreadsheetCell& inCell);
   SpreadsheetCell getCellAt(int x, int y);
   int getId() const;
   static const int kMaxHeight = 100;
   static const int kMaxWidth = 100;
protected:
   bool inRange(int val, int upper);
   void copyFrom(const SpreadsheetImpl& src);
   int mWidth, mHeight;
   int mId;
   SpreadsheetCell** mCells;
   const SpreadsheetApplication& mTheApp;
   static int sCounter;
};

class SpreadsheetApplication;
class Spreadsheet {
public:
   Spreadsheet(const SpreadsheetApplication& theApp, int inWidth,
      int inHeight);
   Spreadsheet(const SpreadsheetApplication& theApp);
   Spreadsheet(const Spreadsheet& src);
   ~Spreadsheet();
   Spreadsheet& operator=(const Spreadsheet& rhs);
   void setCellAt(int x, int y, const SpreadsheetCell& inCell);
   SpreadsheetCell getCellAt(int x, int y);
   int getId() const;
protected:
   SpreadsheetImpl* mImpl;
};

void Spreadsheet::setCellAt(int x, int y, const SpreadsheetCell& inCell) {
   mImpl->setCellAt(x, y, inCell);
}

SpreadsheetCell Spreadsheet::getCellAt(int x, int y) {
   return mImpl->getCellAt(x, y);
}

int Spreadsheet::getId() const {
   return mImpl->getId();
}

Spreadsheet::Spreadsheet(const SpreadsheetApplication& theApp, int inWidth,
                         int inHeight) {
   mImpl = new SpreadsheetImpl(theApp, inWidth, inHeight);
}

Spreadsheet::Spreadsheet(const SpreadsheetApplication& theApp) {
   mImpl = new SpreadsheetImpl(theApp);
}

Spreadsheet::Spreadsheet(const Spreadsheet& src) {
   mImpl = new SpreadsheetImpl(*(src.mImpl));
}

Spreadsheet::~Spreadsheet() {
   delete mImpl;
   mImpl = nullptr;
}

```
The copy constructor looks a bit strange because it needs to copy the underlying SpreadsheetImpl from the source spreadsheet. Because the copy constructor takes a reference to a SpreadsheetImpl, not a pointer, you must dereference the mImpl pointer to get to the object itself so the constructor call can take its reference. The Spreadsheet assignment operator must similarly pass on the assignment to the underlying SpreadsheetImpl:
``` cpp
Spreadsheet& Spreadsheet::operator=(const Spreadsheet& rhs)
{
   *mImpl = *(rhs.mImpl);
   return *this;
}
```

**Preventing Inheritance** C++11 only
C++11 allows you to mark a class as final, which means trying to inherit from it will result in a compiler error.
``` cpp
class Super final {
   // Omitted for brevity
};
```

**Preventing Overriding** C++11 only
C++11 allows you to mark a method as final which means that the method cannot be overridden in a subclass. Trying to override a final method will result in a compiler error.
``` cpp
class Super {
public:
   Super();
   virtual void someMethod() final;
};
```
**Parent Constructors**
C++ defines the creation order as follows:
 1.	If the class has a base class, the default constructor of the base class is executed, unless there is a call to a base class constructor in the ctor-initializer in which case that constructor is called instead of the default constructor.
 2.	Non-static data members of the class are constructed in the order in which they were declared.
 3.	The body of the class’s constructor is executed.
**WARNING** Virtual methods behave differently in constructors. If your derived class has overridden a virtual method from the base class, calling that method from a base class constructor will call the base class implementation of that virtual method and not your overridden version in the derived class.
These rules can apply recursively. If the class has a grandparent, the grandparent is initialized before the parent, and so on.
``` cpp
class Something {
public:
   Something() { cout << "2"; }
};

class Parent {
public:
   Parent() { cout << "1"; }
};

class Child : public Parent {
public:
   Child() { cout << "3"; }
protected:
   Something mDataMember;
};

int main() {
   Child myChild;
   return 0;
}
```
The proper execution will output the result 123.
When the myChild object is created, the constructor for Parent is called fi rst, outputting the string "1". Next, mDataMember is initialized, calling the Something constructor, which outputs the string "2". Finally, the Child constructor is called, which outputs "3".

Passing constructor arguments from the subclass to the superclass is perfectly fi ne and quite normal. Passing data members, however, will not work. The code will compile, but remember that data members are not initialized until after the superclass is constructed. If you pass a data member as an argument to the parent constructor, it will be uninitialized.

•	Parent Destructors
Because destructors cannot take arguments, the language can automatically call the destructor for parent classes. The order of destruction is conveniently the reverse of the order of construction:
1.	The body of the class’s destructor is called.
2.	Any data members of the class are destroyed in the reverse order of their construction.
3.	The parent class, if any, is destructed.
**WARNING**Just as with constructors, virtual methods behave differently when called from a destructor. If your derived class has overridden a virtual method from the base class, calling that method from the base class destructor will call the base class implementation of that virtual method and not your overridden version in the derived class.  
These rules apply recursively. The lowest member of the chain is always destructed first.
``` cpp
class Something {
public:
   Something() { cout << “2”; }
   virtual ~Something() { cout << “2”; }
};

class Parent {
public:
   Parent() { cout << “1”; }
   virtual ~Parent() { cout << “1”; }
};

class Child : public Parent {
public:
   Child() { cout << “3”; }
   virtual ~Child() { cout << “3”; }
protected:
   Something mDataMember;
};

int main() {
   Child myChild;
   return 0;
}
```
If executed, this code will output "123321".
  
**Non-Virtual Destructors** 
```
Always make your destructors virtual! The compiler generated default destructor is not virtual, so you should define your own virtual destructor, at least for your parent classes.
```
All destructors should be declared virtual. If the preceding destructors were not declared virtual, the code would continue to work fi ne. However, if code ever called delete on a superclass pointer that was really pointing to a subclass, the destruction chain would begin in the wrong place. For example, the following code is similar to the previous example but the destructors are not virtual. This becomes a problem when a Child object is accessed as a pointer to a Parent and deleted.
``` cpp
class Something {
public:
   Something() { cout << “2”; }
   ~Something() { cout << “2”; } // Should be virtual, but will work
};

class Parent {
public:
   Parent() { cout << “1”; }
   ~Parent() { cout << “1”; } // BUG! Make this virtual!
};

class Child : public Parent {
public:
   Child() { cout << “3”; }
   ~Child() { cout << “3”; } // Should be virtual, but will work
protected:
   Something mDataMember;
};

int main() {
   Parent* ptr = new Child();
   delete ptr;
   return 0;
}
```
The output of this code is a shockingly terse "1231".

**Referring to Parent Names** 
```
Microsoft Visual C++ supports the __super keyword (with two underscores).
This allows you to write the following:
return __super::getTemperature() + "\u00B0F";
```
``` cpp
string MyWeatherPrediction::getTemperature() const
{
   // Note: \u00B0 is the ISO/IEC 10646 representation of the degree symbol.
   return WeatherPrediction::getTemperature() + "\u00B0F";
}
```
