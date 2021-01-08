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

####
### Day 3 notes
