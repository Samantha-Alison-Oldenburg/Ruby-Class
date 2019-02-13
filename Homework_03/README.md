# Homework 3: Control Structures and Problem Solving #

So far you have learned how to perform basic calculations and how to evaluate the truthness of basic statements. These `true` and `false` values are useless on their own. But when they are used to make _decisions_ of what to do in your code, they turn Ruby from the world's most complicated calculator to something that can perform complex tasks. The tools to make these decisions are called **control structure**, called so because they are structures in your code that control what step your program will make next.

## The Homework ##

This homework will be a little different. I will be describing function I want you to write. The first two control structures you'll learn about in this lesson will be needed to write this function. The latter ones can make it easier. If you're feeling overwhelmed by the problem, then just focus on the first two control structures, `if` and `while`.

### Fizzbuzz ###
Fizzbuzz is a counting game. To play it, you count aloud upwards from one (e.g. 1, 2, 3, 4, 5, 6....). However, there are a few rules:

If a number is divisible by 3, say "Fizz" instead of the number.

If a number is divisible by 5, say "Buzz" instead of the number.

If a number is divisible by both 3 and 5, say "Fizzbuzz" instead of the number.

Otherwise, just say the number.

Here's a game of fizzbuzz that counts up to 22:

> 1, 2, Fizz, 4, Buzz, Fizz, 7, 8, Fizz, Buzz, 11, Fizz, 13, 14, Fizzbuzz, 16, 17, Fizz, 19, Buzz, Fizz, 22

### The function ###

Your function will play fizzbuzz. It will take a single parameter, which will be the number it counts to. Instead of saying the numbers aloud, your function will use `puts` statement to put each number on one line.

Example:

``` ruby
fizzbuzz(5)

# it should print the following out
1
2
Fizz
4
Buzz
```


## Control Structures ##

### if ###

An `if` block allows you to run a piece of code once if a condition you provide is true. Here's the basic syntax of an `if` statement:

``` ruby
if [condition]
  [code you want to run if condition is true]
end
```

Let's look at a pratical use of an `if` statement, and see it in action.

``` ruby
def print_is_odd(foo)
  if foo.odd?
    puts "It's odd."          # This line will only be reached if foo is odd
  end

  if !foo.odd?                # The ! means not. So if a == false, !a == true
    puts "It's not odd."      # This line will only be reached if foo is not odd
  end
end
```

### while ###

A `while` block is similar to an `if` in that it executes code when a provided condition is true. However, it differs in that it will _continue_ to run the block of code over and over until the condition becomes false. It creates a **loop**. Let's see the syntax and an example

``` ruby
while [condition]
  [code you want to repeat while the condition is true]
end
```

``` ruby
def print_all_numbers_less_than(number)
  i = 1

  while i < number
    puts i

    i = i + 1
  end
end

print_all_numbers_less_than(5)

# This should print
1
2
3
4
```

Loops can be super power and useful, but make sure you provide a way to escape them, or you can be stuck in an infinite loop.

``` ruby
def puts_a_thing(a_thing)
  while true
    puts 5
  end

  puts a_thing     # This line will never get called, because the while loop condition will never become false
                   # You also never get to leave this function if you call it. The console will just keep
                   # printing 5 until you forcibly close the program.
end
```

### Interlude: Nesting control structures ###

It is entirely valid and useful to have a control structure inside the code part of another control block. Sounds complicated, but let's see an example:

``` ruby
def describe_number(number)
  if number.odd?
    puts "It's odd"

    if number > 5
      puts "and it's greater than 5"
    end
  end

  if !number.odd?
    puts "It's not odd"

    if number < 4
      puts "And it's less than 4"
    end
  end
end

```

Call this method once with each number between 1 and 8.

### else and elsif ###

#### else ####

Remember the `print_is_odd` method from above? Let's clean it up a bit using an `else` statement. An `else` statement is an extension to an `if` block. It allows you to run a block of code when the given condition isn't true. Let's see the syntax of an `if-else` statement and then see how it looks for `print_is_odd`:

``` ruby
if [condition]
  [code to run when the condition is true]
else
  [code to run when the condition is false]
end
```

