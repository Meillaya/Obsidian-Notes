COMPSCI 3MI3 Fall, 2022\
By: Nathan Agbomedarho\
Student ID: 400081762\
Date: November 18th 2022\

### Question 1

The symbol c is bound statically, references and declarations execute during compilation. Symbols: ".()+;" in java are static bound. Java operators also execute during runtime. They can be statically or dynamically bound for the symbols "x()" & "y()". Depending on the program configuration, the way in which the symbols operate may occur early or late during runtime.

### Question 2
**Point 1:** 

def2: a b c\
def1: e f\

**Point 2:**

def3: b c d\
def2: a\
def1: e f\

**Point 3:** 

def5: a c\
def4: d e\
def3: b\
def1: f\

**Point 4:** 

def4: c d e\
def3: b\
def2: a\
def1: f\

**Point 5:** 

def3: b c d\
def2: a\
def1: e f\

**Point 6:** 

def2: a b c\
def1: e f\

### Question 3


(a)
Fun3: d,e,f\
Fun2: a,b,c\

(b): 
Main: f\
Fun1: d,e\
Fun2: a,b,c\

(c):
Fun2: a,c\
Fun1: b\
Fun3: d,e,f\

(d): 
Main: f\
Fun2: a,b,c\

(e):
Fun2: a,b,c\
Fun3: d,e,f\

(f):
Fun3: d,e,f\
Fun2: A,b,c\

### Question 4

**Script 1:**

``` bash
#!/bin/bash
X="hello"
echo $X
```

**Script 2:**

```bash
#!/bin/bash
X="world"
echo $X
sh ./script1
echo $X
```

When script 1 is called it echoes the value of x, which is "hello". Script 2 echoes the values of x, which is "world", then it calls script 1 which echoes "hello" and then it echoes the value "world" again.

**Scoping of bash script variables:**
To access a variable, we use the $ symbol as a reference. In relation to the scopes of variables, we have local and global variables. Local variables can only be accessed within a particular part of the code, in which they are declared; which is to say a variable declared in a bash script can't be accessed outside of the script. Conversely,  global variables can be referenced and accessed outside of scripts and also within.

In this case the variables are local to the script and can't be accessed outside of it.

### Question 5

Pointers refer to a specific address in memory. They can perform arithmetic operations, references however cannot. Accessing memory with pointer arithmetic is fundamentally unsafe, to prevent this Java does not allow pointer arithmetic. In java we cannot manipulate pointers, they exist as a tool to facilitate references. References are objects/values in memory and they are declared with an explicit type. Arithmetic operations can't be performed on variables referenced, as the variables itself refers to a different variable, and arithmetic on an address returns an address.

Java references function as memory addresses, the language restricts the functions they can perform; you can't perform arithmetic operations on them, due to their immutable nature. Arithmetic on objects has unknown effects. Objects in java are simply references that are passed, they aren't passed to methods or returned. Java essentially restricts pointer arithmetic on reference, as such enabling pointers in Java would reduce the safety and integrity of the language, and needlessly make it more complex.

### Question 6

Python does not provide left/right versions of its comparison operators. It decides which function to call first. The subclass's implementation of comparison is respected first during comparison.

### Question 7
