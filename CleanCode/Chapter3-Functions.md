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
