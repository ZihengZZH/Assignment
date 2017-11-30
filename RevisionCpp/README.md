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

C++ allows us to define our own types based on other existing data types. In order to do that we shall use keyword ```typedef```, whose form is:
```cpp
typedef   existing_type   new_type_name ;
```
where ```existing_type``` is a C++ fundamental or any other defined type and ```new_type_name``` is the name that the new type we are going to define will receive. For example:
```cpp
typedef char C;
typedef unsigned int WORD;
typedef char * string_t;
typedef char field [50];
```
In this case we have defined four new data types: ```C```, ```WORD```, ```string_t``` and ```field``` as ```char```, ```unsigned int```, ```char*``` and ```char[50]``` respectively, that we could perfectly use later as valid types:
```cpp
C achar, anotherchar, *ptchar1;
WORD myword;
string_t ptchar2;
field name;
```
```typedef``` can be useful to define a type that is repeatedly used within a program and it is possible that we will need to change it in a later version, or if a type you want to use has too long a name and you want it to be shorter.

21.	**What are enumerators?**

An enumeration is a user-defined type that consists of a set of named integral constants that are known as enumerators. Each enumerator becomes a named constant of the enumeration's type (that is, name), visible in the enclosing scope, and can be used whenever constants are required.
```cpp
enum Foo { a, b, c = 10, d, e = 1, f, g = f + c };
//a = 0, b = 1, c = 10, d = 11, e = 1, f = 2, g = 12

enum color { red, yellow, green = 20, blue };
color col = red;
int n = blue; // n == 21

enum { a, b, c = 0, d = a + 2 }; // defines a = 0, b = 1, c = 0, d = 2
```

22.	**What are the differences between classes and structures?**

||Class|Structure|
|:--------------------------|:--------------|:----------------|
|Definition|A class in C++ can be defined as a collection of related variables and functions encapsulated in a single structure.|A structure can be referred to as a user defined data type possessing its own operations.|
|Keyword for declaration|Class|Struct|
|Default access specifier|Private|Public|
|Purpose|Data abstraction and further inheritance|Generally, grouping of data|
|Type|Reference|Value|
|Usage|Generally used for large amounts of data.|Generally used for smaller amounts of data.|


23.	**Consider an object oriented program for a temperature controller. What objects could use to do this? What methods and attributes would these objects have?**

```cpp
class controller {

private:
	int threshold;
	int temperature;
	bool open;

public:
	int getTemperature();
	void doesReach();
	void heat();

};
```

24.	**What are class constructors? How and why are they used?**

* Constructors

A class **constructor** is a special member function of a class that is executed whenever we create new objects of that class. A constructor will have exact same name as the class and it does not have any return type at all, not even void. Constructors can be very useful for setting initial values for certain member variables. A default constructor does not have any parameter, but if you need, a constructor can have parameters. This helps you to assign initial value to an object at the time of its creation.  

* Destructors

A **destructor** is a special member function of a class that is executed whenever an object of it's class goes out of scope or whenever the delete expression is applied to a pointer to the object of that class. A destructor will have exact same name as the class prefixed with a tilde (~) and it can neither return a value nor can it take any parameters. Destructor can be very useful for releasing resources before coming out of the program like closing files, releasing memories etc.  

25.	**What access keywords are used in functions and what do they do?**

Data hiding is one of the important features of Object Oriented Programming which allows preventing the functions of a program to access directly the internal representation of a class type. The access restriction to the class members is specified by the labeled public, private, and protected sections within the class body. The keywords **public**, **private**, and **protected** are called access specifiers.  
A class can have multiple public, protected, or private labeled sections. Each section remains in effect until either another section label or the closing right brace of the class body is seen. The default access for members and classes is private.  

|Access|public|protected|private|
|------|:----:|:------:|:----:|
|Same class|YES|YES|YES|
|Derived class|YES|YES|NO|
|Outside class|YES|NO|NO|

26.	**What are Class destructors and what do they do?**

* Constructors

