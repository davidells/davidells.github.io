---
id: 525
title: Functional Programming
date: 2013-02-25T03:18:18+00:00
author: dells
layout: post
guid: http://davidells.info/blog/?p=525
permalink: /2013/02/some-notes-on-functional-programming/
img: 2013/02/lambda.jpg
dsq_thread_id:
  - "1103286494"
categories:
  - Uncategorized
---

_Functional programming refers to a style of programming that has been enjoying a revival of sorts, and presents a strong alternative to object oriented programming. When you hear folks say things like &#8216;Javascript is actually a very powerful language&#8217;, they are probably referring to it&#8217;s support for functional programming concepts like lambdas and closures._

_Languages like Scala, Haskell, Clojure, among others, continue to attract programmers every day because of their deep support for functional programming style. Listed below are some core tenents of functional programming:_

**Functions are the core abstraction, and first class citizens.** &#8211; Object oriented programming is sufficient for many problems, but is mostly over applied. A functional style which packs more into functions and less into objects has the potential for better modularity and re-usability. Giving functions first class status, allowing them to be passed as arguments to other functions and returned from other functions, gives rise to higher order functions and lets us abstract not just interfaces and contracts for objects, but functional execution structure, transformations of data, cross cutting concerns, and so on.

**Values are immutable.** &#8211; Immutability of values eases the challenge of reasoning about program correctness by taking out one of the most complex pieces of a program: shared mutable state. Programs can instead be defined solely through inputs and outputs of functions. It also eases the way we reason about concurrent access: immutable values, since they cannot be changed, are naturally thread safe. (At this point, that sounds like a silly cop out: &#8220;get rid of the synchronization problem by avoiding mutability&#8221;&#8230; I mean, concurrent programs need to alter shared data, right?) At any rate, ubiquitous mutability, and code that relies on the particular state of objects, gives rise to programs that are a bit more like spaghetti, because there could be very complex interactions happening between many clients that are sharing and mutating the same state. Obviously, some mutable state is necessary (IO in particular!), but it should be used judiciously, not by default.

**Lambdas and Closures are powerful tools.** &#8211; This is really an extension of the tenet regarding functions as the core abstraction. Lambdas are just unnamed functions, and tend to take out lots of boilerplate that would otherwise be required. Closures refer to a runtime behavior that preserves the values within the enclosing scope of where a function has been declared (typically a lambda function). This is a powerful tool for creating functions that are parametrized in some way during creation.

**Functions should not have side effects.** &#8211; This is the main strategy in avoiding mutable state and the pitfalls that go with it. Side effect free functions do not alter any global or shared state, and return output which is predictably derived from its inputs. This is called referential transparency, and is important in program reasoning and execution. If a function call and its output are logically equivalent, the runtime can defer function calls, or automatically execute function calls in parallel (since there&#8217;s no way for side effect free functions to rely on global state or even order of execution, as long as one is not an input to another). See also: idempotent.

**Declarative over imperative code.** &#8211; Functional programs tend towards a declarative style instead of an imperative style. That is, instead of telling the computer how to do some set of steps to calculate something, you tell the computer about a set of rules and functions and relationships, and the runtime uses these to compute the final value. Hence, you lean on the runtime to do a lot of &#8220;boilerplate&#8221; execution, and end up with a program that contains just the declaration of the logic and rules for the program. 

**Recursion over explicit iteration.** &#8211; Fallout from previous tenet. A declarative style is likely to favor recursion over iteration when repetition is needed. Iteration isn&#8217;t strictly forbidden, but mutable state like a loop counter is. Recursion is typically optimized in a functional language with a technique called tail-recursion, which is enabled by ensuring that a recursive call to a function is the final operation called in the function. Some nice examples of elegant recursive definitions: fibonacci numbers, factorials, quicksort, and many others.

**Lazy evaluation is a good thing.** &#8211; If state is immutable, and functions maintain referential transparency, than we can logically consider a function and set of inputs to be equal to the output of the function. This means a runtime can defer expensive function calls, and only execute them when the output is needed. Also, lazy evaluation is the only way to represent logically infinite data sets and data structures. Lazy evaluation let&#8217;s us only compute the needed subset of some infinite data structure (like fetching the first 10 entries from &#8220;the set of natural numbers&#8221; which is an infinite data set).

**_Here are a few other points to note about functional programming:_**

**Algebraic Data Types** &#8211; Algebraic data types are a bit different than the commonly known abstract data types. While the latter says &#8220;here&#8217;s some interface and contract of behavior, regardless of implementation&#8221;, the former is more concerned with defining structure specifically, and doing so in a known finite way. Instead of saying &#8220;you can make any subtype of this interface&#8221;, it&#8217;s saying &#8220;this is a type, which may only exist as these other known types&#8221;. See [this wikipedia article](http://en.wikipedia.org/wiki/Algebraic_data_type) for a decent recap, and also [one of its references](http://foldoc.org/algebraic+data+type)

**Core collection types and functions** &#8211; Functional programming&#8217;s foundation is made up of some basic but powerful building blocks. Core collection types like list and map give us a way to structure data, while core functions like filter, map, and fold give us composable pieces of highly reusable code. In regards to transforming data, these are invaluable. To say these are the fundamental elements of any functional program would be an understatement. They are powerful abstractions that can be composed and reused far more than the specialized types and methods typically created in an object oriented program. Here&#8217;s a random online [recap of map, fold, and filter](http://www.cse.unsw.edu.au/~en1000/haskell/hof.html). These functions are so composable because they are [higher order functions](http://en.wikipedia.org/wiki/Higher-order_function).

**Concurrent programming primitives** &#8211; Functional programming seems to be especially leveraged for concurrent or distributed applications. Though they are not tied directly to the concept of functional programming, the actor model and software transactional memory are important elements of concurrent programming that enjoy native support in many functional languages. The actor model is just the message passing model, and provides a good way to map distributed logic into composable, decoupled, isolated pieces. Software transactional memory leverages native support of atomic &#8220;create and swap&#8221; operations which conditionally update value references under the condition that the original value matches what is expected. When this doesn&#8217;t happen, harmful concurrent access can be detected and handled (usually by the client just trying again). Check out this [IBM rundown of Java&#8217;s Atomic class](http://www.ibm.com/developerworks/java/library/j-jtp11234/)