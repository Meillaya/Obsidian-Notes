### Question 1
Potential arguments against having a single language for all programming domains are:
- The language would inevitably become large and complex, resulting in expensive maintenance of compilers
- The language would not excel in any programming domain; it would neither be efficient in compile time nor code execution
- It would be difficult to use, regardless of application as a result of innumerable functions and constructs
- Maintenance would be difficult, as there will be far too many use-cases and edge-cases to account for, as well as the different needs of user

### Question 2

Potential arguments for having a single language for all programming domains are:
- It would simplify the process of hiring developers for certain tasks, as they wouldn't need to know the newest technology or framework to improve chances of employment
- Saves time for developers and makes learning easier, as they will only need to learn and master one language and its frameworks/libraries instead of mastering many
- Will reduce the cost of entry for new or potential software engineers as they will only need to learn one language for future employment
- Code re-usability would improve, as would ease of collaboration between developers, especially on large projects

### Question 3

Efficiency is the speed at which a particular language compiles and executes code, especially in relation to other languages and in large projects. Safety, on the other hand, describes how secure or reliable a programming language is at ensuring the safety of data processed during/after compilation and also during code execution.

Software development is quite flexible in what it allows engineers to achieve with languages; however, at every step a compromise needs to be made between efficiency and safety. Certain languages excel at the former while not so impressive with regard to the latter, while for other languages it's the reverse; while for other languages they strike a balance between the two.

Python is a language which is designed primarily for safety, not efficiency. It is designed to be very productive and extensible, with its wide array of libraries and frameworks. This is one of the many reasons why it is such popular language. However, the trade-off is that Python is not a fast language, as opposed to a newer language that focus on efficiency and safety like Rust or Golang. Python also doesn't allow you to have explicit control of memory or resource allocation, as the compiler automatically computes that during compilation. As a result of this, your code can run slower, because you don't fully control resource management.

### Question 4

A common problem in programming, is the issue of handling the semicolon, where a search continues in the code for where it has been skipped. Modern IDEs and compilers have solved this issue, however it's still an issue that needs to be attended to. Python doesn't make use of semicolons however, it makes use of indentation which makes it so that programmers will make fewer errors related to syntax. 

One of Python's main strength lies in its indentation style, and I believe this approach is more natural and less likely to result in syntax errors compared to the other approaches. The indentation approach makes Python code very readable and easy to debug. Python does use a symbol during interpretation to terminate a statement, it makes uses of the line feed to demarcate the end of statements, instead of semicolons.

### Question 5
Python code is structured with indentation, code blocks are defined by this indentation style.

Positives:
- Code is easy to read, clear, and easily understood
- Code blocks are easily identifiable, and code readability improves tremendously
- Code is easy to maintain, modify and improve
- The look and feel of the code is attractive
- Large amount of libraries and excellent frameworks
- Quick development in teams for projects
- Easy to learn

Negatives:
- Memory/resource allocation limitations
- It is not a fast language
- Is not suitable for memory intensive tasks
- Doesn't lend itself well to optimization

### Question 6

$1. \space[0 - 9]^{+}$ 

$2. \space 0|[1-9][0-9]^*$

$3. \space 0 \space \text{"."} \space [0-9]^+|[1-9][0-9]^{*} \space\text{"."} [0-9]^+$

$4. \space 0? \text{"."}  \space [0-9]^*|[1-9][0-9]^*\text{"."}[0-9]$


