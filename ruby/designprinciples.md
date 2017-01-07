# Design Principles
_Notes from Practical Object-Oriented Design in Ruby by Sandi Metz_

## Single Responsibility Principle:
* “A class should do the smallest possible useful thing”
   * Should only have ONE reason to change.
   * The one reason to change makes it easy to flow through the rest of your application.
   * Classes that do too much risk breaking your application.
* A class with single responsibility is easy to reuse. 
  * You don’t have to pick and choose which parts of the class to use. 
  * You don’t want to duplicate the code elsewhere (not very DRY, increased bugs ).
* Determining if a class has single responsibility:
  * Rephrase every method as a question and it should make sense. 
    * POODR example is “Mr. Gear, what is your ratio?” vs “Mr. Gear, what is your tire (size)?”
  * Describe what a class should do in one sentence. If you need to use the word “and” or “or,” it has more than one responsibility.
* Write code that embraces change:
  * Depend on behavior (captured in methods) which only lives in ONE place
  * DRY code tolerates change because any change in behavior changes in just one place.
  * Hide instance variables by wrapping them in accessor methods
    * `attr_reader :chainring, :cog` creates chainring and cog from @chainring and @cog 
    * This changes data into behavior, which introduces the issue of visibility (it’s now a public method) as well as narrowing the distinction between data and objects (best to think of things as “plain old objects”).
    * If a change needs to be made to the value of instance variable, you can now change it in one place instead of on every use of @cog
    * Hiding data protects code from unexpected changes.
    * Send messages to access variables as data often as behavior you don’t know about yet.
  * Hide data structures
    * You don’t want things to depend on a certain structure because if that structure changes, every reference must also me changed. 
    * They obscure what data really is.
    * Use Struct class to wrap structures.
      * Structs are “a convenient way to bundle a number of attributes together, using accessor methods, without having to write an explicit class”
      * If input changes, the code will change in just one place
      * Eliminates need to continuously index into a complex array.
      * Protects against external data structure changes
      * Makes your code more readable/intention known.
* Single responsibility is important for methods too.
  * “Separating iteration from the action that’s being performed on each element is a common case of multiple responsibility that is easy to recognize”
  * Having all methods have single responsibility clarifies their effect on the class. Single purpose makes what the class does more obvious.
  * “If a bit of code inside a method needs a comment, extract that bit into a separate method. The new method name serves the same purpose as did the old comment.”
  * Single responsibility in methods helps figure out the scope of a class and also if that class has multiple responsibilities itself.
