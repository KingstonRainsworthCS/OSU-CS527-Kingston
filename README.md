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
