COMPSCI 3MI3 Fall, 2022\
By: Nathan Agbomedarho\
Student ID: 400081762\
Date: November 18th 2022\

### Question 1
(a) Static Array :- A static array may be defined as the data structure with a fixed length. It is the most common form of array used. it is the type of array whose size cannot be altered. 
Example :- if you create an array of size 10 you cannot add the 11th element in static array because size of static array is fixed.

Advantages of static arrays :-

1) It has efficient execution time.
2) The lifetime of static allocation is the entire run time of program.

(b) Fixed stack-dynamic array :- Fixed stack-dynamic array is one in which the subscript ranges are dynamically bound and the storage allocation is dynamic during execution. Once bound they remain fixed during the lifetime of the variable.

Advantages of Fixed stack-dynamic array :-

1)Space efficiency Supports recursion.

(c) Stack-Dynamic:- Dynamic Stack is just like Dynamic Array, is a stack data structure whose the length or size increases or decreases in real time based on the operations like insertion or deletion performed on it. 

Advantages of static-dynamic :-

1) Flexibility :- size need not be known until the array is about to be used

(d) Fixed heap-dynamic array :- A fixed heap-dynamic array is one in which the subscript ranges are dynamically bound and the storage allocation is dynamic but they are both fixed after storage is allocated.

Advantages of Fixed heap-dynamic array :- 

1) Ultimate in flexibility.

(e) Heap-dynamic array :- A heap-dynamic array is one in which the subscript ranges are dynamically bound and the storage allocation is dynamic and can change any number of times during the array's lifetime.

Advantages of Heap-dynamic array :- 

1) Ultimate in flexibility.


### Question 2
Binary-coded decimal is a tool of writing numerals that assigns a 4-digit binary code to every digit 0 thru 9 in a decimal (base 10) quantity. definitely located, binary-coded decimal is a manner to transform decimal numbers into their binary equivalents.

in the BCD numbering device, a decimal range is separated into 4 bits for each decimal digit inside the quantity. every decimal digit is represented with the aid of its weighted binary value acting a direct translation of the quantity.

Binary Coded Decimal (BCD) code BCD is a way to specific every of the decimal digits with a binary code. inside the BCD, with 4 bits we're capable of constitute 16 numbers (0000 to 1111). however in BCD code handiest first ten of these are used (0000 to 1001). The very last six code combos i.e. 1010 to 1111 are invalid in BCD.

Binary Coded Decimal, or BCD, is some different system for changing decimal numbers into their binary equivalents. it's miles a form of binary encoding wherein every digit in a decimal variety is represented within the shape of bits. This encoding can be completed in each four-bit or eight-bit (commonly 4-bit is favored). Binary-coded decimal is a tool of writing numerals that assigns a four-digit binary code to every digit zero via 9 in a decimal (base 10) range. in fact located, binary-coded decimal is a way to transform decimal numbers into their binary equivalents. A binary code represents text, laptop processor instructions, or a few other information the use of a -image tool. the 2-picture machine used is frequently "0" and "1" from the binary amount device. The binary code assigns a sample of binary digits, furthermore called bits, to anybody, steering, and so forth.

### Question 3
Tombstones are a mechanism to detect dangling pointers that can appear in certain computer programming languages, e. g. C, C++ and assembly languages, and to act as a containment to their dangerous effects.  
A tombstone is a structure that acts as an intermediary between a pointer and the heap-dynamic data in memory. The pointer – sometimes called the handle – points only at tombstones and never to the memory that holds the actual value. When the data is deallocated, the tombstone is set to a null (or, more generally, to a value that is illegal for a pointer in the given runtime environment), indicating that the variable no longer exists. This prevents the use of invalid pointers, which would otherwise access the memory area that once belonged to the now deallocated variable, although it may already contain other data, in turn leading to corruption of in-memory data. Depending on the operating system, the CPU can automatically detect such an invalid access (e. g. for the null value: a null pointer dereference error). This supports in analyzing the actual reason, a programming error, in debugging, and it can also be used to abort the program in production use, to prevent it from continuing with invalid data structures.  
In more generalized terms, a tombstone can be understood as a marker for "this data is no longer here". For example in filesystems it may be efficient when deleting files to mark them as "dead" instead of immediately reclaiming all their data blocks.  
The downsides of using tombstones include a computational overhead and additional memory consumption: extra processing is necessary to follow the path from the pointer to data through the tombstone, and extra memory is necessary to retain tombstones for every pointer throughout the program. One other problem is that all the code – that needs to work with the pointers in question – needs to be implemented to use the tombstone mechanism.  
No popular programming language currently uses tombstones. However, built–in support by the programming language or the compiler is not necessary to use them.

