# Homework 02: Useing you're type's good #

## 1. Objects and more about methods ##

### What's an object? ###
In Ruby, almost everything is an object. Objects contain values. Whether that value is a number, a string of characters, or even a method.

Some examples of objects:

  * `5`
  * `"Hello"`
  * `3`
  * `42`
  * `"foo"`
  * `"bar"`

It's safe to say that when you assign a varible, _the thing your are assigning to it is an object._

### But wait, there's more too it ###

Objects have values, but that's not all they have. Objects have **methods**, too.

In the last lesson, we defined methods like this:

``` ruby
def add(a, b)
  return a + b
end
```

And called them like this:

``` ruby
add(5, 4)
```

But check these methods out, fire up your `irb`:

``` ruby
z = "hello"    # just a boring assignment...
z.length       # length is actually a method

-5.abs         # abs (which stands [absolute value](https://www.mathsisfun.com/numbers/absolute-value.html)) is also a method
```

So let's try these methods out!

``` ruby
length           # it doesn't work

abs              # it also doesn't work

"hello".abs      # it doesn't work

5.length         # it doesn't work either
```

The error that pops up is `NameError: undefined local variable or method`. But how can they be undefined, we just used them?

Remember last lesson. If you have a method

``` ruby
def puts_a_thing(some_random_thing)
  puts some_random_thing             # RIGHT HERE
end
```

we know that `some_random_thing` is defined and has a value on the line that says **RIGHT HERE**, but if you were to enter `some_random_thing` into your terminal, it wouldn't be defined. Try it out. Objects work similarly to that.

When we've defined methods so far, we defined it so that it can be used anywhere. But you can also define methods to only exist for certain objects. `length` works for all the word objects, but doesn't for the numbers. To call a method named `bar` on an object named `foo`, you enter `foo.bar`. That's exactly what I did earlier with `5.abs` and `"hello".length` By lesson 4, you'll know how to make these special kind of methods.

Bonus question: What does the `.length` method do for words? Hint, if you can't figure it out, try calling it on different words until you see a pattern.

## 2. Let's do a quick experiment ##

Exit and fire back up your `irb` and make the following variable assignments:

``` ruby
a = 3
b = 5
c = "three"
d = "five"
```

Now, let's try out some of the operators from last lesson.

``` ruby
a + b   # this should be 8
b + a   # this should be 8

c + d   # this should be "threefive"
d + c   # this should be "fivethree"

a - b   # this should be -2
b - a   # this should be 2
```

These all make sense. The variables whose values are words ("five", "three") get combined together, while the variables that store numbers (3, 5) get added in the first pair and subtracted in the last pair of lines above. But what happens if you try mixing words and numbers?


``` ruby
c + a   # what happens?
a + c   # what happens?
```

Both of these result in your terminal printing out a lot of stuff. But the first word is `TypeError`. I'm going to give give you a method that you can call on `a` and `b`, it's one of those special methods that work for number objects.

``` ruby
a.to_s
b.to_s

# .to_s is a method that returns a word version of the number.
# Note the quotation marks around the output.

c + a.to_s

b.to_s + d
```

## 3. Let's talk about types ##

We've talked about how some objects are numbers, and others are words. These are two different `types` of objects. Formally, it can be said the difference between `5` and `"5"` is the **types**. Additionally, `5.to_s` is converting the type of `5` to be the same as `"5"`.

These are the two basic types we've been using so far:

### String ###
A string is a an ordered list of characters (letters, numbers, special symbols, etc.). I've been calling them words until now, but we'll be using the name string for now on. It's more accurate anyway. `"a391j+fa20a!"` is not a word, but it is a string. A rule of thumb for ruby: if the object is between two `"`" or two `'`. it's a string.


### Integer ###
Numbers without fractions or decimals. I will probably use the term integer more than the word `Fixnum`, which is what ruby calls them.


But what about your decimals?

### Floats ###
Numbers with decimals: `1.5`, `0.333333`, etc. "Float" is the standard name for this type in the industry. Sounds weird, but that's just what we call them.

Keep in mind: `5` is a integer, and `5.0` is a float. Even if their values are the same, their _behaviour_ is not.

Here's a demonstration of how integers and floats behave differently with the divsion operator.

``` ruby
4.0 / 3.0       # Behaves just like your calculator

4 / 3           # This is integer division. Also called division
                # with remainder. It removes the decimal from the
                # result.
```

Let's also take this opportunity to show another feature of ruby, automatic type conversion.

``` ruby
4 / 3.0

4.0 / 3
```

In both these cases, you get the same result as `4.0 / 3.0`, even though one of the objects is an integer. How? What happened? Ruby knew that having an integer on one side and a float on the other makes no sense. It also knows you don't change the value of a integer by converting it into a float. So it automatically converts the integer into a float for you.

This is super convenient when working with our next type.

### Boolean ###
There are only two different values in the boolean type: `true` and `false`. You can think of a boolean as an answer to a yes or no question. For example, let's look at another method on the `Fixnum` object type, `odd?`. Odd tells you if a number is odd or not.


``` ruby
5.odd?      # true
4.odd?      # false
1.odd?      # true

y = 10
y.odd?      # false
```

Another place where booleans are used is comparisons. Comparisons are done in ruby using a completely different set of operators.

Given two variables, `foo` and `bar`:

``` ruby
foo == bar     # is foo equal to bar?
foo != bar     # are foo and bar not equal?

foo < bar      # is foo less than bar?
foo > bar      # is foo greater than bar?

foo <= bar     # is foo lees than or equal to bar?
foo >= bar     # is foo greater than or equal to bar?
```

Let's try it in practice

``` ruby
a = 3
b = 5
c = 3

d = "3"
e = "5"
f = "3"
```

I promise there's no homework, so I'm going to make a method that does all the comparisons for you. This method uses a lot of things you haven't learned yet, so don't worry if you don't know how it works. Think of it as a taste of what you'll be able to do.

``` ruby
def compare_three(input_1, input_2, input_3)
  inputs = [input_1, input_2, input_3]

  result_hash = inputs.combination(2).inject({}) do |hash, input_pair|

    # lists in ruby start at 0, not 1
    var_1 = input_pair[0]
    var_2 = input_pair[1]

    display_var_1 = var_1.class == String ? '"' + var_1.to_s + '"' : var_1.to_s
    display_var_2 = var_2.class == String ? '"' + var_2.to_s + '"' : var_2.to_s

    hash.merge!({
      "#{display_var_1} == #{display_var_2}" => var_1 == var_2,
      "#{display_var_1} != #{display_var_2}" => var_1 != var_2,

      "#{display_var_1} < #{display_var_2}" => var_1 < var_2,
      "#{display_var_1} > #{display_var_2}" => var_1 > var_2,

      "#{display_var_1} <= #{display_var_2}" => var_1 <= var_2,
      "#{display_var_1} >= #{display_var_2}" => var_1 >= var_2,
    })
  end

  result_hash.each { |k,v| puts "#{k} is #{v}" }

  return nil
end
```

In ruby, everything can be automatically converted into a `Boolean`. Additionally, _almost_ everything gets converted into `true`. The only things that aren't 'truthy' are `false` and `nil`. We'll learn more about `nil` soon.

And that's it! Your done with one of the hardest lessons well have in this intro!
