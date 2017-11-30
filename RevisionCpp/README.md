# Revision notes of Cpp


## Revision Questions

1.	**What are the differences between high and low level programing languages?**

|High|Low|
|---|---|
|Abstraction from the complex|Little or no abstraction from a computer's ISA|
|More structured & intuitive| |
|Easier to read| |
|Works across OS| |
|Ordinary/Natural Language|Machine Language|
|C++, Java, Python|Assembly Language|

2.	**What are the roles of the pre-processor, compiler and linker?**  

First, the C **preprocessor** cpp expands all those macros definitions and include statements (and anything else that starts with a #) and passes the result to the actual compiler.  
The **compiler** effectively translates preprocessed C code into assembly code, performing various optimizations along the way as well as register allocation.  
The **linker** produces a binary executable that can be run from the command interface.  
[Reference](https://courses.cs.washington.edu/courses/cse378/97au/help/compilation.html)

3.	**What is the difference between implicit and explicit casting of variables?**

Converting an expression of a given type into another type is known as *type-casting*.  
Implicit conversions do not require any operator. They are automatically performed when a value is copied to a compatible type.  
C++ is a strong-typed language. Many conversions, specially those that imply a different interpretation of the value, require an explicit conversion.  
```cpp
short a=2000;
int b;
b = (int) a;    // c-like cast notation
b = int (a);    // functional notation 
```

4.	**If ```a = 5, b = 6, c = 8, d = 2``` what will be the value of ```e``` after this operation?**
```cpp
e = a > b ? c : d; // 2
```


5.	**Consider precedence bracket the operations below in the order the are executed:**
```cpp
a + b * c – d // *+-
a > b ? a : c > d ? e : f // >?: >?:
```

6.	**What are pre-processor directives?**

Preprocessor directives are lines included in a program that being with the character #, which make them different from a typical source code text. They are invoked by the compiler to process some programs before compilation. Preprocessor directives change the text of the source code and the result is a new source code without these directives.  
[Reference](https://www.techopedia.com/definition/24295/preprocessor-directive)

7.	**Describe the purpose of the element in a simple C++ program:**
```cpp
// Hello, World! Example
#include <iostream>
using namespace std;
int main()
{
    std::cout << “Hello, World!” << std::endl;
    return 0;
}
```
\# - Pre-processor syntax  
\#include\<iostream\> - Header Inclusion  
Namespaces contain a set of functions in one set to avoid variable clashes. Namespace is a method for differentiating similar entities coming from different developmental efforts

8.	**What is the difference between ‘global’ and ‘automatic’ variables?**

A **global variable** is a variable that is defined outside all functions and available to all functions.  
For **automatic variables**, specifies that the type of the variable that is being declared will be automatically deduced from its initializer.  
[Reference](http://faculty.cs.niu.edu/~freedman/241/241notes/241var2.htm)

9.	**What is operator precedence?**

[Reference1](https://msdn.microsoft.com/en-us/library/126fe14k.aspx)  
[Reference2](http://en.cppreference.com/w/cpp/language/operator_precedence)

10.	**Consider the two operations below. What will be the value of i, j and k after each step?**
 ```cpp
 int i{ 5 }, j{ 5 }, k{};
 k++; // invalid
 k = ++i + j; // 11
 k = i++ + j; // 11
 k += --j; // 15
 k /= ++j // 2
 ```
 
11.	**Explain the conditional operator and how it works on the code below:**
```cpp
 int i{ 5 }, j{ 10 }, k{};
 k = i > j ? i : j; // 10
 ```
 
12.	**What are ‘nested loops’? When and how are they used?**

A *nested loop* is a loop within a loop, an inner loop within the body of an outer one. How this works is that the first pass of the outer loop triggers the inner loop, which executes to completion. Then the second pass of the outer loop triggers the inner loop again. This repeats until the outer loop finishes. Of course, a *break* within either the inner or outer loop would interrupt this process.  

13.	**Explain the use and differences between ```if/elseif/else``` statements and ```switch/case``` statements.**

* Switch
    * ```switch``` is usually more compact than lots of nested ```if else``` and therefore, more readable.
    * If you omit the ```break``` between two switch cases, you can fall through to the next case in many C-like languages. With ```if else``` you'd need a goto (which is not very nice to your readers ... if the language supports ```goto``` at all).
    * In most languages, ```switch``` only accepts primitive types as key and constants as cases. This means it can be optimized by the compiler using a jump table which is very fast.
    * In many languages, switch only accepts only some data types.
* If-else
    * ```if``` allows complex expressions in the condition while switch wants a constant.
    * You can't accidentally forget the ```break``` between ```if```s but you can forget the ```else``` (especially during cut'n'paste).
    * it accepts all data types.

14.	**What is ```nullptr``` ?**

The ```nullptr``` keyword represents a null pointer value. Use a ```null pointer``` value to indicate that an object handle, interior pointer, or native pointer type does not point to an object.  
Use ```nullptr``` with either managed or native code. The compiler emits appropriate but different instructions for managed and native null pointer values. For information about using the ISO standard C++ version of this keyword, see [nullptr](https://docs.microsoft.com/zh-cn/cpp/cpp/nullptr).  
[Reference](http://en.cppreference.com/w/cpp/language/nullptr)

15.	**What is the difference between the ‘stack’ and the ‘heap’?**

* Stack Memory  

This type of memory stores all the local variables and the function calls made in a program.  
Normal variable declarations like,  
 ```cpp
int a;
int b[5];
 ```
happen in Stack Memory during compile time.  
Stack Memory is generally small in size(```usually less than 8MB```).  
Small size of the Stack Memory leads to memory overflow in situations where we try to use large amount of space(declare really large arrays or an array of a structure) or in recursive programs where the depth of recursion becomes really large( because function calls are also stored in the Stack Memory) and hence we get a Segmentation Fault.  

* Heap Memory  

Heap Memory on the other hand is used in case of dynamic allocations( ```mallocs``` ) like,
 ```cpp
int *a = (int*)malloc(length*sizeof(int));
 ```
Size of the Heap Memory is only limited by the size of the RAM and the swap memory. Memory allocation happens at runtime.  
This is like a free pool of memory for programs from which they can request some space for their use and then put it back in the pool( using ```free()```).  
Heap memory is mostly used in situations where large amount of memory is needed(when Stack Memory is not enough).

16.	**How do you allocate / deallocate dynamic memory?**

Dynamic memory is allocated using operator ```new```. ```new``` is followed by a data type specifier and, if a sequence of more than one element is required, the number of these within brackets []. It returns a pointer to the beginning of the new block of memory allocated. Its syntax is: 
```cpp
pointer = new type
pointer = new type [number_of_elements]
 ```
The first expression is used to allocate memory to contain one single element of type ```type```. The second one is used to allocate a block (an array) of elements of type ```type```, where ```number_of_elements``` is an integer value representing the amount of these. 

In most cases, memory allocated dynamically is only needed during specific periods of time within a program; once it is no longer needed, it can be freed so that the memory becomes available again for other requests of dynamic memory. This is the purpose of operator ```delete```, whose syntax is:
```cpp
delete pointer;
delete[] pointer;
```
The first statement releases the memory of a single element allocated using ```new```, and the second one releases the memory allocated for arrays of elements using new and a size in brackets ([]).

17.	**What is function overloading? When is it useful?**

**Function overloading** is the process of using the same name for two or more functions. The secret to overloading is that each redefinition of the function must use either different types of parameters or a different number of parameters. It is only through these differences that the compiler knows which function to call in any given situation.  
The concept of functions overloading is also known as **Polymorphism**. Function overloading is used within the class concept for constructors and member functions. Advantages of function overloading:
* The function can perform different operations and hence eliminates the use of different function names for the same kind of operations.
* Program becomes easy to understand.
* Easy maintainability of the code.
* Function overloading brings flexibility in C++ programs.

18.	**What are function templates? When and how are they used?**

In C++, **function templates** are functions that serve as a pattern for creating other similar functions. The basic idea behind function templates is to create a function without having to specify the exact type(s) of some or all of the variables. Instead, we define the function using placeholder types, called **template type parameters**. Once we have created a function using these placeholder types, we have effectively created a “function stencil”. [Reference](http://en.cppreference.com/w/cpp/language/function_template)  
When you call a template function, the compiler “stencils” out a copy of the template, replacing the placeholder types with the actual variable types from the parameters in your function call! Using this methodology, the compiler can create multiple “flavors” of a function from one template! Using a function template is extremely straightforward -- you can use it just like any other function. Here’s a full program using our template function:  
```cpp
#include <iostream>
 
template <typename T>
const T& max(const T& x, const T& y)
{
    return (x > y) ? x : y;
}
 
int main()
{
    int i = max(3, 7); // returns 7
    std::cout << i << '\n';
 
    double d = max(6.34, 18.523); // returns 18.523
    std::cout << d << '\n';
 
    char ch = max('a', '6'); // returns 'a'
    std::cout << ch << '\n';
 
    return 0;
}
```


19.	**What are exceptions? How do you handle exceptions?**

An exception is a problem that arises during the execution of a program. A C++ exception is a response to an exceptional circumstance that arises while a program is running, such as an attempt to divide by zero.  
Exceptions provide a way to transfer control from one part of a program to another. C++ exception handling is built upon three keywords: **try**, **catch**, and **throw**.
* throw − A program throws an exception when a problem shows up. This is done using a throw keyword.
* catch − A program catches an exception with an exception handler at the place in a program where you want to handle the problem. The catch keyword indicates the catching of an exception.
* try − A try block identifies a block of code for which particular exceptions will be activated. It's followed by one or more catch blocks.
```cpp
#include <iostream>
using namespace std;

double division(int a, int b) {
   if( b == 0 ) {
      throw "Division by zero condition!";
   }
   return (a/b);
}

int main () {
   int x = 50;
   int y = 0;
   double z = 0;
 
   try {
      z = division(x, y);
      cout << z << endl;
   } catch (const char* msg) {
     cerr << msg << endl;
   }

   return 0;
}
```

20.	**What are user defined data types?**


21.	**What are enumerators?**


22.	**What are the differences between classes and structures?**


23.	**Consider an object oriented program for a temperature controller. What objects could use to do this? What methods and attributes would these objects have?**


24.	**What are class constructors? How and why are they used?**
25.	**What access keywords are used in functions and what do they do?**
26.	**What are Class destructors and what do they do?**
27.	**How can you encapsulate dynamic memory allocation in an object?**
28.	**What is operator overloading, why and how is it used?**
29.	**What is class inheritance, what is advantages does it have?**
30.	**How to class access keywords relate to inheritance?**
31.	**What are virtual functions in classes?**
32.	**What are STL containers? What are the advantages of using containers?**
33.	**What are STL Iterators? How are they used?**
34.	**What are Smart pointers? How do they differ from ‘raw’ pointers?**
35.	**What is the difference between an unique pointer and a shared pointer?**
36.	**What is the difference between the ‘size’ and ‘capacity’ of a vector?**
37.	**What does the reserve method do in a vector?  When is it advantageous to use it?**
38.	**What are containers?**
39.	**What are the differences between sequence containers and associative containers?**
40.	**What are the main features of (and differences) of vector, deque and list containers.**
41.	**What does double linking in a list mean?**
42.	**What are map objects?**
43.	**What are iterators and how are they used?**
44.	**Using the ```std::multiplies<>()``` functor and the ```std::transform<>()```  algorithm multiply the element 0 to 20 of ```numbersA``` with element 10 to 30 of ```numbersB``` and save the result on element 0:20 of ```numbersC```.**
```cpp
std::vector < int >  numbersA(100);
std::vector < int >  numbersB(100);
std::vector < int >  numbersC(100);
// binary transform declaration
Output Iterator transform(InputIterator begin1, InputIteraotr end1, 
InputIterator begin2, OutputIterator result, biary function f);
```
45.	**What is event based programing?**

46.	**What are the differences between windows applications and console applications?**

47.	**What are windows messages? How are they handled?**

48.	**What is event based programing?**

49.	**What are the differences between windows applications and console applications?**

