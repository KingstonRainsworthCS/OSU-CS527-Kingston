# OSU-CS527-Kingston
CS 527 Error-correcting codes

## Sylabus
[Canvas links](https://canvas.oregonstate.edu/courses/1795317/assignments/syllabus)

## Office hours
 MW 11AM-noon and R: 2PM-3PM

## Grade breakdowns

| Type             | Percentage    |
| ---------------- |:-------------:|
| Weekly Homework  | 35% / 10      |
| Mid term         | 25%           |
| Term paper       | 15%           |
| Final            | 25%           |

## Week 1

* Introduction

### Assignments

* TBA

### Day 1 notes

Term paper is done as group work, summarize studies of 1-2 paper concerning topic around information theory

### Number guessing game

From set {0, 1, 2, 3, 4, 5, ...15} guess a number by asking question => Binary search is fastest way

Arrange set to group of binary group (1 at every position) and check if number belong to a certain set:

{ 4, 5, 6, 7 } 0
{ 2, 3, 6, 7 } 1
{ 1, 3, 5, 7 } 1

Add check to detect 1 lie

### Hat color game

3 player as a team guess color of their hat (Red or Black), win if at least one correct guess is made and no wrong guess is made

Startegy: look at other player color, if different pass if same guess opposite

### Outline

Given a source and destination, source will try to send information to destination via a channel (noisy channel with probability of error > 0)  with a rate ( source bit / encoded bit )

Source coding: encode message in way to minimalize length, e.g.

a (50%) => 0, b (25%) => 10, c (12.5%) => 110 d (12.5%) => 111 would give 1.75 bits per character (versus 2bits with regular binary encoding)

### Noisy channel coding theorem

For every memoryless channel, the capacity, C (maximal mutual info between in/output) has the follow property:

For any e > 0 and rate R < C, for large enough n, there exists a code of length N and rate >= R and a decoding algorithm such that the maximal probability of block error is < e.

"This means that, theoretically, it is possible to transmit information nearly without error at any rate below a limiting rate, C."

If probability of bit error pb is acceptable, rates up to R(pb) are achievable, where

R(pb) = C / 1 (1 - H(pb))

Where H() is the binary entropy function

For any pb, rates greate than R(pb) are not achievable

### Day 2 notes

#### Bayes theorem

Given two random var, x and y and some output xi (i=1,2,3, ..., n) and yi

P(X/Y) = P(Y/X)*P(X) / P(Y) = P(X,Y)/P(Y)

#### Entropy

let x be a random variable with output xi (i from 1 to n) with probability p(xi),

entropy (bits) (certainty of information) H(X) = Sum (i from 1 to n) p(xi)*log2(1/p(xi))

In binary outputs, maximum entropy is 1 achieve at p = 0.5

Joint entropy
H(X,Y) = Sum (i from 1 to n) p(xi,yi)*log2(1/p(xi,yi))

Conditional entropy

H(X|Y) = Sum (i from 1 to n) p(yi)*H(X|Y=yi)

H(X|Y=ym) = Sum (i from 1 to n) p(X=xi | Y=ym)*log2(1/p(X=xi | Y=ym))

## Week 2

### Day 1 notes

#### Mutual Information I(X,Y)

Let X and Y be two random variables, the mutual information is defined as:

I(X,y) = H(X) - H(X/Y) = H(Y) - H(Y/X)

I(X,Y) is the cross section of a venn diagram displaying H(X) and H(Y)

#### Relative entropy

Given two probabilities mass functions:

D(p || q) = Sum (i from 1 to n) p(n)log(p(x)/q(x)) always greater than or equal 0

#### Source coding


## Week 3

### Day 1 notes

#### Huffman's encoding (Optimal encoding)

Subsequently construct a tree by combining two least probable character probability to create superset of character in binary form as a new root for those characters

#### D-ary Huffman's encoding
For D= {0,1,2,3, ... D-1}, every internal node must have out degree of D-1

The number of leaf nodes N congruence 1 mod (D-1)

Hint: use optimal proof in lecture video for Q4

#### Optimal code

Given Pi Pj for character Xi and Xj, average length of code for X i and Xj, denoted Li and Lj

If Pi <= Pj, Li <= Lj

The two longest code word must have the same length

The two longest code word must differ only in the least significant bits
Encoding at the source before sending

### Day 4 notes

#### Source coding cont.

Given coding scheme C, the following property exists:
Non-singular
xi != xj => C(xi) != C(xj)

Extension:
C(xi xj) = C(xi)C(xj)

Uniquely decodable code: the extension must also be non-singular

Prefix code:
One code word cannot be prefix of another one

Instantaneous:
Can be decode immediately without waiting for the whole string

#### Kraft's inequality
Given list of character D = {0,1,2,..D-1}
sum from i=1 to n of 1/D^li <= 1

Use to test if given codes is prefix codes


given character x1 -> xi with probability p1 -> pi encode to length l1 -> li
Sum from i=1 to n of Pi * li >= H(X) (entropy of probabilty of characters)
Average length of code must always be greater than entropy
#### Shannon - Fano encoding

X        Y        Z         characters
P1       P2       P3        probabilities
log1/P1  log1/P2  log1/p3   length

## Week 5

### Day 1 notes
#### Hamming code

Single error correcting, double error detecting (SECDEC)
length n = 2^r -1
number of check bits = r



#### Hamming distance
Hamming distance d(x,y) between two n-tuples is the number of positions they differ:
X=11010
Y=01001
=> D(X,Y) = 3

Properties of distance (vector):
* D(X,Y) >= 0
* D(X,Y) = D(Y,X)
* D(X,Y) + D(Y,Z) >= D(X,Z)
Min distance of a code:
Min of every pair of code in a set of possible code word

1. A code C is capable of detecting t errors if and only if the min Hamming distance of code is t+1 (always possible to find this code too)
2. A code C is capable of correcting t-errors if and only if the min Hamming distance is 2t + 1
3. A code C is capable of correcting t-errors and simultaneously detect d>= t errors if and only if the min distance of the code is t+d+1

### Day 2 notes
#### Sphere packing bound
|C| <= 2^n/(1+(nC1)+(nC2)+(nC3)+...(nCt))
for n is the length of bits and t is the number of possible error correction

#### t-error correcting code
Correct up to t errors

### introduction to algebra

#### group

Group(G,*) where G is a set of elements, * are binary operator
Properties:
1. Closures: forall a, b in G, a*b must be in g
2. Associative: (a\*b)\*c = a\*(b\*c)
3. Identity: there must exist a element I in G such that  a + I = I + a
4. Inverse: exist an element where a^ where a\*a^ = a^*a = I
5. Communicative (optional): a\*b = b\*a, if satisfy go to abelian group

#### subgroup
subgroup H of a group G is the subset of element in G that satisfy all properties of said group
number of elements in a subgroup always divides the number of elements in the group

#### coset
coset of subgroup H is any set express-able as a + H

#### Field
Field(F,+,*)

1. (F,+) must be a abelian group
2. (F-{I},*) abelian group
3. Distributive: a(b+c) = ab + ac

#### Galois Field

Can do addition, subtraction, multiplication and division

## Week 6

### Homework hints
1. Hamming code examples
2. Erasure error: 000 -> 0*0
3. Same with 2, now also correct a normal error. If distance is 2t +1 we can do t error correction
4. Use picture, triangle inequalities, N(X,Y) >= t+1, look at N(X,X1) N(Y,Y1)
5. Assymetric (error is always  all + or - from original at every bits) of magnitude l (+-l), use same principle as 4.
6. singular is possible by parity bits, two error detect via  parity on row or column, miss-corrected at 3 when all 3 are in a grid shape, divide by C(m*n,3)
7. kinda obvious after looking into cross parity

#### Vector space
1. (V,+) over field (F,+,*) form an abelian group
2. For any a in F and any V in V, a.v is in V

A sets of vectors is called linearly independent if a1v1 + a2v2  ... + akvk = 0 implies a1 a2 ... ak = 0
A sets of vectors is said to span a vector space V if any u in V can be written as u = a1v1 + a2v2 + ... + akvk
Every vector space have at least one set of vector that span the space. This is the basis
The number of elements in the basis is called the dimension of the vector space
Two vector are orthogonal if inner product v.u = 0
Dual space: all vector is orthogonal to all vectors of another subspace
