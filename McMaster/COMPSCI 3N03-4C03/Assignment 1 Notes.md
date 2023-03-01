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

The maximum bit rate on a noisy channel can be calculated using the Shannon-Hartley theorem, which states that the maximum bit rate (in bits per second) of a channel is equal to the channel capacity, which is given by:

C = B * log2(1 + S/N)

where C is the channel capacity in bits per second, B is the bandwidth in hertz, S is the signal power, and N is the noise power.

To calculate the maximum bit rate on this channel, we need to know the bandwidth and the signal-to-noise ratio (SNR). The bandwidth is given as the difference between the upper and lower frequencies of the channel, which is 10 MHz - 4 MHz = 6 MHz.

The SNR is given in decibels (dB) as SNRdB = 15 dB. We can convert this to a ratio using the formula:

SNR = 10^(SNRdB/10)

which gives:

SNR = 10^(15/10) = 31.62

Now we can calculate the noise power as:

N = S/SNR

where S is the signal power. Since we don't know the signal power, we'll assume that it is equal to the noise power, so that the SNR is 1 (or 0 dB) and we can calculate the maximum bit rate for this worst-case scenario:

N = S/1 S = N

Plugging in the values we get:

N = S/SNR = N/31.62 N = S = (1/31.62)*10^(-3) watts

Finally, we can calculate the maximum bit rate as:

C = B * log2(1 + S/N) = 6 * log2(1 + 10^3/31.62) = 6 * log2(31.62 + 1) = 6 * log2(32.62) = 6 * 5 = 30 Mbps (approximately)

Therefore, the maximum bit rate on this channel is approximately 30 Mbps.

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

To determine whether each Hamming code is valid or not, we need to perform the following steps:

Step 1: Count the number of parity bits (p) in the Hamming code.
Step 2: Calculate the value of each parity bit using even parity (i.e., the parity bit is 0 if the number of 1s in the corresponding data bits is even, and 1 otherwise).
Step 3: Compare the calculated parity bits with the parity bits in the Hamming code. If they match, the Hamming code is valid; otherwise, it contains errors.

Let's apply these steps to the given Hamming codes:

Hamming code 1: 0 1 0 1 0 1 1 0 0 0 1 0
Step 1: There are 4 parity bits in this Hamming code.
Step 2:
Parity bit P1 = D3 ⊕ D5 ⊕ D7 ⊕ D9 ⊕ D11 = 0 ⊕ 0 ⊕ 1 ⊕ 0 ⊕ 1 = 0
Parity bit P2 = D3 ⊕ D6 ⊕ D7 ⊕ D10 ⊕ D11 = 0 ⊕ 1 ⊕ 1 ⊕ 0 ⊕ 1 = 1
Parity bit P3 = D5 ⊕ D6 ⊕ D7 ⊕ D12 = 1 ⊕ 1 ⊕ 1 ⊕ 0 = 1
Parity bit P4 = D9 ⊕ D10 ⊕ D11 ⊕ D12 = 0 ⊕ 0 ⊕ 1 ⊕ 0 = 1
Step 3: The parity bits in the Hamming code are 1 1 1 1, which do not match the calculated parity bits 0 1 1 1. Therefore, this Hamming code contains errors.

Hamming code 2: 1 1 1 1 1 0 0 0 1 1 0 0
Step 1: There are 4 parity bits in this Hamming code.
Step 2:
Parity bit P1 = D3 ⊕ D5 ⊕ D7 ⊕ D9 ⊕ D11 = 1 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 0 = 0
Parity bit P2 = D3 ⊕ D6 ⊕ D7 ⊕ D10 ⊕ D11 = 1 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 0 = 0
Parity bit P3 = D5 ⊕ D6 ⊕ D7 ⊕ D12 = 0 ⊕ 0 ⊕ 0 ⊕ 0 = 0
Parity bit P4 = D9 ⊕ D10 ⊕ D11 ⊕ D12 = 1 ⊕ 1 ⊕ 0 ⊕ 0 = 0
Step 3: The parity bits in the Hamming code are 1 0 0 0, which do not match the calculated parity bits 0 0 0 0. Therefore, this Hamming code contains errors.

Hamming code 3: 0 1 0 1 0 1 1 0 0 0 1 1
Step 1: There are 4 parity bits in this Hamming code.
Step 2:
Parity bit P1 = D3 ⊕ D5 ⊕ D7 ⊕ D9 ⊕ D11 = 0 ⊕ 01 ⊕ 1 ⊕ 1 = 0
Parity bit P2 = D3 ⊕ D6 ⊕ D7 ⊕ D10 ⊕ D11 = 0 ⊕ 1 ⊕ 1 ⊕ 0 ⊕ 1 = 1
Parity bit P3 = D5 ⊕ D6 ⊕ D7 ⊕ D12 = 1 ⊕ 1 ⊕ 1 ⊕ 1 = 0
Parity bit P4 = D9 ⊕ D10 ⊕ D11 ⊕ D12 = 0 ⊕ 0 ⊕ 1 ⊕ 1 = 0
Step 3: The parity bits in the Hamming code are 0 1 0 0, which match the calculated parity bits 0 1 0 0. Therefore, this Hamming code is valid.

Hamming code 4: 0 0 0 0 1 0 0 0 1 0 1 0
Step 1: There are 4 parity bits in this Hamming code.
Step 2:
Parity bit P1 = D3 ⊕ D5 ⊕ D7 ⊕ D9 ⊕ D11 = 0 ⊕ 1 ⊕ 0 ⊕ 0 ⊕ 1 = 0
Parity bit P2 = D3 ⊕ D6 ⊕ D7 ⊕ D10 ⊕ D11 = 0 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 1 = 0
Parity bit P3 = D5 ⊕ D6 ⊕ D7 ⊕ D12 = 1 ⊕ 0 ⊕ 0 ⊕ 0 = 1
Parity bit P4 = D9 ⊕ D10 ⊕ D11 ⊕ D12 = 0 ⊕ 1 ⊕ 1 ⊕ 0 = 0
Step 3: The parity bits in the Hamming code are 0 0 1 0, which do not match the calculated parity bits 0 0 1 0. Therefore, this Hamming code contains errors.

Therefore, only the third Hamming code (0 1 0 1 0 1 1 0 0 0 1 1) is valid.