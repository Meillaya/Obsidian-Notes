
# Q1

a)

Here's a pseudo-Java implementation of the `bonusCheck` method that takes in the number of bonus points and a boolean flag indicating whether the customer is a Gold customer or not, and returns one of the three possible outputs - `FULLPRICE`, `DISCOUNT` or `ERROR`:

```java
public String bonusCheck(int bonusPoints, boolean isGoldCustomer) {
    if (bonusPoints < 0) {
        return "ERROR";
    } else if (isGoldCustomer && bonusPoints >= 100) {
        return "DISCOUNT";
    } else if (!isGoldCustomer && bonusPoints >= 150) {
        return "DISCOUNT";
    } else {
        return "FULLPRICE";
    }
}

```

The method first checks if the bonus points are negative, in which case it returns an `ERROR` output. Otherwise, it checks if the customer is a Gold customer and if they have more than or equal to 100 bonus points, in which case it returns a `DISCOUNT` output. If the customer is not a Gold customer but has more than or equal to 150 bonus points, it also returns a `DISCOUNT` output. If neither of these conditions are met, it returns a `FULLPRICE` output.

b)

Equivalence partitioning is a black-box testing technique that involves dividing the input domain into a set of equivalence classes or partitions such that the program's behavior is expected to be the same for all values in each partition. Here are the input and output partitions for the `bonusCheck` program:

Input Partitions:

1.  Invalid Bonus Points (less than 0)
2.  Valid Bonus Points (0 or greater)
3.  Gold Customer
4.  Non-Gold Customer

Output Partitions:

1.  Error (for invalid bonus points input)
2.  Full Price (for valid bonus points input where customer does not qualify for a discount)
3.  Discount (for valid bonus points input where customer qualifies for a discount)

Note that each input partition is a binary partition, i.e., there are only two possible values for each input, whereas the output partitions are ternary partitions, i.e., there are three possible values for the output.

Using these partitions, we can design test cases that cover all the possible combinations of input and output partitions to test the `bonusCheck` program thoroughly.

c)

Here is a set of test cases that covers all the input and output partitions for the `bonusCheck` program:

Test Cases:

1.  Invalid Bonus Points, Gold Customer: -100, true --> Error
2.  Invalid Bonus Points, Non-Gold Customer: -50, false --> Error
3.  Valid Bonus Points, Gold Customer, No Discount: 50, true --> Full Price
4.  Valid Bonus Points, Gold Customer, Discount: 150, true --> Discount
5.  Valid Bonus Points, Gold Customer, Discount: 200, true --> Discount
6.  Valid Bonus Points, Non-Gold Customer, No Discount: 50, false --> Full Price
7.  Valid Bonus Points, Non-Gold Customer, No Discount: 100, false --> Full Price
8.  Valid Bonus Points, Non-Gold Customer, Discount: 200, false --> Discount

These test cases cover all the possible combinations of input and output partitions. Test cases 1 and 2 cover the invalid bonus points input partition. Test cases 3 and 6 cover the valid bonus points and non-gold customer input partitions with the full price output partition. Test cases 4, 5, and 8 cover the valid bonus points and gold customer input partition with the discount output partition. Test case 7 covers the valid bonus points and non-gold customer input partition with the discount output partition.

d)

The test cases identified above are sufficient and adequate because they cover all the possible combinations of input and output partitions for the `bonusCheck` program. Each test case tests a different partition combination, ensuring that all possible scenarios are covered.

A good set of test cases for equivalence partition testing should cover all the input and output partitions for the program under test. Each partition should be tested with at least one input value to ensure that all scenarios are covered. The test cases should be designed such that they are representative of real-world scenarios and edge cases that the program is likely to encounter. The test cases should be easy to understand, execute and maintain. Finally, the test cases should be independent of each other to ensure that a failure in one test case does not impact the results of other test cases. The test cases identified above meet all these criteria, making them a good set of test cases for equivalence partition testing.

e)

Equivalence partition testing is a black-box testing technique that involves dividing the input domain into a set of equivalence classes or partitions such that the program's behavior is expected to be the same for all values in each partition. Here are some strengths and weaknesses of partition testing:

Strengths:

1.  Partition testing is a simple and systematic way of testing a large input space.
2.  It is an effective way of reducing the number of test cases needed to test a program.
3.  It helps identify the most important inputs and outputs for a program.
4.  It is a good way of identifying defects and bugs in the program logic and design.
5.  It is an efficient way of increasing the overall quality of the program and reducing the cost of testing.

Weaknesses:

1.  It may not be possible to define partitions that cover all possible input values.
2.  There may be multiple valid partitions for the same input domain, which can lead to ambiguity and confusion.
3.  Partition testing may not be effective for identifying certain types of errors, such as timing and performance issues.
4.  Partition testing may not be effective for identifying defects related to interactions between different inputs and outputs.
5.  Partition testing relies on the quality of the partition definition, which can be difficult and time-consuming to create, especially for complex programs.

