### Question 1
Some arguments against using a single language for all programming domains are:  
Due to this, the language would become inevitably vast and complex.

This would result in expensive compilers and in turn their expensive maintenance.

The language will then probably not be well suited for any programming domain, either in terms of the efficiency of the compiler or of the code it generates.

More importantly, the language contains many unnecessary and confusing functions and constructs (those intended for other scopes) regardless of scope, making it difficult to use.

Different users will learn different subsets, making maintenance difficult.

### Question 2
It would dramatically cut the costs of programming training and compiler purchase and maintenance

it would simplify programmer recruiting and justify the development of numerous language dependent software development aids.

Single language makes learning easier for developers. This saves time in learning new languages, and developing products faster.

Since learning is easier, an average developer can do their task better, and doing work with more productivity will lead to more employee satisfaction in the company.

The ease of learning only a single language for employment will attract more students in software development.

Collaboration between developers becomes faster as points of discussion and basis of review is only a single language.

1.  A single language in all domains results in poor separation of concerns. Building complex systems is possible by abstractions and abstraction is built as a series of layers.
2.  It would result in increase of code re-usability.
3.  Language might be more complex to use it for all programming domains, because the usage for all the applications is not same, So it must include all the usages to make it robust.
4.  It would results in cut the costs of programming learning and maintenance of the compiler.
5.  It would simplify programmer recruiting and justify the development of numerous language dependent software development aids.

### Question 3
**1**. there is no special criteria in designing a efficient language and the problem is that they will confuse in between the efficient and safety.

**2**. every developer has to compromise on some criteria to design another criteria. mand developers and language designers trade safety for efficiency and there are soe designers who focussed on safety rather that efficiency one language among those is **PYTHON**.

3. generally python is not designed to be efficient and we all have to make a note of this.

**4**. Python is designed for the productivity and for extensibility through a necessarily ugly C FFI. and the tradeoff is very fundamental and also Python is slow forever

**5**.The bindings of Python are very bad forever.

**6**. Moreover python is designed for the security and safety purpose and that is the reason many top most companies use python language in developing their websites.

**7**. Python is strongly typed programming languageand it is most well written code in dynamic languages tends to follow a lot of the same conventions as strongly-typed code.

**8**. In Pyyhon you will never have to declare the type of your variables because they are statically computed during compilation and a Python Interpreter would compute them running the program.

**9**. so python is not efficient but it provides more safety for your applications.

### Question 4
The most common issue faced by the programmer is to deal with the problem of skipping the semi colon and then keep on searching in the complete code where it has been skipped. Though this has been resolved by many modern day IDEs but still this is a problem. As python doesnot involves any semi colon to written in at the end of the statement, hence it provides liberty to the programmers for skipping the semi colon at the end of the statement, as programmer don't have to worry about the syntactical errors to some extent.

The main strength behind the python programming language is it's indentation style. Though it is recommended to most of the programmer to add indentation to there codes but some of the programmers are lazy enough to skip this part. But with the python programming language this has been made compulsory for adding the proper indentation in the code. Python uses the line feed at the end of each statement to mark the end of the statement, instead of the traditional semi colon.
### Question 5
Python programs get structured with identation. Code blocks are defined by their indentation. All statements with same distance to the right belongs to the same block of code. If we need any further nested block, then it has to be indented further to the right. In python indentaion can be done using space/tab key(space prefereble to tab as tab is not of fixed length).

**Positives:** 1) With indentation, code becomes clear and can be easily understood.

2) Easy to indentify the start and close of the code block.

3) Increase in Code readability. And attractive look and feel.

4) Code becomes easy to maintain, modify and enhance with indentation.

**Negatives:** 1) Code doesn't lend itself to minimisation
### Question 6
So, to solve this problem, let understand how regular expressions (RE) works.

1.  unsigned integer with leading zeroes allowed, ie. 0, 0000, 1, 200, 0220 etc:
    -   so, let first break problem and write RE for given problem step by step
    -   first case should be number should be from 0 to 9 , so RE = [0-9]
    -   Now, atlease one number should be there, RE = [0-9]+
    -   so this RE make sure that atlease one digit will be there and it may start with any number.
    -   Now, we need to map this RE to Unix grep format only, i.e. grep “ [0-9]+”
2.  unsigned integer which not allow leading zeroes, ie. 0, 1, 200 etc:
    -   so, let first break problem and write RE for given problem step by step
    -   first case should be number should be either 0 or start with 1 to 9, RE= 0 | [1-9]
    -   Now, now let say, if number not start with 0 than it may contain other digit from 0 to 9, i.e. 0 | [1-9][0-9]*
    -   so this RE make sure that atlease one digit will be there and allow leading zeroes.
    -   Now, we need to map this RE to Unix grep format only, i.e. grep “0 | [1-9][0-9]*”
3.  similar to above example, we can write RE step by step:
    -   before "." and after "." RE will be same as previous one only. So we can write as follow: "0 | [1-9][0-9]* . [0-9]+"
4.  in this number can be 0 also so we shold allow empty string before and after "."
    -   so as per this problem, any part before and after can be black
    -   (0 | [1-9][0-9]*)? . [0-9]*
### Question 7-9
```Python

```