![[McMaster/COMPSCI 3MI3/Assignments/q3.png]]



### Question 4
Numerous conceivable kind blunders can be clouded by essentially pressuring the sort of an operand from its erroneous sort given in the explanation to a proper kind as opposed to detailing it as a mistake in a language that requires many sort compulsions, debilitating the useful impact serious areas of strength for of makes it more hard for the developer to detect an error in factor composing.

For instance, consider the factors a = 10 and b= 20. At the point when we do a division c among an and b, for example, c= a/b, the compiler would quickly expect to be that an and b are whole numbers. The result would be a number that is assessed down, instead of a decimal number.

Pressure rules can cause issues where a sort can be switched over completely to one more sort some place in your code. This can make the code challenging to investigate if one don't watch out. It can likewise invalidate the point areas of strength for of which is intended to hold that back from occurring.

### Question 5
It is a special case of resource management, in which the limited resource being managed is memory. Benefits for the programmer is that **garbage collection** frees the programmer from manually dealing with memory allocation and deallocation. The bottom line is that **garbage collection** helps to prevent memory leaks.

Garbage collection is a form of automatic memory management. The garbage collector or collector attempts to reclaim garbage, or memory used by objects that will never be accessed or mutated again by the application.

Tracing garbage collectors require some implicit runtime overhead that may be beyond the control of the programmer, and can sometimes lead to performance problems. For example, commonly used Stop-The-World garbage collectors, which pause program execution at arbitrary times, may make garbage collecting languages inappropriate for some embedded systems, high-performance server software, and applications with real-time needs.

A more fundamental issue is that garbage collectors violate locality of reference, since they deliberately go out of their way to find bits of memory that haven't been accessed recently. The performance of modern computer architectures is increasingly tied to caching, which depends on the assumption of locality of reference for its effectiveness. Some garbage collection methods result in better locality of reference than others. Generational garbage collection is relatively cache-friendly, and copying collectors automatically defragment memory helping to keep related data together. Nonetheless, poorly timed garbage collection cycles could have a severe performance impact on some computations, and for this reason many runtime systems provide mechanisms that allow the program to temporarily suspend, delay or activate garbage collection cycles.

Despite these issues, for many practical purposes, allocation/deallocation-intensive algorithms implemented in modern garbage collected languages can actually be faster than their equivalents using explicit memory management (at least without heroic optimizations by an expert programmer). A major reason for this is that the garbage collector allows the runtime system to amortize allocation and deallocation operations in a potentially advantageous fashion. For example, consider the following program in C++:

``` C++
class A {
  int x;
public:
  A() { x = 0; ++x; }
};
 
int main() {
 for (int i = 0; i < 1000000000; ++i) {
   A *a = new A();
   delete a;
 }
 std::cout << "HELLO!" << std::endl;
}

```

One of more widely used libraries that provides this function is Hans Boehm's conservative GC. As we have seen earlier C++ also supports a powerful idiom called _RAII (resource acquisition is initialization)_ that can be used to safely and automatically manage resources including memory.


A fundamental issue with garbage collectors is that they violate locality of reference, as they find bits of memory that have not recently been accessed. Modern computer architecture relies heavily on caching, and locality of reference is imperative for its effectiveness. They are generally cache-friendly, however there can be severe performance impacts with certain computations upon compilation and during runtime. Garbage collectors allow the system to amortize allocation/deallocation operations which can be an advantage. Consider the following C++ program:\


Garbage collection is a method to free the programmer from worrying about basic memory management.

Thought this is the real need, so many drawbacks were left in dark for long years.

Because of so many bads, came to a conclusion that it is adding no value.

Problems:

- In cyclic loop dependencies, mostly it cannot make a right decision. It could possibly get it wrong.

