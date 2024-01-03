---
title: Generators
date: 2024-01-02 00:00:00 +0800
categories: [Python]
tags: [Python, programming]
---

## What is a generator?
Simply, a function with `yield` instead of `return` statement.

#### Side Notes
* Does not return all the values at once. It returns an `iterator` instead.
  * Memory efficient.
* Saves the state of the "function" by saving local variables.
* Good for retrieving small batches of data in infinite data.

## Basic Examples
To turn a function into a generator, use `yield`.
```python
def print_number_up_to(n):
  for i in range(n):
    yield i
```
Here, we have a generator that simply prints out all the numbers that are smaller than the input. 

Since generator returns an iterable object, we can access the values through iterating the object:

```python
for i in print_number_up_to(5):
  print(i)
```

Returns the following.
```python
>> 0
>> 1
>> 2
>> 3
>> 4
```

#### Accesing values using `next()`
Taking the same example, values can be printed using `next()`.

```python
gen = print_number_up_to(3)
print(next(gen))
>> 0

print(next(gen))
>> 1
```

Because a generator saves the state of local variables, it can resume where it was last left off.

```python
print(next(gen))
>> 2
```

At this point, if we try to print the next value, it will throw an `StopIteration` error.
```python
print(next(gen))

>> Traceback (most recent call last):
>>   File "/home/runner/ImperturbableSaltyDowngrade/main.py", line 13, in >> <module>
>>     print(next(gen))
>> StopIteration
```

## Generator expression
A generator can be created in a single line, using the generator expression.
```
generator = ( expression )
```

Here's an example of the above code.
```python
# def print_number_up_to(n):
#   for i in range(n):
#     yield i

# Same as print_number_up_to()
n = 3
generator = ( i for i in range(n) )
```
Now, we can print out the values the same way.
```python
# Use for-loop to print values
for i in generator :
    print(i)

>> 0
>> 1
>> 2
```

```python
# Use next() to print values
print(next(gen))
>> 0

print(next(gen))
>> 1
$$
print(next(gen))
>> 2
```
