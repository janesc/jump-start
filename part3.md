# Lesson Plan

### Scope
* Functions and blocks each introduce new scopes
* A scope is basically an environment where variables are accessible (think inside a function vs outside of it)
* A **local variable** is only defined within its scope
* You should generally not name a local variable the same as the function or as another variable in scope, because it causes a namespace conflict. (I.e., the older variable will no longer be accessible.)

Exercise:

* Will this function work? Don't run it, just analyze the code mentally.

```ruby
i = 0
def iterate!
  while i < 5
    puts i
    i += 1
  end
end

iterate!
```

* What about this one?

```ruby
arr = [1, 2, 3, 4]
sum = 0
arr.each do |el|
  sum += el
end
puts sum
```

* And this one?

```ruby
arr = [1, 2, 3, 4]
def array_product(arr)
  arr.each do |el|
    el *= el
  end
  puts el
end

array_product(arr)
```

### Pass-by-reference
* When you pass a variable into a function or a method, the original variable always continues to refer to the same object.
* A variable is just a **pointer**. Think of it as just writing down the address of a building into an address book.
* Re-assigning the same variable within another scope doesn't mutate the original object, it just changes that scope's address book.
* Writing stuff into your address book doesn't actually change where buildings live! It's just your own form of book-keeping.
* More concretely, all Ruby objects live in memory. And they'll still live in memory unless you explicitly mutate them.

### Mutation

* Safe vs. unsafe methods. The bang, `!`, at the end of the method name denotes an unsafe method.
* The bang generally means the method mutates the input.
* Pay attention to whether you need to re-assign your variable, or mutate it in your function.
* Some Ruby objects are **immutable**, which means they cannot mutate. You must create a new and different object and re-assign your variable if you want to change an immutable object.
* Things that are immutable:
  * Booleans (`true`/`false`)
  * `nil`
  * Numbers
* Arrays and hashes are **mutable**. `[1,2,3,[4,5,6],7]` is an array with some immutable elements, and one mutable element. This could make a difference if you are iterating over elements of an array and changing them as you go.
* Here's a rule of thumb for mutability—if you can pass it into a function and change the object, then it's mutable. Otherwise it's not.
* Think about it: can you imagine something immutable, like `true` or `0` changing because you called some function?
    ```ruby
  var = false
  crazy_function_that_does_crazy_things!(var)
  puts var == false # no function can change its value!
    ```

Exercises:
* What will this code do?

```ruby
arr = [1,2,3,4]

def destroy_array!(arr)
  arr = []
end

puts destroy_array!(arr)
puts arr
```

* And this code?

```ruby
arr = [1,2,3,4]

def double_arr(original_arr)
  doubled_arr = original_arr
  (0...original_arr.length).each do |i|
    doubled_arr << original_arr[i]
  end
  doubled_arr
end

puts double_arr(arr)
puts arr
```

* What about this?

```ruby
def add_all_up_to_n(n)
  (0..n).each do |val|
    n += val
  end
  n
end

n = 5
puts add_all_up_to_n(n)
puts n

```

Coming up soon:
## Nested iteration
## More enumerables
## More string methods
## More array methods
## Parallel assignment
### Coding problems!
