# Homework 04: Arrays and Hashes #

Arrays and hashes are two ways to define a group of values. Both can be assigned to a single variable just like the values `5` and `'hello'` can.


## Arrays ##

And array is an _ordered_ group of values. Think of it like a numbered list of objects, with the first item being item _0_. Arrays are written in ruby as a comma-separated list of objects enclosed in a pair of square brackets, `[]`.

``` ruby
one_to_ten = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

To access a specific value in an array, you need its _index_, essentially its place on the numbered list. **Remember:** the array's indices starts at _0_, not _1_.

Here's another array along with a table showing the index of each value.

``` ruby
array_of_strings = ['this', 'is', 'an', 'array', 'of', 'strings']
```

| index | value |
|-------|-------|
|   0   |`'this'`|
|   1   |`'is'`|
|   2   |`'an'`|
|   3   |`'array'`|
|   4   |`'of'`|
|   5   |`'strings'`|


Here's how you access the _nth_ member of the array: `array[n]`

``` ruby
array_of_strings[0]  # returns 'this'
array_of_strings[1]  # returns 'is'
```

Keep in mind, that since the index starts at _0_, the index of the last member of an array is _one less_ than the length (the amount of items in the array) of the array.

### Homework Part 1 ###

Write a function that takes a single argument, an array, and prints out each member of the array on a single line. Use a `while` loop. Hint: you can get the length of an `array` using the object method `.count` (`array.count`).
