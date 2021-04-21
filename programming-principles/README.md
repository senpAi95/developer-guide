# programming-principles
Principles of programming

These are the universal laws and princples in software development which can guide developers and anyone about to design a software. This is my attempt of understanding those principles.

## KISS - Keep it short and simple

Its stricing for simplicity. Frameworks might often have sophisted solutions for a simple problem. Developers might feel tempted to write a clever solution that uses complex features. KISS principle states that there is no value in a solution being clever but in one being easily understandable. This doesn't mean we are not supposed to use inheritance or polymorphism but rather use them only when its necessary or if there is some substantial advantage.
 
 Why?
 
 A simpler solution is easy to maintain and better to understand than a complex one. This includes readability, understandability. Writing simple code is less error prone. There is a bigger advantage when the person who maintains the software is not the one who wrote it.

```“When you make your code more flexible or sophisticated than it needs to be, you over-engineer it. Some do this because they believe they know their system’s future requirements. They reason that it’s best to make a design more flexible or sophisticated today, so it can accommodate the needs of tomorrow. That sounds reasonable, if you happen to be a psychic.” - Refactoring To Patterns - Joshua Kerievsky.```

To Summarize,
  * Simple solutions are faster to implement.
  * Simpler solutions yield fewer implementation faults (reduces testing effor).
  * Easy to maintain ( detecting and correcting defects is more effective and efficient).
  * Perfection is reached not when there is nothing left to add, but when there is nothing left to take away.

## YAGNI - You aren't gonna need it.

Don't implement something until it is necessary.


Why? 

Any work that's only used for a feature that's needed tomorrow, means losing effot from features that needs to be done for current iteration. It also leads to code bload. Always implement things when you actually need them, never when you just forsee that you need them.


## Seperation of Concerns

Its a design principle for separating a computer program into distinct sections, such that each section addresses a separate concern. For example, business logic is a concern and the user interface is another concern. Changing the user interface should not require changes to business logic and vice versa.

Why? 

* Simplify development and maintenance of software applications.
* When concerns are separeated individual sections can be reused, as well as developed and updated independently.

How?

Break Program functionality into separate modules that overlap as little as possible.
