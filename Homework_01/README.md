# Homework 01: Fun with Ruby #


## What is Ruby? ##

Ruby is a relatively new programming language. It's only about a decade or two old. It features a lot of features that make it super friendly to new programmers, but one that can be also unfriendly: ruby is an interpreted language (it is read and interpreted one line at a time). In comparison compiled languages, like C++, read all the lines first to make sure that the program will run. What this means is:

**Ruby doesn't tell you that you have typos. Consistent spelling is super important**

## 1. Getting Ruby ##

```
sudo apt-get install ruby
```

Now let's fire 'er up!

```
irb
```

## 2. Ruby Introduction: Hello World ##

Type: `puts "Hello World!"

You should see the terminal say (or print as we nerds call it) "Hello World!". Printing is an important function in almost all programming languages, and it's good to know that `puts` it the print function for ruby.

Variables are places that store information. Variables need to be given a name so you can find that location. Think of them like mailboxes that can fit one thing inside of them at a time. They have little addresses so you know which one to open.

The process of giving a variable a value is called _assignment_. In ruby, assignment is super simple. Try it out!

``` ruby

# Lines with the '#' in front of them don't get interpreted
# name_of_the_varible = the_value

a = 4

# to view a variable's value, just type in the variable name
a

b = 7

# you can reassign variables in ruby
a = 8


# you can assign the value of one variable to another
c = b

```

## 3. Operators ##

Operators are fancy characters that do operations on values or variables. The most common operators are the arithmetic ones (+, -, *, /, etc.). Try them out!

``` ruby
7 + 5

a = 4 * 1.5

c = a + 11

d = c * a

e = d / 3

# you can chain multiple operators
f = e + c + a - d

```

## 4. Methods ##

Methods, also known as subroutines or functions, are containers of code. They usually have variables you give as input (called parameters), and almost always have an output. In ruby, the last line of a method definition (the code inside the method) is the output. Copy paste these three lines in terminal.

``` ruby
def puts_a_thing(the_thing)
  puts the_thing

  the_thing
end
```

Let's break that down

`def`: I'm making a method definition
`puts_a_thing`: This is the name of the method. Use that name to call it
`(the_thing)`: The list of parameters. There's just one in this case.
`end`: I'm ending the method defintion
`The lines in the middle`: The method body, where you do the actual work. It can use those parameters like they are variables (which they are).

Now try: `puts_a_thing("Hello World!")`

You just called the method with the

You can also omit the parenthesis in Ruby (this is very rare for programming languages however): `puts_a_thing "Hello World!"`

Remember how the last line in a method is the output? Well we're going to see that in action. An important tool is being able to assign the output of methods to variables.

``` ruby
output = puts_a_thing("Hello World!")
```

Check the value of `output`

Let's try a method with two parameters. Notice the comma separating the two items in the method list:

``` ruby
def puts_two_things(thing_1, thing_2)
  puts thing_1
  puts thing_2
end
```


## 5. Assignment ##
In the file `~/Workspace/ruby-class/Homework_01/assignment.rb`:
1. Write a method that adds two number.
2. Write one that subtracts one number from the second one (note, the order of the parameters is important).
3. Write one that adds three numbers
4. Write one that adds the first two parameters, and subtracts the third one from it.
