# Task 2

Write, from scratch, a function in Racket that takes a positive integer n0 as input and returns a list by recursively applying the following operation, starting with the input number.

![](https://user-images.githubusercontent.com/22341150/36096795-cced4a8a-0fef-11e8-910e-fe88d96cb85a.PNG)

 End the recursion when (or if) the number becomes 1. Call the function collatz-list. So, collatz-list should return a list whose ﬁrst element is n0, the second element is n1, and so on. For example: 
 ```Racket
 > (collatz-list 5) '(5 16 8 4 2 1) 
 > (collatz-list 9) '(9 28 14 7 22 11 34 17 52 26 13 40 20 10 5 16 8 4 2 1) 
 > (collatz-list 2) '(2 1)
 ```

 ## What is Collatz Conjecture?
 The Collatz conjecture is a conjecture in mathematics that concerns a sequence defined as follows: start with any positive integer n. Then each term is obtained from the previous term as follows: if the previous term is even, the next term is one half the previous term. Otherwise, the next term is 3 times the previous term plus 1. The conjecture is that no matter what value of n, the sequence will always reach 1.

 ### Step 1
 Create a function that takes in a number, check if the number is odd or even:
 ```Racket
(define (collats-list n)
  (if (even? n) ; using racket even function to check if number is even then..
      #t ;true
      #f ;false

(collats-list 5) ; pass in 5
 ```

### Step 2
Add our collatz algorithm:
```Racket
(define (collats-list n)
    (if (even? n) ; if number is even then..
        (/ n 2) ; divide by 2
        (+ 1 (* 3 n)))) ; if odd, multiply by 3 and then add 1.

(collats-list 5) ; pass in 5

```
### Step 3 
Next we need the function to end once it returns 1 and return a list of values the algorithm goes through until it hits 1:
```Racket
#lang racket
; Define our collatz-list function.
(define (collatz-list n)
  ; Using cond-clause as there are a few conditions..
  (cond ((= n 1) ; if n = 1 then..
         '(1)) ; return 1, otherwise...
        ((odd? n) ; if number is odd then..
         ; cons returns a pair (list) of results with the last element being 1
         (cons n(collatz-list (+ 1(* 3 n))))) ; multiply by 3 and add 1.
        (else ; otherwise, if number is even then..
         (cons n (collatz-list (/ n 2)))))) ; divide by 2         
  

(collatz-list 5) ; odd number
(collatz-list 10) ; even number


```

## References
- https://docs.racket-lang.org/reference/if.html
- https://docs.racket-lang.org/reference/number-types.html
