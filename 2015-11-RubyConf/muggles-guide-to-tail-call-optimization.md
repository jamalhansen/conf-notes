# A Muggles Guide to Tail-Call Optimization in Ruby
Danny Guinther @dannyguinther
http://blog.tdg5.com
11/16/2015

on the divide between functional and OO langauges

Imagine a world without MINSWAN

From the blog of Guido Van Rossum....

.. here are toxic quotes about Python lack of support TCO

## What is a Tail Call

TC is a call performed as the final action of a proceedure

    def call_in_tail!
        other_method
    end

    def another
        i = 0
        return a_call if i == 0
        i
    end

## Tail Calls are used with Recursion

    def recussive_count(i=5)
        puts i
        return if i == 0
        recursive_count(i -1)
    end

This can replace loops BUT the efficiency of recursion depends on TCO, or you will run out of stack

Tail Call Optimization is Tail Call Elimiation (or close enough)

Ruby does not do TCO by default, and you get stack level too deep error

## TCO to the rescue
Because TCO is the last call of a method, nothing from the calling method is needed anymore

SO you do not necessarily need to come back from the TC

The Call Stack
* keeps track of execution path
* shows where you need to return to

The magic of TCO / TCE is skipping to the end of the call stack and not keeping track.. not by default in MRI

### But wait, why stop here?
Re-use the same stack frame

well it is there since 1.9.2 but not by default.  Not used in production (at least not much so use caution)

enabling it
* re-compile
* rubyvm:instructionSequence
* rubyvm:instructionSequence instance (ie. Arron talk yesterday)
* tco_method gem (uses the instructionsequence above)

Check out Ruby under a Microscope

use "code strings"

something <<-CODE
... some code
CODE

but trying other ways of doing this including ideomatic Ruby blocks

## Benefits
* Ruby is multi-paradigm language
    * funcitonal <--- recursion is one of these tools
    * OO <--- there is a benefit here too by allowing better abstractions
* avoiding stack frames allows faster/earlier GC
* better langauge optimization (Js 6 alows TCO)

## Why not TCO?
* Stack frames not present which makes debugging harder and may break some gems
* set_trace_func needs to be disabled
* can be cumbersome to use
* unknown if it is production ready
* still some "wierdness" around what a TC is (may not optimize)




