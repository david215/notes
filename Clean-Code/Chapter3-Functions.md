# Do One Thing
- How do we determine what "one thing" is?
    - A function does only one thing when:
        - the function does only those steps that are **one level below** the
        stated names of the function.
            - e.g. `if x is y, then apply f to x, and then return x` **is** one
            thing.
        - you **cannot extract another function** from it with a name that is
        not merely a restatement of its implementation.
            - N.B. blocks within `if` statements, `else` statements, `while`
            statements and so on should be one line long, probably a function
            call.
        - statements within a function are at the same level of abstraction.
            - i.e. high level method call shouldn't be in the same function as
            low level direct manipulation of data.
            - *The Stepdown Rule*
                - Every function should be followed by those at the next level
                of abstraction, so that the code is read like a top-down
                narrative.
                - e.g.
                ```
                A baseball game is over when...
                A frame is over when...
                A batter is out when...
                ```
- Use descriptive names
    - using descriptive names can help identify functions that are doing more
      than just one thing.
    - the smaller and more focused a function is, the easier it is to choose a
      descriptive name.
    - hunting for a good name often results in a favorable restructuring of the
      code.
- Have no side effects
    - "Side effects are lies. Your function promises to do one thing, but it
      also does other hidden things."
    - hidden side effects can be disastrous, especially if it creates temporal
      couplings and order dependencies.
        - if there exist temporal couplings / order dependencies, you should
          make them clear in function names.
- Dealing with switch statements
    - obviously, functions with switch statements (or if/else chains) are not
      doing just one thing.
    - should only be used to create polymorphic objects in the basement of an
      abstract factory.
- Flag arguments
    - a "truly terrible practice" which immediately signals that a function does
      more than one thing (if flag is true, do X; else do Y).

# Function Arguments
- Less arguments the better
    - niladic, monadic, dyadic, triadic...
    - as the number of arguments grows, the function becomes harder to reason
      about.
    - from a testing point of view, it is best to avoid the scenario of
      reasoning about every possible combination of arguments.
- Common monadic forms
    1. ask a question about the argument.
        - e.g. boolean fileExists("MyFile")
    2. operate on the argument, transform it into something else, and return it.
        - e.g. InputStream fileOpen("MyFile")
    3. event: there is an input argument but no output argument
        - use the argument to alter the state of the system.
        - e.g.  void passwordAttemptFailedNTimes(int attempts)
- Reducing the number of arguments
    1. make the function a method, e.g. writeField(outputStream, name) ->
       outputStream.writeField(name)
    2. make the argument a field of the class so you don't have to pass it.
    3. make argument objects/lists, e.g. Point class, variable arguments.
- In relation to function names
    - the function and argument should form a **verb / noun pair**, especially
      in the case of monadic functions.
        - e.g. write(name), or even better, writeField(name) for further
          clarificaiton.
    - if there are more than one argument, we can use the **keyword form** to
      encode the names of the arguments into the function name.
        - e.g. assertExpectedEqualsActual(expected, actual)
- Output arguments
    - arguments are most naturally interpreted as **inputs** to a function,
      **not outputs**; in general output arguments should be avoided.
    - if a function must change the state of something, have it change the state
      of its owning object.
        - e.g. appendFooter(report) -> report.appendFooter()
