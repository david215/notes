# Step 1 - on top of my head

- variable scope
    - defines the context in which a variable can be looked up from.
    - e.g. a variable declared in an if block cannot be referenced from outside.

- access modifiers
    - most commonly used: public, default, protected, private.
    - defines which other classes can access fields and methods of a class.
    - e.g. fields are most often private and inaccessible directly; a class
      provides a public getter or setter methods if appropriate.

- OOP
    - a programming paradigm designed to simulate the real world.
    - defines systems in terms of objects and their interactions and
      relationships.

- class and instance
    - a class is a definition of an object, i.e. data and operations it
      supports.
    - an instance is a realization of an object.

- inheritance vs composition
    - inheritance
        - a 'is-a' relationship between objects, e.g. jindo is a dog.
    - composition
        - a 'has-a' relation between objects, e.g. car has 4 wheels.

- interface vs abstract class
    - similarities
        - both are "abstract" in the sense they are not concrete, i.e. cannot be
          initialized.
    - differences
        - an interface only defines the method signatures (used to... at least).
        - an abstract class can have default implementations of methods and also
          default fields.
        - only interface supports multiple inheritance in Java, i.e. a class can
          inherit from multiple interfaces, but not abstract classes.

- method overloading and overriding
    - overloading
        - same method name, but different parameters.
        - e.g. constructors can take different parameters.
    - overriding
        - same signature (method name, parameters, return type all included).
        - e.g. a subclass can override an inherited superclass method.

- enum
    - is an enumeration, i.e. listing of elements.
    - e.g. enum Day { Monday, Tuesdsay, ... }
    - is an enum *class* in Java and supports method calling as well.

- exception handling
    - Exception handling allows programmers to define the behavior a program
      when exceptions occur instead of just halting the program.
    - Two types of exceptions: checked and unchecked (including errors)
        - checked exceptions are caught at compile time.
        - unchecked exceptions require explicit exception handling with try /
          catch or `throws` method signature.
    - There exists an exception hierarchy with BaseException class at its root.
    - try with (i.e. try (some resource) { ... }) was introduced not too long
      ago; useful!

- Collection framework
    - the java.util.Collection module contains commonly used collections
      including lists, sets, maps, and so on.
    - faciliates creating a new collection objects from an existing collection
      object, e.g. create a new Set from a List.

- inner class vs nested class
    - inner class is a non-static class within a class.
        - can only be accessed if its outer class is initialized.
    - nested class is a (private) static class within a class.
        - can exist without its outer class and if not private, can even be
          accessed from outside, e.g. new Tree.Node();

- lambda
    - is an anonymous function, and was introduced in Java 8 to support
      functional programming.
    - can replace the the implementation of Functional interface for simpler
      functions.

- stream
    - functional programming element introduced in Java 8.
    - Collection interface defines stream() method for all implementing classes
      and Arrays class also provides a static stream method.
    - can result in performance degradation...

- Optional
    - usually used with stream.reduce method which returns an Optional.
    - also provides a static method for providing a default value if a return
      value is null.

- IO stream
    - different from FP stream!
    - accessed through System.in and System.out.
    - best practice: BufferedReader in = new BufferedReader(new
      InputStreamReader(System.in);