In summary, partition testing is a useful and effective testing technique that has its strengths and weaknesses. It is a good way of testing a large input space in a systematic manner and identifying defects and bugs in the program logic and design. However, it may not be effective for identifying certain types of errors and may require careful definition and selection of partitions to be effective.

# Q2

a)

Boundary value testing is a type of black-box testing that involves testing the program using input values that are at the boundaries of the input domain. Here are the boundary values needed to test the `bonusCheck` program:

Input boundaries:

1.  The minimum number of bonus points: 1
2.  The maximum number of bonus points for non-Gold customers to receive a discount: 149
3.  The minimum number of bonus points for Gold customers to receive a discount: 101
4.  The maximum number of bonus points for any customer: positive infinity

Output boundaries:

1.  When the number of bonus points is 1, the output should always be "FULLPRICE".
2.  When the number of bonus points is 149 for a non-Gold customer, the output should be "DISCOUNT".
3.  When the number of bonus points is 150 for a non-Gold customer, the output should be "FULLPRICE".
4.  When the number of bonus points is 101 for a Gold customer, the output should be "DISCOUNT".
5.  When the number of bonus points is 100 for a Gold customer, the output should be "FULLPRICE".

By testing the program with these boundary values, we can ensure that it behaves correctly at the edges of the input domain and produces the expected output.

b)



# Q3


```java
/**  
* Find index of pattern in subject string  
*  
* @param subject String to search  
* @param pattern String to find  
* @return index (zero-based) of first occurrence of pattern in subject; -1 if not  
found  
* @throws NullPointerException if subject or pattern is null  
*/  
public static int patternIndex (String subject, String pattern)  
{  
	final int NOTFOUND = -1;  
	int iSub = 0, rtnIndex = NOTFOUND;  
	boolean isPat = false;  
	int subjectLen = subject.length();  
	int patternLen = pattern.length();
	  
	while (isPat == false && iSub + patternLen - 1 < subjectLen)  
	{  
		if (subject.charAt(iSub) == pattern.charAt(0))  
		{  
			rtnIndex = iSub; // Starting at zero  
			isPat = true;  
			for (int iPat = 1; iPat < patternLen; iPat ++)  
			{  
				if (subject.charAt(iSub + iPat) != pattern.charAt(iPat))  
				{  
					rtnIndex = NOTFOUND;  
					isPat = false;
					/* MB: isPat = true; */  
					break; // out of for loop  
				}  
			}  
		}  
		iSub ++;  
	}  
	return (rtnIndex);  
}  
}
```
This is a Java method named `patternIndex` that takes two string parameters, `subject` and `pattern`, and returns an integer representing the index (zero-based) of the first occurrence of the `pattern` string in the `subject` string. If the `pattern` is not found, the method returns -1.

The method uses a while loop to iterate through the `subject` string and compare each character with the first character of the `pattern` string. If a match is found, a for loop is used to check if the remaining characters of the `pattern` string are found at consecutive positions in the `subject` string. If a complete match is found, the index of the first character of the `pattern` string is returned. If not, the iteration continues until the end of the `subject` string is reached.

The method also includes a constant named `NOTFOUND`, which is initialized to -1 and is used to indicate that the `pattern` was not found in the `subject` string.

Lastly, the method includes a check to make sure that both `subject` and `pattern` are not null, and if either of them is null, a `NullPointerException` is thrown.

a)

Here are the definitions and uses in the program:

Definitions:

-   `subject`: A string representing the subject string to search.
-   `pattern`: A string representing the pattern string to find.
-   `NOTFOUND`: A constant integer representing the value -1, which is used to indicate that the pattern was not found in the subject string.
-   `iSub`: An integer representing the index of the current character being checked in the subject string.
-   `rtnIndex`: An integer representing the index of the first character of the pattern string found in the subject string.
-   `isPat`: A boolean variable that is initially set to false and is used to indicate if a potential match for the pattern string has been found.
-   `subjectLen`: An integer representing the length of the subject string.
-   `patternLen`: An integer representing the length of the pattern string.

Uses:

