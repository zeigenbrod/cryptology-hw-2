# HW 2 Analysis
## Zoe Eigenbrod

## Problem 1 

0010110110001011101

1. split into pairs

00 10 11 01 10 00 10 11 10 1

2. determine outputs

00 -> reject

10 -> 1

11 -> reject

01 -> 0

10 -> 1

00 -> reject

10 -> 1

11 -> reject

10 -> 1

1 -> reject

Final output: 10111

1010101010

1. split into pairs

10 10 10 10 10

2. Determine outputs

10 -> 1

10 -> 1

10 -> 1

10 -> 1

10 -> 1


Final output: 11111

### Is its output balanced?

The output is not balanced because there are no 0s.


## Problem 2

(a)

If we know that: 

P(0) = 1 - p
P(1) = p

In neumann's extractor, we only accept mixed pairs, so we look at the probability for each mixed pair

P(0,1) = (1-p)p
P(1,0) = p(1-p)

Add the accepted outcome probabilities together

2p(1-p)

Look at singular outcome compared to both outcomes

P((1,0) | (1,0)+(0,1)) = p(1-p) / 2p(1-p)

Simplified, becomes 1/2


(b)

Assuming the pairs are independent, and the bits within each pair are independent.

Accepted pairs are (0,1) and (1,0). For any given pair, A_i = 1 means the input is accepted, A_i = 0 means the input is rejected.

A bit being uniform means it is equally likely to occur. Each pair is uniform because they both have a probability of 1/2.

Each emitted bit is independent because the pair it comes from is also independent. 

Given k accepted pairs, k bits have a 1/2 chance of being either 0 or 1. If k is bits and z is output:

P(Z = z | L = k) = (1/2)^k = 2^-k


(c)

We must condition L = k to account for different output lengths based on accepted pairs present.

Assuming p = 1/2 and N = 2 

Any given 4 bit sequence has a probability of 1/2 x 1/2 x 1/2 x 1/2 = 1/16

For a 0 output, there are 4 possible sequences:

(01 | 00)
(00 | 01)
(01 | 11)
(11 | 01)

So,
P(Z = 0) = 4(1/16) = 1/4

P(Z = 00) = 1/16 because there is only one possible sequence (01 | 01).

Different lengths do not have the same probability, so we need to condition L = k.

## Problem 3

### Derive the probability of output bit = 1 given accepted

P(0,1) = (1-p)q
P(1,0) = p(1-q)

P((1,0) | (1,0)+(0,1))

= P(1,0) / (P(0,1) + P(1,0))

= p(1-q) / ((1-p)q + p(1-q))

### Show the output is 1/2 if p=q

For a uniform output:
P((1,0) | (1,0)+(0,1)) = 1/2

P(0,1) = (1-p)q
P(1,0) = p(1-q)

so if p(1-q) = (1-p)q 

p-pq = q - pq

p = q

Meaning the output can be uniform iff p=q.

### Evaluate at p=1/2, q=1/4

If we assume 

p = 1/2

q = 1/4

Then,
P(0,1) = (1 - 1/2)(1/4) = 1/8
P(1,0) = (1/2)(1-1/4) = 3/8

P((1,0) | (1,0)+(0,1)) = (3/8) / (1/8 + 3/8) = 3/4

The output is not uniform.

### Give a (p,q) that makes every emitted bit equal

For the emitted bits to be considered equal the bits must be as follows:

p = 0, q = 1

or

p = 1, q = 0

## Problem 4

(a)

X_0 is fair

P(X0 = 0) = 1/2
P(X0 = 1) = 1/2

P(Xi = 1) = P(Xi-1 = 1)(3/4) + P(Xi-1 = 0)(1/4)

= 3/8 + 1/8

= 1/2

Because each bit has a 3/4 probability to be a repeat, and a 1/4 probability to be a new bit

Meaning every X_i is fair.



Probability of 01:

P(01) = P(Xi-1 = 0)(1/4) = 1/8

Probability of 10:

P(10) = P(Xi-1 = 1)(1/4) = 1/8

(b)

There are four possible 4-bit strings where both pairs are accepted:

0101 -> 01 | 01 -> 00

0110 -> 01 | 10 -> 01

1001 -> 10 | 01 -> 10

1010 -> 10 | 10 -> 11

1/2 probability for the first bit, 3/4 for repeat, and 1/4 for changing bit:
P(0101) = (1/2)(1/4)(1/4)(1/4) = 1/128

P(0110) = (1/2)(1/4)(3/4)(1/4) = 3/128

P(1001) = (1/2)(1/4)(1/4)(3/4) = 3/128

P(1010) = (1/2)(1/4)(1/4)(1/4) = 1/128

Probability of both pairs being accepted is:
1/128 + 3/128 + 3/128 + 1/128 = 8/128

The emitted bits agree when the output is 00 or 11:
(1/128 + 1/128) / (8/128) = 1/4

The emitted bits are not independent.

(c)

Failing conclusion is that the emitted bits are independent, output is uniform given L = k. If an input bit is dependent then the emitted bit is dependent. The output bits can each be 50/50 but still be dependent on each other.


## Problem 5

The probability that a pair will be accepted is 2p(1-p)

The yield of bits can be written as

2p(1-p) / 2

bits per input bit = p(1-p)

## H(p) comparisons

### p = 0.50

(0.5)(0.5) = 0.25
yield = 0.25
H(p) = 1

### p = 0.75

(0.75)(0.25) = 0.1875
yield = 0.1875
H(p) = 0.8113

### p = 0.99

(0.99)(0.01) = 0.0099
yield = 0.0099
H(p) = 0.0808

Yield < H(p) due to invalid bits being discarded.

A rejected 00 means two 0s occured in a row.

## Problem 6

### Show that some X makes f(X) constant

If there are 2^n inputs possible, with 2 possible outputs (0/1), that means at least half of the inputs have the same output, as shown below:

2^n / 2 = 2^(n-1) of the inputs have the same output.

### Min-entropy

If X is selected at the same rate from 2^(n-1) inputs:

P(X=x) = 1 / 2^(n-1)

If min-entropy is:

H_∞ (X) = -log2(max P(X=x))

then:

H_∞ (X) = -log2(1 / 2^(n-1)) = n - 1

meaning f(X) is either 0 or 1 every time, so it is not uniform.

### Why this does not contradict Problem 2

Problem 6 looks at bits with min-entropy of n-1, while Problem 2 only looks at bits with independent bias.