``` ruby
def print_is_odd(foo)
  if foo.odd?
    puts "It's odd."
  else
    puts "It's odd."
  end
end
```

#### elsif ####

Imagine a function that you give a temperature and it (subjectively) tells how cold that is:

``` ruby
def how_could_is(temperature)
  if temperature < 0
    puts "It's so darn cold!"
  end

  if temperature < 32
    puts "It's cold!"
  end

  if temperature < 50
    puts "It's a little chilly..."
  end

  if temperature < 70
    puts "It's a really not chilly..."
  end

  if temperature < 90
    puts "It's not cold at all!"
  end
end
```

This method has a **huge** flaw. Can you see it? Try to figure it out before moving to the next paragraph. Hint: Try calling the method with different numbers.

The answer can be seen if you call the method with `-1`. It will print all five statements. That's no good! There's a quick and dirty way to fix this, putting a `return` at the end of each `if` block.


``` ruby
def how_could_is(temperature)
  if temperature < 0
    puts "It's so darn cold!"
    return
  end

  if temperature < 32
    puts "It's cold!"
    return
  end

  if temperature < 50
    puts "It's a little chilly..."
    return
  end

  if temperature < 70
    puts "It's a really not chilly..."
    return
  end

  if temperature < 90
    puts "It's not cold at all!"
    return
  end
end
```

But this only works if these decisions are the last thing we want to do in this method...

``` ruby
def how_could_is(temperature)
  if temperature < 0
    puts "It's so darn cold!"
    return
  end

  if temperature < 32
    puts "It's cold!"
    return
  end

  if temperature < 50
    puts "It's a little chilly..."
    return
  end

  if temperature < 70
    puts "It's a really not chilly..."
    return
  end

  if temperature < 90
    puts "It's not cold at all!"
    return
  end

  puts 'And that is the weather!'   # This never gets printed for numbers less than 90...
end

```

That's no good...

Wait.

What if we used nested `if-else` statements? It would work... it just doesn't look great.


``` ruby
def how_could_is(temperature)
  if temperature < 0
    puts "It's so darn cold!"
  else
    if temperature < 32
      puts "It's cold!"
    else
      if temperature < 50
        puts "It's a little chilly..."
      else
        if temperature < 70
          puts "It's a really not chilly..."
        else
          if temperature < 90
            puts "It's not cold at all!"
          end
        end
      end
    end
  end

  puts 'And that is the weather!'   # This will get called!
end
```

This code is super hard to understand. It's very wordy, and has a lot of nested blocks you have to keep track of. Try to read the code of this function aloud. You should say a ceratain phrase a lot: "else if". `elsif` is made for these exact situations.

``` ruby
if temperature < 0
  puts "It's so darn cold!"
elsif temperature < 32
  puts "It's cold!"
end
```

Does the exact same thing as.

``` ruby
  if temperature < 0
    puts "It's so darn cold!"
  else
    if temperature < 32
      puts "It's cold!"
    end
  end
```

Let's rewrite `how_cold_is`:

``` ruby
def how_could_is(temperature)
  if temperature < 0
    puts "It's so darn cold!"
  elsif temperature < 32
    puts "It's cold!"
  elsif temperature < 50
    puts "It's a little chilly..."
  elsif temperature < 70
    puts "It's a really not chilly..."
  elsif temperature < 90
    puts "It's not cold at all!"
  end

  puts 'And that is the weather!'
end

```

You can even have an `if-elsif-else` block:

``` ruby
def how_could_is(temperature)
  if temperature < 0
    puts "It's so darn cold!"
  elsif temperature < 32
    puts "It's cold!"
  elsif temperature < 50
    puts "It's a little chilly..."
  elsif temperature < 70
    puts "It's a really not chilly..."
  elsif temperature < 90
    puts "It's not cold at all!"
  else  # This would only get called for temperature >= 90
    puts "It's so darn hot!!!"
  end

  puts 'And that is the weather!'
end

```

***

And that's it! The lesson's done. You have all you need to create a fizzbuzz program. Make it in a file `Homework_03/fizzbuzz.rb`.
