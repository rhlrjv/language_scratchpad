Ruby Learnings
==============

Array Injection
---------------
A simple way to do aggregation style processes on an array

### example code:
```ruby
a = [1,2,3,4,5]

print "item\tprior result\n"

sum = a.inject(0) do |result, item|
  print item, "\t", result, "\n"
  result+Float(item)/2
end

print "sum: ", sum, "\n"
```
result:
```sh
$ ruby inject.rb
item    prior result
1       0
2       1.0
3       3.0
4       6.0
5       10.0

sum: 15.0
```
### gotcha:
If the initial result is not passed in, the inject opperator just uses the first item in the list as the result and starts the iteration from the second item. This may lead to a different result than expected.

```ruby
sum = a.inject do |result, item|
  print item, "\t", result, "\n"
  result+Float(item)/2
end
```
result:
```sh
$ ruby inject.rb
item    prior result
2       1
3       2.0
4       3.5
5       5.5

sum: 8.0
```