A class **constructor** is a special member function of a class that is executed whenever we create new objects of that class. A constructor will have exact same name as the class and it does not have any return type at all, not even void. Constructors can be very useful for setting initial values for certain member variables. A default constructor does not have any parameter, but if you need, a constructor can have parameters. This helps you to assign initial value to an object at the time of its creation.  

* Destructors

A **destructor** is a special member function of a class that is executed whenever an object of it's class goes out of scope or whenever the delete expression is applied to a pointer to the object of that class. A destructor will have exact same name as the class prefixed with a tilde (~) and it can neither return a value nor can it take any parameters. Destructor can be very useful for releasing resources before coming out of the program like closing files, releasing memories etc.  

27.	**How can you encapsulate dynamic memory allocation in an object?**

As we know that Constructor is a member function of a class which is called whenever a new object is created of that class. It is used to initialize that object. Destructor is also a class member function which is called whenever the object goes out of scope.  
Destructor is used to release the memory assigned to the object. It is called in these conditions.  
* When a local object goes out of scope
* For a global object, operator is applied to a pointer to the object of the class
We again use pointers while dynamically allocating memory to objects. Let's see an example of array of objects.

```cpp
#include <iostream>

using namespace std;

class A
{
	 public:
       	A() { 
    	  cout << "Constructor" << endl; 
      	}
       	~A() { 
    	   cout << "Destructor" << endl; 
        }
};

int main()
{
	A* a = new A[4];
	delete [] a; // Delete array
	return 0;
}
```

28.	**What is operator overloading, why and how is it used?**

You can redefine or overload the function of most built-in operators in C++. These operators can be overloaded globally or on a class-by-class basis. Overloaded operators are implemented as functions and can be member functions or global functions.  
An overloaded operator is called an operator function. You declare an operator function with the keyword operator preceding the operator. Overloaded operators are distinct from overloaded functions, but like overloaded functions, they are distinguished by the number and types of operands used with the operator.   
```cpp
#include <iostream>

class HAHA {
private:
	int num;

public:
	HAHA() {
		num = -1;
	}

	void operator ++() {
		num = num + 10;
	}

	void display() {
		std::cout << num << std::endl;
	}

};

int main() {
	HAHA test;
	++test;
	test.display(); // 9
}
```

29.	**What is class inheritance, what is advantages does it have?**

The capability of a class to derive properties and characteristics from another class is called **Inheritance**. Inheritance is one of the most important feature of Object Oriented Programming.  
**Sub Class**: The class that inherits properties from another class is called Sub class or Derived Class.  
**Super Class**:The class whose properties are inherited by sub class is called Base Class or Super class.  


30.	**How to class access keywords relate to inheritance?**

* Public mode

If we derive a sub class from a public base class. Then the public member of the base class will become public in the derived class and protected members of the base class will become protected in derived class. Private members of the base class will never get inherited in sub class.  
* Protected mode 

If we derive a sub class from a Protected base class. Then both public member and protected members of the base class will become protected in derived class. Private members of the base class will never get inherited in sub class.  
* Private mode

If we derive a sub class from a Private base class. Then both public member and protected members of the base class will become Private in derived class. Private members of the base class will never get inherited in sub class.  

||Derived class|Derived class|Derived class|
|--|--|--|--|
|Base class|public mode|private mode|protected mode|
|private|Not inherited|Not inherited|Not inherited|
|protected|protected|private|protected|
|public|public|private|protected|

31.	**What are virtual functions in classes?**

A virtual function is a member function that you expect to be redefined in derived classes. When you refer to a derived class object using a pointer or a reference to the base class, you can call a virtual function for that object and execute the derived class's version of the function.  
Virtual functions ensure that the correct function is called for an object, regardless of the expression used to make the function call.

