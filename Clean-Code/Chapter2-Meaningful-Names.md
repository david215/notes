- Use **intention-revealing** names
    - > If a name requires a comment, then the name does not reveal its intent.
    - > The problem isn't the simplicity of the code but the *implicity* of the
    code.
        - i.e., **be explicit**.
- Avoid **disinformation** 
    - Avoid ambiguous or misleading names.
    - e.g. don't name a collection of accounts `accountList` when it's not a
    list.
- Make meaningful **distinctions**
    - Noninformative names
        - e.g. `a`, `d`
        - e.g. `productInfo` vs `productData`
- Use pronounceable names
    - key to communication
- Use **searchable** names
    - > The length of a name should correspond to the size of its scope.
        - > If a variable or constant might be seen or used in multiple places
        in a body of code, it is imperative to give it a search-friendly name.
        - e.g. naming a global variable `e` will make it impossible to search
        for it, but `i`, `j`, `k` in a local loop is acceptable.
- Class names and method names
    - Classes and objects should have noun or noun phrase names.
        - e.g. Customer, Account
    - Methods should have verb or verb phrase names.
        - e.g. postPayment, deletePage
        - For overloaded constructors, use factory methods with verb names.
            - `Complex example = new Complex.FromRealNumber(23.0)`
- Pick one word per concept
    - e.g. don't use `fetch`, `retrieve`, and `get` together.
- Add meaningful context
    - e.g. `state` variable by itself vs `Address.state`
    - i.e. create necessary classes, methods to provide context.
