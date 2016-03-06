# Extremely Defensive Coding
Sam Phippen  @samphippen
11/16/2015
Member of the Rspec core team
works for Fun & Plausible Solutions

## Start with a story
The story is from Q&A session from a deep internal archetecture talk of his.

He was asked: when is it OK to overide methods on object?

_Ummmm, sort of, like..._

This is a difficult question and it is hard to give a good explicit answer it.

Eventually came up with an answer that has to do with consistancy, and that is. Override methods of an object when it when it makes your code more consistant with other Ruby code.

For example the  == on a data object.  The default implementation will compare the instance, when it is prefered to compare the data.

Now for something completely different...

## What makes a gem good?

* Internals? _Not really_
* Interface? _Yes_
* Convenience
    * Is it more convenient than doing yourself
    * Will it stay convenient over time?
* It should be understandable by everyone on the team
* It should with a wide range of Ruby codebases

## RSpec
How does it stand up to this criteria?
* Not always convenient

### User Story
When I stub an object, I want the original implemention returned after the example so that my objects are not broken.

Take a look at the implementation to see how this works.

    allow(cat).to
    receive(:meow)

This will stub meow on cat and we will also want to remove cat.meow() and store it elsewhere so that we can return it back later (after the test).

How do you save a method and move it around in Ruby?

#### The method() method!
* takes a symbol and returns a method *

The method method allows us to treat a method as a symbol (object) that you can pass it around.

This allows you to complete the user story

But, it was not this simple.

## Defensive Coding
    RSpec::Support
      .method_handle_for

This is a simple wrapper around the method() method and it began simply as:

    def self.method_handle_for(object, method_name)
        method(object, method_name)
    end

But hold on! Simply calling method() is not good enough in some instances

### Problem: Users Lie
    def method
        'get'
    end

Above exists in http handler library
This blows away the method() method!

So, to solve this, they stored the method() method in a constant using an instance method method which will always give the correct method method in Kernel. This will give the original implementation of the method method regardless.

This original implementation of the method method can be used in .method_handle_for

### Ruby implementations lie
Some objects do not have Kernel in the inheretance chain
* basic objects
* objects with dup of Kernel

These objects will not have a method method.

"We really really try to support all versions of Ruby"

But the above broke jruby support

Point is: Ruby interpreters behave differently and RSpec tries to support them all (problems with Rubinius)

### Sometimes users do not lie

_Gave an example where you cannot be sure of the best way to do it_

So you trust but verify

When you do, you end up with a really big chunk of code

Point:  Rspec strives to do something reasonable no matter what you throw at it.
.. Also please file bugs

## Take-aways

* Your gem should be defensive
* Code will be run on non-mri interpreters
* Ruby users are wierd

What makes a Gem good?
* Internals?  this explanation made no sense so no
* Interface? Yes it handles lots of edge cases and multiple platforms

Gems - provide a strong abstraction boundary between what you do and the gem implementation.  Hides huge complexity behind a barrier

Write defensively, and your users will not look in the box


