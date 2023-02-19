## Question 1

Probability of getting a connection = $1/25$

Probability of not getting a connection = $24/25$

Required Probability:

$$

\begin{equation}
\left( \frac{24}{25} \right)^{7}= 0.75
\end{equation}
$$


## Question 2
The Shannon Capacity Formula establishes the relationship between data rate, noise and error rate.

According to Shannon Capacity Formula

Max channel Capacity is

$C=B·log_2 (1+SNR)$ in bps (bits per second)

where Signal-to-Noise ratio (SNR or S/N) is expressed in decibels •

$\text{SNR}_{dB} = 10 log_{10}$ (Signal power/Noise power) •

B is the bandwidth in Hertz

Here $\text{SNR}_{dB}$=15 db

15 =$10log_{10}$(SNR)

1.5=$log_{10}$(SNR)

Therefore, SNR=101.5

**SNR =31.6**

Bandwidth B=10Mhz-4Mhz

**B =6Mhz=6*106Hz**

Maximum Bit Rate,C is given by Shannon Capacity Formula
$$
\begin{equation}

C = B*log_{2}(1+SNR)

= (6*106)*log_{2}(1+31.6)

= (6*106)*log_{2}(32.6)

= (6*106)*5.027

=30.162*106
\end{equation}

$$


**C = 30Mbps**

## Question 3
In a block of bits with 5 rows and 6 columns including horizontal and vertical parity bits, the total number of bits is 5 * 6 + 2 * 6 + 2 * 5 = 40. If exactly 4 bits are inverted due to transmission errors, the probability that the error will go undetected depends on the specific location of the inverted bits. If the inverted bits are located in a way that they do not affect the horizontal or vertical parity, then the error will go undetected. To estimate the probability, we can calculate the number of combinations of 4 bits that do not affect the parity and divide that by the total number of combinations of 4 bits.

For example, consider the case where the 4 inverted bits are located in 4 different rows. In this case, the horizontal parity will still be correct. If we choose the 4 bits randomly, the number of combinations is C(5,4) = 5, and the probability of error detection is 1 - 5/C(40,4) = 1 - 5/91390. This is an upper bound on the probability of error detection, since the 4 inverted bits could be located in less than 4 different rows.

A more accurate estimate can be obtained by considering all possible combinations of 4 bits and checking if they affect the parity. However, this is a complex calculation and the exact answer depends on the specific design of the block of bits.

In general, the probability of error detection is close to 1, and the probability of error going undetected is close to 0. The closest answer to the probability of the error going undetected is 0.05.

Since there are horizontal and vertical parity bits in this block of bits, it is possible to detect errors by checking if the parity bits are correct. If exactly 4 bits are inverted, there are 2 possibilities: either all 4 bits are in the same row, or all 4 bits are in the same column. In either case, the error can be detected by the corresponding parity bit.

To calculate the probability of failure to detect the error, we need to consider the possibility that the 4 bits are inverted in a way that neither the horizontal nor the vertical parity bits can detect the error. This would happen if 2 bits are inverted in the same row and 2 bits are inverted in the same column, but not in the same row and column.

The number of ways to choose 2 bits from a row is C(6, 2) = 15, and the number of ways to choose 2 bits from a column is C(5, 2) = 10. The total number of ways to choose 4 bits is C(30, 4) = 3003. So the probability of failure to detect the error is:

(15 * 10)/3003 = 0.05

So the probability of failure to detect the error is 0.05, or 5%.
## Question 4
CRC (Cyclic Redundancy Check) is a technique for error detection that involves dividing the data bit sequence by a predetermined polynomial (generator polynomial) and using the remainder as the checksum. In this case, the 11-bit message is "10111010100" and the generator polynomial is x^4 + x^3 + 1.

To perform the division, the message is padded with zeros to the left to make it the same length as the generator polynomial. In this case, the 11-bit message is padded with 4 zeros to become "000010111010100".

Next, the division is performed bit by bit starting from the leftmost bit. In each step, if the leftmost bit is 1, the divisor (generator polynomial) is XORed with the current dividend (padded message). If the leftmost bit is 0, the divisor is simply shifted to the right by one bit. This process is repeated until the dividend is less than the divisor. The final remainder is the checksum, which is appended to the original message to form the complete code transmitted by the sender.

The division process is shown below:
```lua
   000010111010100
 / x^4 + x^3 + 1
   ----------------
   000010111010100
   000010111010100
 - 000001110000000
   ----------------
     000100110100
   000100110100
   000100110100
 - 0000011100000
   ----------------
       1101100
     1101100
     1101100
   - 0000111
   ----------------
        00100

The final remainder is "00100", which is the 4-bit checksum. To obtain the complete code transmitted by the sender, the checksum is appended to the original message:

10111010100 + 00100 = 101110101001001

So the code transmitted by the sender is "101110101001001".

```

## Question 5
Hamming code is a error detection and correction technique in which extra bits (parity bits) are added to the data to be transmitted to ensure that errors can be detected and corrected. In this case, the data byte to be transmitted is "10011010".

To construct the Hamming code, the data byte is first separated into groups of bits and parity bits are added to the positions that correspond to powers of 2 (e.g. 1, 2, 4, 8, etc.). The parity bits are calculated such that the number of 1's in each group, including the parity bit, is always odd.

Here's the process to generate the Hamming code for the data byte "10011010":
```vb
Step 1: Assign parity bits to positions
1   2   3   4   5   6   7   8
P   D   D   P   D   D   D   D

Step 2: Calculate parity bits
1: 10011010 => 1 (odd number of 1's, so no change)
2: 01001101 => 0 (even number of 1's, so invert the bit)
4: 00100110 => 1 (odd number of 1's, so no change)
8: 10000110 => 0 (even number of 1's, so invert the bit)

Step 3: Combine parity and data bits
P   D   D   P   D   D   D   D
0   1   0   0   1   1   0   1   0

The resulting code is "011100101010".

So the Hamming code to be transmitted is "011100101010".

```

## Question 6
The reason is that the Hamming code is designed to detect and correct one-bit errors. In this case, since exactly one bit has been flipped during transmission, the parity check performed by the receiver will fail for exactly one code.

By examining the parity bits of each code, it is easy to see that the code 0 1 0 1 0 1 1 0 0 0 1 1 has even parity, which means that the number of 1's in each group, including the parity bit, is even. This means that the code has passed the parity check and is most likely correct.

The other codes have an odd number of 1's in some of the groups, which means that the parity check has failed for those codes and they are most likely incorrect.