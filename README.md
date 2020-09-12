# Combinatorial Parser

### Functional expressions in Clojure

- Developed functions `constant`, `variable`, `add`, `subtract`, `multiply`, `divide`, `med` and `avg`, that take an arbitrary number of arguments
- An expression parser has been developed that reads expressions in the standard Clojure form


For example:  
Expression `2x-3` representation:
```clj
  (def expr
   (subtract
    (multiply
      (constant 2)
      (variable "x"))
    (constant 3)))
```
`(parseFunction "(- (* 2 x) 3)")` is equivalent to `expr`.

### Clojure Object Expressions

- Developed constructors `Constant`, `Variable`, `Add`, `Subtract`, `Multiply` и `Divide` to represent expressions with variables.
- A function `evaluate` has been developed, that calculates an expression if the values of the variables are known
- A function `toString` has been developed, that displays an expression in the standard Clojure form
- A function `parseObject` has been developed, that parses expressions in the standard Clojure form
- A function `diff` has been developed, that returns an expression representing the derivative with respect to a given variable.

Examples:

```clj
;; 2x - 3
(def expr
  (Subtract
    (Multiply
      (Constant 2)
      (Variable "x"))
    (Const 3)))
    
(evaluate expr {"x" 2}) ;; 1

(toString expr) ;; "(- (* 2 x) 3)"

(parseObject "(- (* 2 x) 3)") ;; expr

(diff expr "x") ;; (Constant 2),

```

### Combinatorial parser

- A function `parseObjectInfix` has been developed that parses expressions written in infix form.
- A function `toStringInfix` has been developed, that displays an expression in infix form
- The system of operator priorities has been implemented, as well as left-associative and right-associative operations.

Examples:

```clj

(toStringInfix (parseObjectInfix "2 * x - 3")) ;; "((2.0 * x) - 3.0)"

(toStringInfix (parseObjectInfix "2 * x + 3 * z")) ;; "((2.0 * x) - (3.0 * z))"

(toStringInfix (parseObjectInfix "2 ** 3 ** 4")) ;; "(2.0 ** (3.0 ** 4.0))"

(toStringInfix (parseObjectInfix "2 + 3 + 4")) ;; "((2.0 + 3.0) + 4.0)"

```
