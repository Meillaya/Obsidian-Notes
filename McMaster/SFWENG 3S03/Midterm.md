# Question 1

(a)

Three functional tests for this program are as follows:

**Test 1:**

Check for valid user input. This test will verify that the user inputs calculate the correct amount for the car insurance payment according to the formula used to calculate the customer's car insurance payments. The test will fail if the program fails to compile or returns a null/empty value or returns an incorrect car insurance payment value.

Example pseudocode:

```python
def carInsurance()

age, yDriving, claimAmts = 0
postalCode = ''
payment = 0

try:
//formula to calculate insurance


except Exception:
	print("Incorrect value or null return val. Check input")
	sys.exit(1)

return 0
```

**Test 2:**

Check for invalid input. This test will verify that the program can correctly handle negative inputs or invalid input types. The expected output in such cases will be an error message or thrown exception.

Example pseudocode:

```python
def carInsurance()

age = -100
yDriving = five
claimAmts = -1
postalCode = 239548
payment = 0

try:
//formula to calculate insurance


except Exception:
	print("Invalid input values.")
	sys.exit(1)

return 0
```

**Test 3:**

Check for edge cases. This test will check for some common test cases in such calculations, such as input values that are correct but don't result in a correct car insurance payment. For example: 

- Age: 21
- Postal Code: 290 234
- Years of driving: 3
- Number of claims in the last 3 years: 0

This input values are valid, but the software test might not catch such an exception, which is why it's important to test for such edge cases.

(b)

Three boundary value tests for this software are as follows:

1. Test for a minimum and maximum age, this test will verify that input age values fall within a certain range and the program handles the calculation correctly within these bounds.
2. Test for 

# Question 2

