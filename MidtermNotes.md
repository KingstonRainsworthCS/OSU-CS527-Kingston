## Topic:
### Entropy:
Describe how much bits an event will have
H(X) given X is the vent with probabilty p = p*log(1/p)
H(X,Y) = Sum (i from 1 to n) p(xi,yi)*log2(1/p(xi,yi))
H(X|Y) = Sum (i from 1 to n) p(yi)*H(X|Y=yi)
H(X|Y=ym) = Sum (i from 1 to n) p(X=xi | Y=ym)*log2(1/p(X=xi | Y=ym))



### Source Coding

#### Optimal code

Given Pi Pj for character Xi and Xj, average length of code for X i and Xj, denoted Li and Lj

If Pi <= Pj, Li <= Lj

character with smaller probability must have longer code length

#### Non-singular
xi != xj => C(xi) != C(xj)

Any character must have a different codewird

#### Extension:
C(xixj) = C(xi)C(xj)

#### Uniquely decodable code
the extension must also be non-singular

#### Prefix code
One code word cannot be prefix of another one

#### Instantaneous
Can be decode immediately without waiting for the whole string