- Computers however have all sorts of other places where pointers could be stored. They have shared memory, specialized vector processors, registers, graphics texture memory, in fact almost every chip in the system has some manner in which to store and retrieve data.

It’s simply not feasible, or even possible, for a garbage collector to properly scan all this memory(stored pointers)

- It holds on to resources too long. Because of this, late deallocation will happen.

- It doesn’t prevent memory leaks.

When the concept of cache comes in a program, objects will store in cache, till the program terminates. In this case, those unused free cache objects are technically in use. Garbage collector cannot do anything in this case.

- It is slow

- It pauses and interrupts


### Question 6
Operator Precedence is the priority for grouping different types of operators with their operands. It is a collection of rules that reflect conventions about which procedures to perform first in order to evaluate a given mathematical expression.

Operator Associativity is the left-to-right or right-to-left order for grouping operands to operators that have the same precedence. It is a property that determines how operators of the same precedence are grouped in the absence of parentheses.

**Operator precedence**:

The operator precedence is used to group the operands in a given expression for evaluation. The operator having higher precedence is evaluated first as compared to the lower precedence operator.

For example:

x = 1 - 4 * 3

In the above expression, the precedence of multiplication is higher than subtraction, so multiplication will be evaluated first and the subtraction will be performed and the result will be:

x = -11

**Operator associativity:**

The associativity is the property that determines how the operator of the same precedence is executed if the parentheses are missing in the expression.

The evaluation order of the expression is determined by precedence and associativity if the parentheses are missing in the expression.

The associativity can be:

1.  Left to right
2.  Right to left

The right-associative means the operators are grouped from the right.

For example:

The assignment operator '=' is right-associative in most of the programming languages.

a = b = c  
First, the value of c is assigned to b and then assign to variable a.

The operator '^' is right-associative.

x = 2^3^2

The above expression will be calculated as:

x = 2^(3^2)

x = 2^(9)

x = 512

### Question 7



### Question 8
**Question A :**

Here + operator will be evaluated first so value of x is 3 and then foo function will be evaluated which will update the value of x to 8 value returned by the function is 4.

So value of x after the assignment statement = 3 + 4 = 5.

  

**Question B :**

Here + operator will be evaluated first so foo function will be evaluated which will update the value of x to 8 value returned by the function is 4 and value of x is 8 and then

So value of x after the assignment statement = 8 + 4 = 12.

**Question C :**

Consider following example :

  

The GNU C compiler gcc works by translating the C code into assembly code and then assembling it into an executable file. The assembly code is then linked with the standard C library to create the final executable file.

To determine the precedence level of the function call in C, I modified the little program to include a print statement inside the main function. I then compiled and ran the program. The output showed that the print statement inside the main function was executed first, before the print statement inside the foo function. This indicates that the function call in C has the highest precedence level.

```C
#include <stdio.h>

int main()

{

int x=30;

printf("%d",printf("%d",printf("%d",x)));

return 0;

}
```

The output of the program is "3021".
This is because the function call to printf has the highest precedence level.


### Question 9
``` C
#include <iostream>

using namespace std;

int main()

{

int arr[2];

arr[0] = 1;

arr[1] = 4;

arr[3] = 7;

arr[4] = 8;

cout << arr[3] << endl;

cout << arr[4] << endl;

return 0;

}
```

As we know that the size of the array arr[2] is 3 and it's last index is 2 as defined above and index 3 and 4 are out of the array bound.

But when we store some value at some index out of the bound and print that index it still print the value stored in it even though it is out of bound.

And that is why we know that C/C++ does not check for array bound for static one dimensional array.

C/C++ does not do the array bound checking and it can store the data to any index memory of which comes under the stack area of the program. If it 

### Question 10

Let's first understand the concept of static and dynamic scoping.  
Static scoping- This is resolved at compile time, in this the variable referred is always the top level value, the value is independent of the run stack i.e it returns same value irrespective of the base call  

Dynamic scoping- Dynamic scoping on the other hand, refers to the most recent variable value and is decided at run time, the value returned is dependent on the run stack i.e the function calling it  
Lets look at a sample python Code-

x = 10  
def fun1():  
return x;

def fun2():  
x = 20;  
return fun1();  
  
print( fun2());  
Now, if it were using dynamic scoping, it should print 20 , but it prints 10, which means python uses static scoping

![[q10.png]]