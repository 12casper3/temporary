Furthermore, the three vulnerabilities it found were all of the same kind, namely: `Review this "Function" call and make sure its arguments are properly validated.`. We were unfamiliar with this vulnerability, but fortunately SonarQube provides an explanation for each scan result which in this case was: 
 test

teset

> In addition to being obtuse from a syntax perspective, function constructors are also dangerous: their execution evaluates the constructor's string arguments similar to the way `eval` works, which could expose your program to random, unintended code which can be both slow and a security risk. 
>In addition to being obtuse from a syntax perspective, function constructors are also dangerous: their execution evaluates the constructor's string arguments similar to the way `eval` works, which could expose your program to random, unintended code which can be both slow and a security risk. 
test

teset

> 
test

teset


> In general it is better to avoid it altogether, particularly when used to parse JSON data. You should use ECMAScript 5's built-in JSON functions or a dedicated library. 
test

teset

test

teset

>In general it is better to avoid it altogether, particularly when used to parse JSON data. You should use ECMAScript 5's built-in JSON functions or a dedicated library. 
 