```cpp
#include <iostream>
using namespace std;

class Polygon {
  protected:
    int width, height;
  public:
    void set_values (int a, int b)
      { width=a; height=b; }
    virtual int area ()
      { return 0; }
};

class Rectangle: public Polygon {
  public:
    int area ()
      { return width * height; }
};

class Triangle: public Polygon {
  public:
    int area ()
      { return (width * height / 2); }
};

int main () {
  Rectangle rect;
  Triangle trgl;
  Polygon poly;
  Polygon * ppoly1 = &rect;
  Polygon * ppoly2 = &trgl;
  Polygon * ppoly3 = &poly;
  ppoly1->set_values (4,5);
  ppoly2->set_values (4,5);
  ppoly3->set_values (4,5);
  cout << ppoly1->area() << '\n'; // 20
  cout << ppoly2->area() << '\n'; // 10
  cout << ppoly3->area() << '\n'; // 0
  return 0;
}
```

32.	**What are STL containers? What are the advantages of using containers?**

* Sequence Containers
    * [array](http://www.cplusplus.com/reference/array/array/) Array class
    * [vector](http://www.cplusplus.com/reference/vector/vector/) Vector
    * [deque](http://www.cplusplus.com/reference/deque/deque/) Double ended queue
    * [list](http://www.cplusplus.com/reference/list/list/) List
    * [forward_list](http://www.cplusplus.com/reference/forward_list/forward_list/) Forward list

* Associative Containers
    * [set](http://www.cplusplus.com/reference/set/set/) Set
    * [map](http://www.cplusplus.com/reference/map/map/) Map
    * [unordered_set](http://www.cplusplus.com/reference/unordered_set/unordered_set/) Unordered Set
    * [unordered_map](http://www.cplusplus.com/reference/unordered_map/unordered_map/) Unordered Map

* Container Adaptors
    * [stack](http://www.cplusplus.com/reference/stack/stack/) LIFO stack
    * [queue](http://www.cplusplus.com/reference/queue/queue/) FIFO queue
    * [priority_queue](http://www.cplusplus.com/reference/queue/priority_queue/) Priority queue

33.	**What are STL Iterators? How are they used?**

An iterator is any object that, pointing to some element in a range of elements (such as an array or a container), has the ability to iterate through the elements of that range using a set of operators (with at least the increment (++) and dereference (\*) operators).  
The most obvious form of iterator is a pointer: A pointer can point to elements in an array, and can iterate through them using the increment operator (++). But other kinds of iterators are possible. For example, each container type (such as a list) has a specific iterator type designed to iterate through its elements.  
Iterators are classified into five categories depending on the functionality they implement. [Reference](http://www.cplusplus.com/reference/iterator/)  
* Output
* Input 
* Forward
* Bidirectional
* Random Access

34.	**What are Smart pointers? How do they differ from ‘raw’ pointers?**

In modern C++ programming, the Standard Library includes smart pointers, which are used to help ensure that programs are free of memory and resource leaks and are exception-safe.  
Smart pointers are defined in the std namespace in the <memory> header file. They are crucial to the RAII or Resource Acquisition Is Initialialization programming idiom. The main goal of this idiom is to ensure that resource acquisition occurs at the same time that the object is initialized, so that all resources for the object are created and made ready in one line of code. In practical terms, the main principle of RAII is to give ownership of any heap-allocated resource—for example, dynamically-allocated memory or system object handles—to a stack-allocated object whose destructor contains the code to delete or free the resource and also any associated cleanup code.  
In most cases, when you initialize a raw pointer or resource handle to point to an actual resource, pass the pointer to a smart pointer immediately. In modern C++, raw pointers are only used in small code blocks of limited scope, loops, or helper functions where performance is critical and there is no chance of confusion about ownership.  

```cpp
void UseRawPointer()
{
    // Using a raw pointer -- not recommended.
    Song* pSong = new Song(L"Nothing on You", L"Bruno Mars"); 

    // Use pSong...

    // Don't forget to delete!
    delete pSong;   
}

void UseSmartPointer()
{
    // Declare a smart pointer on stack and pass it the raw pointer.
    unique_ptr<Song> song2(new Song(L"Nothing on You", L"Bruno Mars"));

    // Use song2...
    wstring s = song2->duration_;
    //...

} // song2 is deleted automatically here.
```

35.	**What is the difference between an unique pointer and a shared pointer?**

Both of these classes are smart pointers, which means that they automatically (in most cases) will deallocate the object that they point at when that object can no longer be referenced. The difference between the two is how many different pointers of each type can refer to a resource.  
When using ```unique_ptr```, there can be at most one ```unique_ptr``` pointing at any one resource. When that ```unique_ptr``` is destroyed, the resource is automatically reclaimed. Because there can only be one ```unique_ptr``` to any resource, any attempt to make a copy of a ```unique_ptr``` will cause a compile-time error.  
[Reference](https://mbevin.wordpress.com/2012/11/18/smart-pointers/)

36.	**What is the difference between the ‘size’ and ‘capacity’ of a vector?**

**Size** is not allowed to differ between multiple compilers. The size of a vector is the number of elements that it contains, which is directly controlled by how many elements you put into the vector.  
**Capacity** is the amount of space that the vector is currently using. Under the hood, a vector just uses an array. The capacity of the vector is the size of that array. This is always equal to or larger than the size. The difference between them is the number of elements that you can add to the vector before the array under the hood needs to be reallocated.  
You should almost never care about the capacity. It exists to let people with very specific performance and memory constraints do exactly what they want.

37.	**What does the reserve method do in a vector?  When is it advantageous to use it?**
```cpp
void reserve( size_type new_cap );
```
Increase the capacity of the vector to a value that's greater or equal to ```new_cap```. If ```new_cap``` is greater than the current ```capacity()```, new storage is allocated, otherwise the method does nothing.  
If ```new_cap``` is greater than ```capacity()```, all iterators, including the past-the-end iterator, and all references to the elements are invalidated. Otherwise, no iterators or references are invalidated.
```cpp
// vector::reserve
#include <iostream>
#include <vector>

int main () {
  std::vector<int>::size_type sz;

  std::vector<int> foo;
  sz = foo.capacity();
  std::cout << "making foo grow:\n";
  for (int i=0; i<100; ++i) {
    foo.push_back(i);
    if (sz!=foo.capacity()) {
      sz = foo.capacity();
      std::cout << "capacity changed: " << sz << '\n';
    }
  }

  std::vector<int> bar;
  sz = bar.capacity();
  bar.reserve(100);   // this is the only difference with foo above
  std::cout << "making bar grow:\n";
  for (int i=0; i<100; ++i) {
    bar.push_back(i);
    if (sz!=bar.capacity()) {
      sz = bar.capacity();
      std::cout << "capacity changed: " << sz << '\n';
    }
  }
  return 0;
}
// making foo grow:
// capacity changed: 1
// capacity changed: 2
// capacity changed: 4
// capacity changed: 8
// capacity changed: 16
// capacity changed: 32
// capacity changed: 64
// capacity changed: 128
// making bar grow:
// capacity changed: 100
```

38.	**What are containers?**

A container is a holder object that stores a collection of other objects (its elements). They are implemented as class templates, which allows a great flexibility in the types supported as elements.  
The container manages the storage space for its elements and provides member functions to access them, either directly or through iterators (reference objects with similar properties to pointers).  
[Reference](http://www.cplusplus.com/reference/stl/)

39.	**What are the differences between sequence containers and associative containers?**

A **sequence** container is ordered. Each item has a unique index from 0-N where N is the number of elements. Example: std::vector.  
An **associative** container has no inherent order. It represents a mapping from a key to a value. That is, instead of having an index, each item is retrieved using its key. Example: std::map.

40.	**What are the main features of (and differences) of vector, deque and list containers.**

Use [deque](http://www.cplusplus.com/reference/deque/deque/) if you need efficient insertion/removal at the beginning and end of the sequence and random access; use [list](http://www.cplusplus.com/reference/list/list/) if you need efficient insertion anywhere, at the sacrifice of random access. Iterators and references to [list](http://www.cplusplus.com/reference/list/list/) elements are very stable under almost any mutation of the container, while [deque](http://www.cplusplus.com/reference/deque/deque/) has very peculiar iterator and reference invalidation rules (so check them out carefully).  
Also, [list](http://www.cplusplus.com/reference/list/list/) is a node-based container, while a [deque](http://www.cplusplus.com/reference/deque/deque/) uses chunks of contiguous memory, so memory locality may have performance effects that cannot be captured by asymptotic complexity estimates.  
[deque](http://www.cplusplus.com/reference/deque/deque/) can serve as a replacement for [vector](http://www.cplusplus.com/reference/vector/vector/) almost everywhere and should probably have been considered the "default" container in C++ (on account of its more flexible memory requirements); the only reason to prefer [vector](http://www.cplusplus.com/reference/vector/vector/) is when you must have a guaranteed contiguous memory layout of your sequence.

41.	**What does double linking in a list mean?**

A doubly-linked list is a linked data structure that consists of a set of sequentially linked records called nodes. Each node contains two fields, called links, that are references to the previous and to the next node in the sequence of nodes.  
```cpp
struct node {
	int data;
	node *prev;
	node *next;
};
```

42.	**What are map objects?**

Maps are associative containers that store elements formed by a combination of a ```key value``` and a ```mapped value```, following a specific order.  
In a ```map```, the ```key value```s are generally used to sort and uniquely identify the elements, while the mapped values store the content associated to this ```key```. The types of key and mapped value may differ, and are grouped together in member type ```value_type```, which is a pair type combining both:
```cpp
typedef pair<const Key, T> value_type;
```
Internally, the elements in a ```map``` are always sorted by its ```key``` following a specific ```strict weak ordering``` criterion indicated by its internal comparison object (of type ```Compare```).  
map containers are generally slower than unordered_map containers to access individual elements by their ```key```, but they allow the direct iteration on subsets based on their order.  
The mapped values in a map can be accessed directly by their corresponding key using the ```bracket operator``` ((operator[]).  
Maps are typically implemented as ```binary search``` trees.

43.	**What are iterators and how are they used?**

The concept of an iterator is fundamental to understanding the C++ Standard Template Library (STL) because iterators provide a means for accessing data stored in container classes such a vector, map, list, etc.  
You can think of an iterator as pointing to an item that is part of a larger container of items. For instance, all containers support a function called begin, which will return an iterator pointing to the beginning of the container (the first element) and function, end, that returns an iterator corresponding to having reached the end of the container. In fact, you can access the element by "dereferencing" the iterator with a \*, just as you would dereference a pointer. 

44.	**Using the ```std::multiplies<>()``` functor and the ```std::transform<>()```  algorithm multiply the element 0 to 20 of ```numbersA``` with element 10 to 30 of ```numbersB``` and save the result on element 0:20 of ```numbersC```.**
```cpp
#include <iostream>
#include <vector>
#include <iterator>
#include <algorithm>

using namespace std;

void display(vector<int> vec) {
	cout << endl;
	for (auto v : vec) {
		cout << v << "\t";
	}
	cout << endl;
}

vector<int> init(int n) {
	vector<int> result;
	for (int i = 0; i < 100; i++) {
		result.push_back(i+n);
	}
	return result;
}


int main() {

	vector<int> numbersA = init(1);
	vector<int> numbersB = init(1);
	vector<int> numbersC(100);

	/*template <class InputIterator, class OutputIterator, class binary>
	OutputIterator transform(InputIterator begin1,
		InputIterator end1, InputIterator begin2,
		OutputIterator result, binary function f);*/

	transform(numbersA.begin(), numbersA.begin()+20,
		numbersB.begin()+9, numbersC.begin(),
		multiplies<int>());

	display(numbersA);
	display(numbersB);
	display(numbersC);

	system("pause");
	return 0;

}
```
![image](https://github.com/ZihengZZH/Assignment/blob/master/RevisionCpp/44.PNG)



