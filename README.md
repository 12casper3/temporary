provides an explanation for each scan result which in this case was:

> In addition to being obtuse from a syntax perspective, function constructors are also dangerous: their execution evaluates the constructor's string arguments similar to the way `eval` works, which could expose your program to random, unintended code which can be both slow and a security risk.
>
> In general it is better to avoid it altogether, particularly when used to parse JSON data. You should use ECMAScript 5's built-in JSON functions or a dedicated library.

SonarQu



provides an explanation for each scan result which in this case was:

> In addition to being obtuse from a syntax perspective, function constructors are also dangerous: their execution evaluates the constructor's string arguments similar to the way `eval` works, which could expose your program to random, unintended code which can be both slow and a security risk.

> In general it is better to avoid it altogether, particularly when used to parse JSON data. You should use ECMAScript 5's built-in JSON functions or a dedicated library.

SonarQu