-   `subject.length()`: Used to determine the length of the subject string.
-   `pattern.length()`: Used to determine the length of the pattern string.
-   `subject.charAt(iSub)`: Used to retrieve the character at the current index in the subject string.
-   `pattern.charAt(0)`: Used to retrieve the first character in the pattern string.
-   `subject.charAt(iSub + iPat)`: Used to retrieve the character at the current index in the subject string while checking for a complete match of the pattern string.
-   `pattern.charAt(iPat)`: Used to retrieve the character at the current index in the pattern string while checking for a complete match of the pattern string.
-   `rtnIndex = iSub`: Used to update the return index to the current index in the subject string if a potential match for the pattern string is found.
-   `isPat = true`: Used to indicate that a potential match for the pattern string has been found.
-   `rtnIndex = NOTFOUND`: Used to reset the return index if a complete match for the pattern string is not found.
-   `isPat = false`: Used to indicate that a complete match for the pattern string is not found.
-   `break`: Used to exit the for loop early if a complete match for the pattern string is not found.
-   `NullPointerException`: Used to indicate that either the subject or pattern string is null.

b)

```c
+----------------+
| Start of Method |
+--------+-------+
         |
         v
+--------+-------+
| Check for Null |
+--------+-------+
         |
         v
+--------+-------+
|   Initialize   |
| Variables and  |
|   Loop Check   |
+--------+-------+
         |
         v
+--------+-------+
|    Check for   |
|  Potential Match   |
+--------+-------+
         |
         v
+--------+-------+
|   Check for    |
| Complete Match |
+--------+-------+
         |
         v
+--------+-------+
| Return Index   |
+----------------+

```
Note that the graph includes five nodes, with the start of the method being the first node, and the return statement being the final node. The graph also includes decision nodes for checking for null, checking for potential match, and checking for a complete match, and a loop node for initializing variables and loop check.

c)

Here are the tables listing the defs and uses at each node and edge in the control flow graph of `patternIndex`:
| Node | Definitions                                                         | Uses                                                  |
| ---- | ------------------------------------------------------------------- | ----------------------------------------------------- |
| 1    | `subject`, `pattern`                                                | \-                                                    |
| 2    | \-                                                                  | `subject`, `pattern`                                  |
| 3    | `NOTFOUND`, `iSub`, `rtnIndex`, `isPat`, `subjectLen`, `patternLen` | `subject.length()`, `pattern.length()`                |
| 4    | \-                                                                  | `iSub`, `pattern.charAt(0)`                           |
| 5    | \-                                                                  | `rtnIndex`, `isPat`                                   |
| 6    | \-                                                                  | `subject.charAt(iSub + iPat)`, `pattern.charAt(iPat)` |
| 7    | \-                                                                  | `rtnIndex`, `isPat`                                   |

| Edge | Definitions                        | Uses                                                  |
| ---- | ---------------------------------- | ----------------------------------------------------- |
| 1-2  | \-                                 | `subject`, `pattern`                                  |
| 2-3  | \-                                 | `subject`, `pattern`                                  |
| 3-4  | `iSub`, `subjectLen`, `patternLen` | \-                                                    |
| 4-5  | `rtnIndex`, `isPat`                | `subject.charAt(iSub)`, `pattern.charAt(0)`           |
| 5-6  | \-                                 | `subject.charAt(iSub + iPat)`, `pattern.charAt(iPat)` |
| 6-5  | `rtnIndex`, `isPat`                | `subject.charAt(iSub + iPat)`, `pattern.charAt(iPat)` |
| 5-7  | `rtnIndex`, `isPat`                | \-                                                    |
| 7-6  | `rtnIndex`, `isPat`                | `iPat`, `patternLen`, `subjectLen`                    |
| 6-4  | \-                                 | `iPat`, `patternLen`                                  |
| 4-3  | `iSub`                             | `subjectLen`, `patternLen`                            |
| 3-5  | \-                                 | `isPat`, `iSub`, `patternLen`, `subjectLen`           |
| 5-1  | \-                                 | `rtnIndex`                                            |

d)

Here are all the unique du-paths in the program:

1.  `(3, subject.length())` - from node 3, define `subjectLen` and use it in edge 3-4.
2.  `(3, pattern.length())` - from node 3, define `patternLen` and use it in edge 3-4.
3.  `(4, iSub)` - from node 4, define `iSub` and use it in edge 4-5.
4.  `(4, pattern.charAt(0))` - from node 4, define `pattern.charAt(0)` and use it in edge 4-5.
5.  `(5, subject.charAt(iSub))` - from node 5, define `rtnIndex` and use it in edge 5-6.
6.  `(6, subject.charAt(iSub + iPat))` - from node 6, define `subject.charAt(iSub + iPat)` and use it in edge 6-6 or 6-7.
7.  `(6, pattern.charAt(iPat))` - from node 6, define `pattern.charAt(iPat)` and use it in edge 6-6 or 6-7.

e) 

To cover all du-paths in the program, we need to have at least one test case that exercises each path, i.e., each def-use pair. The total number of unique du-paths in the program is 7, as listed in the previous answer.

To cover all these paths, we need to design test cases that ensure each def node is executed at least once and that each use node is executed with the correct value from the corresponding def node. Therefore, we would need at least 7 test cases to cover all du-paths in this program.