# Revision notes of Cpp


# Examplar 

1.	What are the differences between high and low level programing languages?

2.	What are the roles of the pre-processor, compiler and linker?

3.	What is the difference between implicit and explicit casting of variables?

4.	If ```a = 5, b = 6, c = 8, d = 2``` what will be the value of ```e``` after this operation?
```cpp
e = a > b ? c : d;
```

5.	Consider precedence bracket the operations below in the order the are executed: 
```cpp
a + b * c – d
a > b ? a : c > d ? e : f
```

6.	What are pre-processor directives?

7.	Describe the purpose of the element in a simple C++ program:
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

8.	What is the difference between ‘global’ and ‘automatic’ variables?

9.	What is operator precedence?

10.	Consider the two operations below. What will be the value of i, j and k after each step?
 ```cpp
 int i{ 5 }, j{ 5 }, k{};
 k++;
 k = ++i + j;
 k = i++ + j;
 k += --j;
 k /= ++j
 ```
 
11.	Explain the conditional operator and how it works on the code below:
```cpp
 int i{ 5 }, j{ 10 }, k{};
 k = i > j ? i : j;
 ```
 
12.	What are ‘nested loops’? When and how are they used?

13.	Explain the use and differences between ```if/elseif/else``` statements and ```switch/case``` statements.
14.	What is ```nullptr``` ?
15.	What is the difference between the ‘stack’ and the ‘heap’?
16.	How do you allocate / deallocate dynamic memory?
17.	What is function overloading? When is it useful?
18.	What are function templates? When and how are they used?
19.	What are exceptions? How do you handle exceptions?
20.	What are user defined data types?
21.	What are enumerators?
22.	What are the differences between classes and structures?	
23.	Consider an object oriented program for a temperature controller. What objects could use to do this? What methods and attributes would these objects have? 
24.	What are class constructors? How and why are they used?
25.	What access keywords are used in functions and what do they do?
26.	What are Class destructors and what do they do?
27.	How can you encapsulate dynamic memory allocation in an object?
28.	What is operator overloading, why and how is it used?
29.	What is class inheritance, what is advantages does it have?
30.	How to class access keywords relate to inheritance?
31.	What are virtual functions in classes?
32.	What are STL containers? What are the advantages of using containers?
33.	What are STL Iterators? How are they used?
34.	What are Smart pointers? How do they differ from ‘raw’ pointers?
35.	What is the difference between an unique pointer and a shared pointer?
36.	What is the difference between the ‘size’ and ‘capacity’ of a vector?
37.	What does the reserve method do in a vector?  When is it advantageous to use it?
38.	What are containers?
39.	What are the differences between sequence containers and associative containers?
40.	What are the main features of (and differences) of vector, deque and list containers.
41.	What does double linking in a list mean?
42.	What are map objects?
43.	What are iterators and how are they used? 
44.	Using the ```std::multiplies<>()``` functor and the ```std::transform<>()```  algorithm multiply the element 0 to 20 of ```numbersA``` with element 10 to 30 of ```numbersB``` and save the result on element 0:20 of ```numbersC```. 
```cpp
std::vector < int >  numbersA(100);
std::vector < int >  numbersB(100);
std::vector < int >  numbersC(100);
// binary transform declaration
Output Iterator transform(InputIterator begin1, InputIteraotr end1, 
InputIterator begin2, OutputIterator result, biary function f);
```
45.	What is event based programing?

46.	What are the differences between windows applications and console applications?

47.	What are windows messages? How are they handled?

48.	What is event based programing?

49.	What are the differences between windows applications and console applications?

