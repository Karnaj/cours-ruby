When we hear about Ruby, blocks are often presented as a feature that will make coffee, exercise and eat well, all at the same time. Clearly, this would be a key feature of Ruby. We have of course already used blocks, but in this chapter we will see them in more depth and see the concepts behind it. In fact, we will more generally see the notion of closure (closure in English).


# the notion of closure

Let us remember that we are in a language where everything is an object. Methods are objects, classes are objects, modules are objects, etc. But what about the code? Since we want all the elements of language to be objects, why not make the code itself an object?

In some languages like Smalltalk from which Ruby draws many of its principles, this is the case, and Ruby of course takes up this principle. This then makes it possible to treat the code like any other object (that is to say that we can pass it as an argument to methods, use methods on it, etc.

However, we still have to figure out how an object can be created from a piece of code, and this is what leads us to the notion of closure.

Here we are going to quickly do some theory to understand how closures work. We can read this part on closures a little quickly, it won't be very disturbing for the rest of the learning.

## Closures

To start, let's see what a closure is. So let's take the definition of Wikipedia.

> A closure is a function accompanied by its lexical environment. The lexical environment of a function is the set of non-local variables that it has captured, either by value (i.e. by copying the values of the variables), or by reference (i.e. - say by copying the memory addresses of the variables).

It’s a little obscure. Let's break it down a bit. The important sentence is the first, a closure is a **function** accompanied by its **lexical environment**. Basically, that means it's a piece of code (actually it's not necessarily a function), along with all the environment that there was at the time this piece of code was written (in particular , all the variables that existed when the piece of code was created).
²
The idea behind it is that the bit of code that you capture in the closure may need existing variables to work. For example if we create a closure with a piece of code that displays the value of a variable `x`, this closure needs this variable `x` to "work".

Thus, a closure is in a way a structure containing a piece of code (therefore instructions) and have access to the variables existing when it was created.

[Here, I delete a small passage]

If we go back to Ruby's side, we have already used closures, each time we have used blocks.

```ruby
a = [1, 2, 3]
y = 5
a.each do |x|
  puts x
  puts y
end
```

Here, we have created a closure with the code `puts x` `puts y` and an environment containing the variables `a` and `y`.

## Higher-order functions

In programming languages theory, we say that a function is of higher order if it takes functions as a parameter or returns functions. This is a rather powerful feature which allows for example to have this kind of code in Python.

```python
def filter(ary, filter_function):
    result = []
    for x in ary:
        if filter_function(x):
            result.append(x)
    return result

def method(x):
    return x % 3 == 0  

filter([2, 3, 5, 8, 12], method)
```

We have a function `filter` that takes two parameters (an array and a function `filter_function`) and returns the arrays of the elements such that `filter_function` returns `True`.

More generally, we will say that the functions of a language are of higher order if they can take functions as parameters and return functions. Similarly, we will say that a language entity is first class if it can be passed as a parameter to a method and if it can be returned to a method. For example, numbers, strings or arrays are first class in Ruby.

## What about Ruby?

In fact, in Ruby all objects are first class (you can generally pass any object to a method and return any object). In particular, and this is what will interest us, **closures are first class objects** and can therefore be passed as parameters to methods.

So when we write `5.times { puts 'Hello' }`, we send the closure containing the code `puts 'Hello'` to the` times` method. It is as if we had given it a `hello` function as argument.

Blocks therefore allow us to "simulate" higher order functions. And in Ruby, so we don't need higher order functions and we don't need to be able to pass methods as arguments to other methods. Note, moreover, that we cannot do it. Writing the name of a method allows you to call the method. So we cannot write this.

```ruby
def filter(ary, filter_method)
  result = []
  ary.each { |x| result << x if filter_method(x) }
  result
end

def method(x)
  return x % 3 == 0
end

filter([2, 3, 5, 8, 12], method)
```

Indeed, writing `filter(ary, filter_method)` calls `filter_method` and therefore is equivalent to executing method and calling filter with as argument ary and the result of method (knowing that here the call method will cause an error since it takes an argument ). The closures offer us a solution to this problem.

In addition, they allow you to do what are called **anonymous functions**. These are functions that we will use without giving them a name. We also often speak of **lambda functions**. And that's exactly what we do when we use a block. Let's take the example `5.times {puts 'Hello'}`; it's like we sent the function whose body is `puts 'Hello'` to `times`, but without give it a name.

[Here, I delete a small passage]

With this chapter, we will learn how to use closures to do the same in Ruby. We will then know how to write the `filter` method in Ruby so that we can call it that.

```ruby
filter([2, 3, 5, 8, 12]) { |x| x % 3 == 0 }
```

---

So much for the long introduction. Now is the time to get to the heart of the matter and see how to handle these closures. It should be noted that Ruby has different ways of managing closings. They differ in a few points, but are not very complicated to understand.


# Blocks

## Use a block in a method

We are not going to review how to give a block as an argument to a function, what we want to see is how to use this block in the function. To illustrate this, we will start with a simple example; our goal is to write a method `day` that performs daytime actions. As each day is potentially different, it will take as a parameter a block with the action of the day.

To start, let's write a `day_description` method that displays the day's actions. We will therefore pass it as parameter a string corresponding to the action to be performed.

```ruby
def day_description(action_description)
  puts "Se lever"
  puts action_description
  puts "Dormir"
end

day_desctiption('Travailler')
day_description('Regarder la télévision')
```

Here it’s fine. Now let's write the method `day` which does not display the description of the actions, but does them. In particular, it will also have to do the action passed as parameter to the function, so we will use a block. To use a block passed as parameter to a method, just use the keyword `yield`. There is nothing else to do.

```ruby
def day
  wake_up
  yield
  spend_the_night
end

day { work }
day { watch_tv }
```

To test our previous code, we will create `wake_up`, `work` methods which... Display the activity (yes, we said we were going to do the activity, but hey...).

```ruby
def wake_up
  puts 'Baillement...'
end

def spend_the_night
  puts 'Ron... Pi...'
end

def work
  puts 'Le pouvoir de la procrastination'
end

def watch_tv
  puts 'Ron... Pi...'
end
```

In fact, **all the methods take a block as parameter**, it is implicit. It's just that they don't all use it.

```ruby
puts('Hello') { puts 22 }
```

Here, the message is displayed and the block is ignored.

We can call the block multiple times if we want. For example, let's modify `day` to do the activity twice a day with a small lunch break in between.

```ruby
def day
  wake_up
  yield
  lunch_break
  yield
  spend_the_night
end
```

### Know if a block is passed as a parameter

It may sometimes be necessary to know if a block has been passed as a parameter. To do this, we use `block_given?` which returns `true` if a block was passed as a parameter. It is good practice to use `block_given`. Indeed, the use of `yield` without block passed in parameter creates a "LocalJumpError (no block given (yield))" error. We therefore correct our code as follows.

```ruby
def day
  wake_up
  block_given? ? yield : procrastinate 
  lunch_break
  block_given? ? yield : procrastinate
  spend_the_night
end
```

Here, if a block is given, it is executed, otherwise the `procrastinate` method is called.


## Blocks with parameters

We have already used blocks with parameters several times. To execute a block passing it as a parameter, just use `yield` by giving it this parameter. For example, let's add an argument `name` to our method `day`, the block will take this name as a parameter.

```ruby
def wake_up(name)
  puts "#{name} wake up."
end

def work(name)
  puts "#{name} fait semblant de travailler."
end

# etc.

def day(name)
  wake_up(name)
  block_given? ? yield(name) : procrastinate(name) 
  lunch_break(name)
  block_given? ? yield(name) : procrastinate(name)
  spend_the_night(name)
end

day('Nom') { |name| work(name) }
```

And we have the desired result. That's it, we know how to use blocks!

Blocks do not check the number of arguments passed to them. If there is too much, the excess is ignored, and if there is not enough, the arguments not supplied will be `nil`.

```ruby
day('Nom') { work('Lui') }
day('Nom') { |name, n| n.times { work(name) } } 
```

Here, with the first call, the block will be called with the argument `name` in the `day` function, but since the block takes no arguments, it will be ignored. The second call will cause an error because `n` will be `nil` (and `nil` object has no `times` method). To overcome this, we could give a default value to `n` and even to `name`.

```ruby
day('Nom') { |name, n=1| n.times { work(name) } }
```

And we have the result.

## Explicit call

With what we have written, we cannot, seeing the prototype of a function (its name and its arguments), know that it expects a block as a parameter. We can explicitly request a block as an argument. For this, we use the following syntax.

```ruby
def day(name, &block)
  wake_up(name)
  block_given? ? yield(name) : procrastinate(name) 
  lunch_break(name)
  block_given? ? yield(name) : procrastinate(name)
  spend_the_night(name)
end
```

The ampersand in front of the parameter name indicates that it is a block. This parameter can only appear last, and of course, there is only one (you can only pass a single block as an argument to a function).

Note that this parameter does not force the call of the function with a block; the block is always optional. It just lets us know that the function is surely waiting for a block. In addition, it allows us to call the block other than using `yield`, using the `call` method of the variable `block`.

```ruby
def day(name, &block)
  wake_up(name)
  block_given? ? yield(name) : procrastinate(name) 
  lunch_break(name)
  block_given? ? block.call(name) : procrastinate(name)
  spend_the_night(name)
end
```

## Some subtleties

Now that we know how to use blocks, let's review some subtleties related to their use.

To start, remember that a closure is a piece of code and its environment (local variables, etc.). Knowing this, that produces the following code.

```ruby
def f(&block)
  x = 10
  block.call
end

x = 2
f { puts x }
```

If we have followed everything that has been said, the block was created with its environment and therefore with the variable `x` which is equal to 2, and it is this value which is displayed.

In fact, it’s even stronger; a block is supposed to contain what is necessary for its execution (note nevertheless that it does not have the variables that are passed to it as a parameter). Thus, the environment in which the block is evaluated is not even taken into account during its evaluation, only the environment captured during its creation exists at this time. The following code therefore does not work. The variable `x` does not exist in the block environment.

```ruby
def f(&block)
  x = 10
  block.call
end

f { puts x }
```

However, we can have the variable x as a block parameter.

```ruby
def f(&block)
  x = 10
  block.call(x)
end

f { |x| puts x }
```


# Proc and lambda

## Reuse blocks ?

One of the reasons we want closings is to be able to pass them as arguments to a function. However, the blocks have a small problem: we cannot retrieve them in variables (for example to reuse them during other calls. Let's say that we have for example a `map` function which takes an array as parameter and applies to each of its elements a function, and another function, `filter` (which we have already mentioned), which keeps the elements which respect a certain condition.

```ruby
def map(ary, &block)
  new_ary = []
  ary.each { |x| new_ary << block.call(x) }
end

def filter(ary, &block)
  new_ary = []
  ary.each { |x| new_ary << x if block.call(x) }
end

a = [1, 2, 3, 4]
map(a) { |x| x.even? }    # => [false, true, false, true]
filter(a) { |x| x.even? } # => [2, 4]
```

Here, we would like to keep the block in a variable and reuse it, but this is not possible. With the following code, we get an error.

```ruby
block = { |x| x.even? } 
```

Someone clever might think of doing a function that explicitly takes a block as a parameter, and returns it.

```ruby
def create_block(&block)
  block
end
```

By running this code in a REPL, and calling this method with a block, we find that it returns an object of the class `Proc`. The class of `block` would therefore be `Proc`. Let's check that out.

```ruby
def block_class(&block)
  block.class
end
```

And by running `block_class {}`, we get `Proc`.

## Procs


A mysterious class `Proc` appears in the middle of our blocks. But what is it? In fact, we cannot reuse a block, and we can almost say that they are not real objects. They only exist for the time of the method. The `Proc` can be linked to variables and are reusable. To define a `Proc`, we give a block as parameter to `Proc.new` or to `proc`.

As for its use… We already used a `Proc` when we used the explicit syntax of blocks. The variable `block` we were using was a `Proc`. We can then write this code.

```ruby
def map(ary, proc)
  new_ary = []
  ary.each { |x| new_ary << proc.call(x) }
end

def filter(ary, proc)
  new_ary = []
  ary.each { |x| new_ary << x if proc.call(x) }
end

a = [1, 2, 3, 4]
proc_method = proc { |x| x.even? }
map(a, proc_method)   # => [false, true, false, true]
filter(a, proc_mehod) # => [2, 4] 
```

There is no ampersand here for the argument `proc` of the methods `map` and `filter`. They are not a block, it is a normal argument of the method. This means in particular that it is still possible to pass a block to the function.

Note that it is possible to create a `Proc` from a method or a symbol using the `to_proc` method. With `:str.to_proc` we create the following Proc.

```ruby
Proc.new { |x, arguments| str.(arguments) }
```

Then we can write this code which calls the method `even?` of `2`.

```ruby
def execute(f, args)
  f.call(args)
end

execute(:even?.to_proc, 2)
```

So, the class `Proc` allows us to get higher order functions.

### From block to `Proc`

Let's come back to the block-`Proc` relationship.

What happens when we write `def f(args, &block)`? Why do we start from a block, and finally get a `Proc`?

The block is simply converted to `Proc`. The ampersand in front of `block` tells Ruby that we want to store the block into a variable, and so it converts it to `Proc` (blocks cannot be stored in a variable).

The `&` operator also allows you to do the reverse conversion and go from `Proc` to block. This is useful if we want to use a `Proc` with a method that takes a block as a parameter.

```ruby
fun = proc { |x| print "#{x + 1} "}
5.times(&fun) # => 1 2 3 4 5
```

Note also that with an object that is neither a `Proc` nor a block, `&` attempts to call the object's `to_proc` method and then transform the corresponding `Proc` into a block. This allows us to use this rather concise syntax.

```ruby
ary = [2, 1, 32, 6]
map(ary, &:to_s) # => ["2", "1", "32", "6"]
```

In this example, the block `{ |x| x.to_s}` is passed to the method; the `to_s` method is called for each element of the array.

## Lambdas

Another way to create a closure from a block is to create a lambda. It is created from two syntaxes.

```ruby
fun1 = lambda { |x| x + 1 }
fun2 = -> (x) { x + 1}
```

The first syntax uses the keyword `lamda` followed by the block to transform into lambda. The second follows the form `-> (arg1, arg2) block`. The use is then the same as that of `Proc`. These objects on which we can call `call` are called callable (we can call them).


```ruby
fun2 = -> (x) { x + 1}
puts fun2.call(4)
```

We prefer to use the second syntax with single-line blocks, and the `lambda` keyword with multi-line blocks.

### What are the differences between `Proc` and lambda?

The question arises indeed. Why have these two objects when they behave the same way?

To start, looking at the class of a lambda, we see that it is an object of class `Proc`. In fact, if we look at the value of a lambda and compare it to that of a `Proc`, we find that a lambda is an object of class `Proc` but with information indicating that it is a lambda.

```ruby
ld = -> (x, y) { x + 2 * y }
pr = Proc.new { |x, y| x + 2 * y }
puts ld  # => #<Proc:value (lambda)>
puts pr  # => #<Proc:value>
```

But that does not answer our question about their differences. In fact, there are two major differences between the `Proc` and the lambdas.

#### Check number of arguments

The first difference is that the lambdas check that the number of arguments passed is correct while the `Proc` sets the parameters not passed to` nil`.

```ruby
ld = -> (x) { puts x }
pr = Proc.new { |x| puts x}

pr.call
ld.call # ArgumentError (wrong number of arguments)
```

#### The behavior of `return`

When a `return` is crossed in a lambda, it interrupts the execution of the function which called it, this is not the case for` Proc`.

```ruby
def f
  ld = -> { return 10 }
  ld.call
  puts "Ici"
  return 0
end 

f # => 0

def g
  pr = Proc.new { return 10 }
  pr.call
  puts "Ici"
  return 0
end

g # => 10
```

Here, when calling `f`, the display is done and the method returns `0`, when calling `g`, this is not the case.

In fact, it's even worse, a `return` in a `Proc` is linked to the place of its creation. Said like that it's a bit obscure, but an example will help to understand.


```ruby
def f(pr)
  pr.call
  return 0
end

pr = Proc.new { return 10 }
f(pr)
```


Here, we get a `LocalJumpError (unexpected return)` error because the `return` is not linked to the `f` function since the `Proc` was created outside.

Likewise in the following code, since the `Proc` was created in the `f` method: Ruby believes that the `return` corresponds to a `return` of `f`, but we are no longer in `f`.

```ruby
def f
  Proc.new { return 10 }
end

pr = f
pr.call
```

Finally, lambdas can be seen as real first-order functions in the sense that a `return` will act as in a method and that the number of parameters is checked.

The cases where we will really need to make this distinction are rather rare; in fact these are the blocks that we will use most frequently. In the rare cases where we will have to choose between `Proc` and lambda, it will usually be enough for us to tell ourselves that lambdas act like real methods.

## Curryfication

Now that we know how to "return methods," we can look at a transformation called [currying](https://en.wikipedia.org/wiki/Currying). The idea is as follows: if we have a method, (say `add(x, y)` which adds `x` and` y`), why not return a new method if we only give one argument to `add`?

`add(2)` would be a method that would take 1 argument `y` and return `2 + y`,` add(10) `would be a method that would take 1 argument `y` and return` 10 + y`, etc. Thus, we fix the first argument and return a method to which we must give the other arguments.

This operation is done with the `curry` method available for `Proc` as for lambdas. It returns a `Proc` or a curryfied lambda and we can then give it the arguments as we want: if we give it fewer arguments than necessary, it will send us a new `Proc` (or a new curryfied lambda).

```ruby
pr = proc { |x, y, z| x + y + z }
pr_curry = pr.curry
add2 = pr_curry.call(2)
puts pr.curry.call(1, 2, 3) # => 6
puts pr.curry.call(1).call(2).call(3)
puts add2.call(1, 2)        # => 4
puts add2.call(1).call(2)   # Ligne précédente curryfiée.
```

With a curried object, we can give fewer arguments than necessary and we will have no errors. However, if we give more, it is the classic behavior that is observed: no problems in the case of a `Proc` where the excess arguments are ignored, the error `ArgumentError` in the case of a lambda.

We will not really use currying, but we present it more as a curiosity and for culture. The more curious can go and see how it is used in certain languages like OCaml and who knows, this notion may be useful late...

# Exercises

The closings are ultimately very useful and we could already see this by seeing the usefulness of the blocks. In this chapter, we will resume an old habit and make some methods to train us to use the closures instead of a little project.

## Exercise 1

To start, write a function `min(a, b, & block)` which returns the minimum of `a` and `b` according to the block passed in parameter. For example, `min(-2, 1, &:abs)` must return `1`, the `abs` method allowing to obtain the absolute value of a number (`-2.abs` is `2` and `1.abs` is `1`).

Correction

The idea is of course to compare the values returned by the call to the block rather than the values `a` and `b` passed in parameter. Here, we decide to compare the two values if no block is given.

```ruby
def min(a, b, &block)
 return (block.call(a) < block.call(b) ? a : b) if block_given?
 (a < b) ? a : b
end
```

## Exercise 2

Let's continue with a simple exercise. Write a method which takes as parameter two methods `f` and` g` and returns the method `h` which is the sum of these two methods (*ie.* `h(x) = f(x) + g(x)`).

Correction.

Here, we are not going to use blocks, but directly ask for `Procs` or lambdas (in any case * callable * objects) as parameters. It seems more logical to do so (our method basically takes two methods in the form of closure and returns a third method in the form of closure).

```ruby
def sum(f, g)
  -> (arg) { f.call(arg) + g.call(arg) }
end
```

We return a lambda, considering that we must give the right number of arguments to the closure that we return and that if in the closure returned we do a `return`, we want the same behavior as in a normal method.

## Exercise 3

Still in the vein of the second exercise, this time we will write a method that compos two methods. Recall that the composition of two methods `f` and` g` is the method `h` such that `h(x)` is equal to `f((x))`.

Correction.

The idea is the same as for exercise 2, our function will have to call `f` with as argument the value returned by the call of `g` on the initial argument.

```ruby
def composition(f, g)
  -> (arg) { f.call(g.call(arg)) }
end
```

Note the existence of composition operators, `>>` and `<<` since version 2.6 of Ruby. With `p1 >> p2` we obtain the `Proc` which does `p1(p2(args))` and with `p1 << p2` the one which does `p2(p1(args)) `(these are lambdas if `p1` is). So, we could have written `(f << g).call (arg)` for this exercise.

## Exercise 4

We will take the third exercise, and make it a little more complex. This time, we want a method that takes as a parameter a list of functions `[f0, f1, ...]` and returns the composition function `f0(f(...))`. By convention, we assume that if the list is empty, the function to return does nothing and returns the argument (this is the identity function).

Correction

This exercise is a good example of using recursion. Here, either the list is empty (we test it with `fun_list.empty?`), or it is not the case, in which case we must do this.

1. Calculate the result `r` of calling the composition of the functions except the first with the argument `arg`.
2. Appeler la première fonction avec l'argument `r`.

Indeed, if we calculate `r = f1(f2(...))`, then we just want to return `f0(r)`. And to calculate `f1(f2(...)))`, we will do the same thing and calculate `f2(f3 (...))`, and so on until falling on `fn(arg)` which will be evaluated in `fn.call(composition([]).call(arg))`, and `compositio([])` is the identity, so we will have `fn.call(arg)`, and we can then go back to get the final result. For further and explicit explanations, we can [find out about recursion](https://zestedesavoir.com/tutoriels/248/la-recursivite/).

```ruby
def composition(fun_list)
  return -> (arg) { arg } if fun_list.empty?
  -> (arg) { fun_list[0].call(composition(fun_list[1..-1]).call(arg)) }
end
```

We can also use the `reduce` method. Indeed, we create a lambda which takes as parameter a variable `x`. This variable is the starting value of the accumulator. Then we scroll through the list of functions and for each function `f`, the accumulator becomes `f(acc)`.

If we do things like that, then with `[f0, f1, ...]`, the accumulator will be `x`, then `f0(x)`, then `f1(f0(x))`, etc. But what we want is `f0(f1(...(x))`. So we have to work with the reversed list.

```ruby
def composition(fun_list)
  lambda do |x|
    fun_list.reverse_each.reduce(x) { |acc, f| f.call(acc) }
  end
end
```

Of course, we can also add up a list of functions for example.

# Conclusion

In this chapter, we demystified the blocks, and added to our panoply of the Rubyist the `Proc` and the lambdas.

- A closure is an object constructed with a piece of code and its environment.
- The closures allow to simulate higher order functions, that is to say that they can be passed as parameters to methods.
- The unary operator `&` allows to pass from `Proc` to block and vice versa.
- The unary operator `&` also allows you to create a block from a method (with `&:method_name`).
