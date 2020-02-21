# Do One Thing
- How do we determine what "one thing" is?
    - A function does only one thing when:
        - The function does only those steps that are **one level below** the
          stated names of the function.
            - e.g. `if x is y, then apply f to x, and then return x` **is** one
              thing.
        - You **cannot extract another function** from it with a name that is
          not merely a restatement of its implementation.
            - N.B. blocks within `if` statements, `else` statements, `while`
              statements and so on should be one line long, probably a function
              call.
        - Statements within a function are at the same level of abstraction.
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
    - Using descriptive names can help identify functions that are doing more
      than just one thing.
    - The smaller and more focused a function is, the easier it is to choose a
      descriptive name.
    - Hunting for a good name often results in a favorable restructuring of the
      code.
- Have no side effects
    - "Side effects are lies. Your function promises to do one thing, but it
      also does other hidden things."
    - Hidden side effects can be disastrous, especially if it creates temporal
      couplings and order dependencies.
        - If there exist temporal couplings / order dependencies, you should
          make them clear in function names.
- Command query separation
    - A function should either do something or answer something, but not both.
        - a confusing example:
        ```java
        public boolean set(String attribute, String value);
        if (set("name", "David")) { ... }
        ```
        - a better solution:
        ```java
        if (hasAttribute("name)) {
            setAttribute("name", "David");
            ...
        }
        ```
- Error handling
    - Prefer exceptions to returning error codes.
        - Returning error codes is a violation of command query separation.
    - Error handling is *one thing*.
        - "Functions should do one thing. Error handling is one thing. Thus, a
          function that handles errors should do nothing else."
    - Extract try/catch blocks.
        - Try/catch blocks confuse the structure of the code and mix error
          processing with normal processing.
        - So extract the bodies of try/catch blocks into functions of their own.
- Dealing with switch statements
    - Obviously, functions with switch statements (or if/else chains) are not
      doing just one thing.
    - Should only be used to create polymorphic objects in the basement of an
      abstract factory.

# Function Arguments
- Less arguments the better
    - niladic, monadic, dyadic, triadic...
    - As the number of arguments grows, the function becomes harder to reason
      about.
    - From a testing point of view, it is best to avoid the scenario of
      reasoning about every possible combination of arguments.
- Common monadic forms
    1. Ask a question about the argument.
        - e.g. boolean fileExists("MyFile")
    2. Operate on the argument, transform it into something else, and return it.
        - e.g. InputStream fileOpen("MyFile")
    3. Event: there is an input argument but no output argument
        - use the argument to alter the state of the system.
        - e.g.  void passwordAttemptFailedNTimes(int attempts)
- Reducing the number of arguments
    1. Make the function a method, e.g. writeField(outputStream, name) ->
       outputStream.writeField(name)
    2. Make the argument a field of the class so you don't have to pass it.
    3. Make argument objects/lists, e.g. Point class, variable arguments.
- In relation to function names
    - The function and argument should form a **verb / noun pair**, especially
      in the case of monadic functions.
        - e.g. write(name), or even better, writeField(name) for further
          clarificaiton.
    - If there are more than one argument, we can use the **keyword form** to
      encode the names of the arguments into the function name.
        - e.g. assertExpectedEqualsActual(expected, actual)
- Output arguments
    - Arguments are most naturally interpreted as **inputs** to a function,
      **not outputs**; in general output arguments should be avoided.
    - If a function must change the state of something, have it change the state
      of its owning object.
        - e.g. appendFooter(report) -> report.appendFooter()
- Flag arguments
    - A "truly terrible practice" which immediately signals that a function does
      more than one thing (if flag is true, do X; else do Y).

