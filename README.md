## Identifying debt

In this chapter we investigated the technical debt of the phaser repository.  
Technical debt is all about how much it would cost extra in the future if you have to redevelop a solution which was chosen now, instead of applying a better solution now that would take more time.  
So technical debt concerns the code quality of a software project and if this code was tested properly.  
To analyze the technical debt, we use code quality tools like SonarQube to get an overview of the source code quality to detect pieces of software that could be improved.

### Code quality tools analysis results

We chose to use two different online code quality tools: SonarQube \(we used SonarCloud as online platform for it\) and DeepScan. As SonarQube gave more results we decided to start improving our technical debt with this tool. The results of both scans are discussed in the following sections.

#### SonarQube

SonarQube works with 4 categories to measure the code quality. The first category scans the project for bugs and vulnerabilities, where bugs are related to the reliability and the vulnerabilities are related to the security of the system. The initial scan resulted in the following amount of bugs/vulnerabilities:  
![](/chapter-3/images/sonarqube/bugs.PNG)

The bug scans looks for parts of code that could fail, for example possible null references or syntax errors.  
It identified some typo's, some cases where a variable could be null or undefined when it is used.  
About 19 of the 35 bugs are related to the potential unintended use of bitwise operator `&` instead of conditional `&&`.  
This bitwise operator appears in a if-condition usually in combination with a mask of some sort resulting in a number.  
This number is then implicitly compared by JavaScript to see if it is zero \(false\) or something else \(true\).  
For readability it might be good to change this to an explicit comparison like `(a&b) != 0`, but this depends on the type of developer and their experience with masks.

Furthermore, the three vulnerabilities it found were all of the same kind, namely: `Review this "Function" call and make sure its arguments are properly validated.`. We were unfamiliar with this vulnerability, but fortunately SonarQube provides an explanation for each scan result which in this case was:

> In addition to being obtuse from a syntax perspective, function constructors are also dangerous: their execution evaluates the constructor's string arguments similar to the way `eval` works, which could expose your program to random, unintended code which can be both slow and a security risk.
>
> In general it is better to avoid it altogether, particularly when used to parse JSON data. You should use ECMAScript 5's built-in JSON functions or a dedicated library.

SonarQube estimates that the time required to fix the bugs is around 4 hours and the time to fix the vulnerabilities is about 15 minutes. SonarQube also analyzes the technical debt and code smells:

![](/chapter-3/images/sonarqube/codesmells.PNG)

This is a very positive result, a technical debt of only two days. The code smells include redundant and unused code, confusing code and more. Fixing these code smells will improve the maintainability of the system. By quickly analyzing these code smells it becomes clear that most of these are related to useless assignments or unused variables, so fixing these code smells will not cost much effort. The most of the other code smells were related to boolean expressions which always seem to evaluate to true.

Another aspect SonarQube looks at is test coverage:

![](/chapter-3/images/sonarqube/coverage.PNG)

This is where the project really lacks behind; it simply does not have any tests. More on this in the Testing debt section.

The final aspect SonarQube check is code duplication:

![](/chapter-3/images/sonarqube/duplication.PNG)

Obviously code duplication is generally bad practice as it makes the system more difficult to maintain. Fortunately Phaser has very low code duplication. In fact, the two files with the most duplication are debug classes, which are not part of the actual system.

#### DeepScan

The other tool we used was DeepScan, a code analysis tool specifically for JavaScript.

![DeepScan analysis](./images/deepscan/analysis.png)

DeepScan was able to find a total of 48 issues:

![DeepScan issues](./images/deepscan/issues.png)

These were mostly issues which were also found by SonarQube. The SonarQube scan however provided much more insight into the technical debt of the system, which is why we decided to concentrate on those results.

### Testing debt

As mentioned before the project does not contain any automated tests, apart from the Travis continuous integration use. The extensive example repository with small pieces of example code for each part of the system is used as a way of manual testing.

It could be argued that is hard to test a gaming framework, which in part is true. For example, how would you test that for example a certain shape is drawn on the screen as expected? This however, is not an excuse to not have any tests at all. Unit tests could be used to test the logic of the code. The project would benefit from this as it could assure that for example the wide variety of calculations done by the framework are correct. When investigating ways to test a JavaScript game engine we stumbled upon the [Crafty game library](https://github.com/craftyjs/Crafty). This project is tested with a JavaScript unit testing framework called [QUnit](https://qunitjs.com/), which could be a useful addition to the Phaser project. Setting up a test environment for this project would however require a lot of in-depth knowledge on the inner workings of the systems and calculations, which would make it very time consuming for us.

