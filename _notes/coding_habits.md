---
layout: page 
title: Coding Practices

---
## A. Best Coding Habits
1. Keep Code Clean
    1. Design- 
        1. 'Don’t expose the internals
        2. Keep implementation details hidden
    2. Dispensables
        1. Remove dead code
        2. Avoid print statements
    3. Variables
        1. Variable names should reveal intent
    4. Functions
        1. Use functions to keep code ‘DRY’ (don’t repeat yourself)
        2. function should do one thing
2. Use functions to abstract away complexity
    1. By doing so we gain- readability, testability, reusability
3. Smuggle out-of-the-jupyter notebooks asap
    1. Law of flat surfaces- any flat surface at home accumulates clutter. Jupiter notebooks are flat surface of the ML world
￼
4. Apply test-driven development
    1. Write unit-tests
    2. Write functional-test to assert that the metrics of the mode are above our expected threshold
5. Make small and frequent commits

## B. Common Code Smells
1. Dead code - does not affect the output, distracts the flow (eg. print statements)
2. Exposed internals - abstract details in function
3. Duplication - create a function
4. Irrelevant variable names
5. Magic numbers

## C. Refactoring process

### Pre-requisites
1. Local dev environment is set-up
2. Run notebook and ensure it works
3. Make a copy of the notebook
4. Remove print statements
5. Read notebook and list code smells
6. Convert notebook as python file
7. Determine boundary of refactoring and ass characterisation test there

### Refactoring steps
1. Run tests in watch mode
2. Identify a block go code that can be extracted into a pure function
3. The refactoring cycle
    1. Write a test
    2. Create a python module and define a function
    3. Make the test pass
    4. In the notebook, replace original code block with the newly defined function
    5. Restart and run entire notebook
    6. Commit your changes
4. Add functional test for ML model
5. Celebrate :)

**Reference**
1. [https://www.thoughtworks.com/insights/blog/coding-habits-data-scientists](https://www.thoughtworks.com/insights/blog/coding-habits-data-scientists)
2. Pep-8 style guide summary- [https://tandysony.com/2018/02/14/pep-8.html](https://tandysony.com/2018/02/14/pep-8.html)


**To-do**
1. Learn Unit-testing
2. Learn Version-control
