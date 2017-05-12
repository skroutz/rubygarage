---
layout: slide
title:  Ruby basics
---

![](/rubygarage/assets/images/ruby.png)

# Ruby is...

> A dynamic, open source programming language with a focus on simplicity and productivity.
> It has an elegant syntax that is natural to read and easy to write.

---

# You can run Ruby...

--

## ...from source files

hello_world.rb <!-- .element: class="filename" -->

```ruby
puts 'Hello Ruby world!'
```

```sh
$ ruby hello_world.rb
Hello Ruby world!
```

hello_world.rb <!-- .element: class="filename" -->

```ruby
#!/usr/bin/ruby
puts 'Hello Ruby world!'
```

```sh
$ ./hello_world.rb
Hello Ruby world!
```

--

## ...inside a REPL
<div style="text-align: right; margin-right:15%">
(a.k.a Read-Eval-Print-Loop)
</div>


```ruby
$ irb
puts 'Hello Ruby world!'
# Hello Ruby world!
# => nil
```

---

# Objects

--

## In Ruby, everything is an object.
(and has methods that you can call)

```ruby
1.class # you can call methods without ()
# => Fixnum

false.class
# => FalseClass

'alice'.capitalize
# => "Alice"

5.next
# => 6

[5, 12, 4].sort
# => [4, 5, 12]

```

--

## Even classes are objects

```ruby
Fixnum.class
# => Class

1.instance_of?(Fixnum)
# => true

>> Fixnum.is_a?(Object)
# => true

Fixnum.methods
# => [:class, :to_s, :superclass, :name, :is_a? ...

1.methods
# => [:to_s, :+, :-, :*, :abs, :zero?, :next ...

1.next
# => 2

1.methods.include?(:methods)
# => true

```
What class is `Fixnum` an instance of?

---

# Numbers

--

## Numbers

```ruby
100.class
# => Fixnum

10000000000000000000.class
# => Bignum

100.0.class
# => Float
```

--

## Numbers conversion

```ruby
1 + 2 # => 3

1 + 2.0 # => 3.0

1.0 + 2 # => 3.0

1 / 2 # => 0

1.0 / 2 # => 0.5

1 / 2.0 # => 0.5

# You can use operators as methods *
1.+(1) # => 2
```

--

## Arithmetic operators

```ruby
a = 10
b = 20

a + b  # => 30
a - b  # => -10
a * b  # => 200
b / a  # => 2
a / b  # => 0
a % b  # => 10
a ** b # => 100000000000000000000

```

--

## Assignment Operators

| Operator | Description                                  |
|----------|----------------------------------------------|
| +=       | c += a is equivalent to c = c + a            |
| -=       | c -= a is equivalent to c = c - a            |
| \*=      | c \*= a is equivalent to c = c \* a          |
| /=       | c /= a is equivalent to c = c / a            |
| %=       | c %= a is equivalent to c = c % a            |
| \*\*=    | c \*\*= a is equivalent to c = c \*\* a      |

---

# Strings

--

## Create string

```ruby
'New string'
# => New string

"New string"
# => New string

String.new
# => ""
```

--

## Interpolation

```ruby
"Seconds/day: #{24 * 60 * 60}"
# => Seconds/day: 86400

'Seconds/day: #{24 * 60 * 60}'
# => Seconds/day: #{24 * 60 * 60}

#      ↓ any code can go here
"Trol#{'Lo' * 3} !!!1"
# => TroLoLoLo !!!1

```

--

## Concatenation

```ruby
'Con' "cat" 'ena' "te"
# => "Concatenate"

'Con' + "cat" + 'ena' + "te"
# => "Concatenate"

str = 'Programming!'
# => "Programming!"

str << ', I love it!'
# => "Programming! I love it!"

str.concat(' What about you?')
# => "Programming! I love it! What about you?"
```

--

## Accessing

```ruby
str = 'Programming! I love it! What about you?'
# => "Programming! I love it! What about you?"

str[13]
# => "I"

str.slice(13)
# => "I"

str[13, 10]
# => "I love it!"

str.slice(13, 12)
# => "I love it!"

str[13..-17]
# => "I love it!"

```

--

## Useful methods

Look in [the docs](http://ruby-doc.org/core-2.4.1/String.html) for more
information

```ruby
'pROgraMMing'.capitalize
# => "Programming"

'Programming'.downcase
# => "programming"

'Programming'.chars
# => ["P", "r", "o", "g", "r", "a", "m", "m", "i", "n", "g"]

'Programming'.index('gra')
# => 3

'Programming'.insert(0, 'Extreme ')
# => "Extreme Programming"
```

--

## More methods

```ruby
'Programming'.partition('gra')
# => ["Pro", "gra", "mming"]

'Programming'.reverse
# => "gnimmargorP"

'Programming! I love it! What about you?'.split
# => ["Programming!", "I", "love", "it!", "What", "about", "you?"]

'Programming!_I love it!_What about you?'.split('_')
# => ["Programming!", "I love it!", "What about you?"]
```

---

# Arrays

--

## Array

> Arrays are ordered, integer-indexed collections

- They can hold any object

- Array indexing starts at 0, as in C or Java.
- A negative index is assumed to be relative to the end of the array
 - an index of -1 indicates the last element

More [in the docs](http://ruby-doc.org/core-2.4.1/Array.html)...

--

## Creating

```ruby
[[1, 2, 3], 10, 3.14, 'This is a string']
# => [[1, 2, 3], 10, 3.14, "This is a string"]

Array.new
# => []

Array.new(3)
# => [nil, nil, nil]

Array.new(3, true)
# => [true, true, true]

%w(monkey fish lion cat #{Time.now}) # equivalent to ['monkey', 'fish'...
# => ["monkey", "fish", "lion", "dog", "cat", "\#{Time.now}"]

%W(monkey fish lion cat #{Time.now}) # equivalent to ["monkey", "fish" ...
# => ["monkey", "fish", "lion", "dog", "cat", "2013-05-03 12:24:42 +0300"]
```

--

## Accessing elements

```ruby
languages = 'Ruby', 'JavaScript', 'Python', 'PHP'
# => ["Ruby", "JavaScript", "Python", "PHP"]

languages.at(0) # => "Ruby"

languages[0] # => "Ruby"

languages[4] # => nil

languages[2..3] # => ["Python", "PHP"]

languages.take(3) 
# => ["Ruby", "JavaScript", "Python"]

languages[1] = 'CoffeeScript' 
# => "CoffeeScript"

languages # => ["Ruby", "CoffeeScript", "Python", "PHP"]
```

--

## Bonus: `dig`  Extracts nested values
<div style="text-align: right; margin-right:15%">
(only from 2.3.0)
</div>

```ruby
a = [[1, [2, 3] ]]

a.dig(0, 1, 1)
# => 3
```

--

## Adding items

```ruby
languages = ['Ruby', 'JavaScript', 'Python', 'PHP']
# => ["Ruby", "JavaScript", "Python", "PHP"]

languages.push('Closure')
# => ["Ruby", "JavaScript", "Python", "PHP", "Closure"]

languages << 'Haskell'
# => ["Ruby", "JavaScript", "Python", "PHP", "Closure", "Haskell"]

languages.unshift('C++')
# => ["C++", "Ruby", "JavaScript", "Python", "PHP", "Closure", "Haskell"]

languages.insert(3, 'CoffeeScript')
# => ["C++", "Ruby", "JavaScript", "CoffeeScript", "Python", "PHP", "Closure",...

languages.insert(4, 'Haml', 'Sass')
# => ["C++", "Ruby", "JavaScript", "CoffeeScript", "Haml", "Sass", "Python",...
```

--

## Removing items (1)

```ruby
languages = ['C++', 'Ruby', 'JavaScript', 'CoffeeScript', 'Haml']
# => ["C++", "Ruby", "JavaScript", "CoffeeScript", "Haml"]

languages.pop
# => "Haml"

languages
# => ["C++", "Ruby", "JavaScript", "CoffeeScript"]

languages.shift
# => "C++"

languages
# => ["Ruby", "JavaScript", "CoffeeScript"]

languages.delete_at(2)
# => "CoffeeScript"

languages
# => ["Ruby", "JavaScript"]

languages.delete('JavaScrip')
# => "JavaScrip"
```

--

## Removing items (2)

```ruby
languages
# => ["Ruby", "JavaScript", "Haml", "Sass", "Python", "Closure"]

languages = ['Ruby', 'JavaScript', nil, 0, 'Python', nil]
# => ["Ruby", "JavaScript", nil, 0, "Python", nil]

languages.compact
# => ["Ruby", "JavaScript", 0, "Python"]

languages = ['Ruby', 'JavaScript', 'PHP', 'Python', 'PHP']
languages.uniq
# => ["Ruby", "JavaScript", "PHP", "Python"]
```

--

## Obtaining information

```ruby
languages = ['Ruby', 'JavaScript', 'PHP', 'Python', 'PHP']
# => ["Ruby", "JavaScript", "PHP", "Python", "PHP"]

languages.length
languages.count
languages.size
# => 5

languages.empty?
# => false

languages.any?
# => true

languages.include?('Ruby')
# => true

languages.include?('Closure')
# => false
```

--

## Concatenation

```ruby
days1 = ['Mon', 'Tue', 'Wed']
days2 = ['Thu', 'Fri', 'Sat', 'Sun']

days1 + days2
# => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

days1.concat(days2)
# => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

days1 = ['Mon', 'Tue', 'Wed']

days1 << 'Thu' << 'Fri' << 'Sat' << 'Sun'
# => ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
```

--

## Operations (1)

```ruby
os = ['Fedora', 'SUSE', 'Red Hat', 'MacOS', 'Windows']
linux_os = ['SUSE', 'Red Hat', 'Ubuntu', 'Fedora']
```

Union

```ruby
os | linux_os
# => ["Fedora", "SUSE", "Red Hat", "MacOS", "Windows", "Ubuntu"]
```

Intersection

```ruby
os & linux_os
# => ["Fedora", "SUSE", "Red Hat"]
```

Difference

```ruby
os - linux_os
# => ["MacOS", "Windows"]

linux_os - os
# => ["Ubuntu"]
```

--

## Operations (2)

```ruby
os = ['Fedora', 'SUSE', 'Red Hat', 'MacOS', 'Windows']
linux_os = ['SUSE', 'Red Hat', 'Ubuntu', 'Fedora']
```

Addition

```ruby
linux_os + ['Debian', 'Gentoo']
# => ["SUSE", "Red Hat", "Ubuntu", "Fedora", "Debian", "Gentoo"]
```

Multiplication

```ruby
linux_os * 2
# => ["SUSE", "Red Hat", "Ubuntu", "Fedora", "SUSE", "Red Hat", "Ubuntu", "Fedora"]

linux_os * ', '
# => "SUSE, Red Hat, Ubuntu, Fedora"
```

--

## Iteration

each

```ruby
a = ['a', 'b', 'c']
a.each { |x| print x, ' -- ' }
# a -- b -- c --
```

each_with_index

```ruby
a = ['a', 'b', 'c']
a.each_with_index { |item, index| puts "[#{index}] => #{item}" }
# [0] => a
# [1] => b
# [2] => c
```
> `each` is actually a VIP method with regards to enumeration.

> There is a `for` construct it's not idiomatic.

--

## Long live `each` method !

```ruby
nums = [1,2,3,4]

nums.each { |n|  print n  }
#         ↑that's a block ↑

nums.each do |n| # ← that's
  print n        # ← also a
end              # ← block!
```


### Under the hood:
`each`
<span style="color:red">yields</span>
 n to the given
<span style="color:blue">block</span>.


---

# Symbols

> Symbols as a type are much like a compiler/interpeter's symbols.

> Ruby too uses a Symbol Table to hold them.

more info [in the docs](http://www.ruby-doc.org/core-2.4.1/Symbol.html)

--

## :symbols are nice, they...
- start with a colon
- are immutable
- usually represent names of things.
 - e.g method names

```ruby
Fixnum.methods
# => [:class, :to_s, :superclass, :name, :is_a? ...

1.methods
# => [:to_s, :+, :-, :*, :abs, :zero?, :next ...

```

> The symbol object will be unique for each different name,
>  but does not refer to a particular "instance" of the name.

--

## Symbol examples

```ruby
:ruby_rules      # => :ruby_rules

:"Ruby rules"    # => :"Ruby rules"

:ruby.object_id  # => 319048

:ruby.object_id  # => 319048

'ruby'.object_id # => 70200985531220

'ruby'.object_id # => 70200985514360
```

--

## Symbols' usage

99/100 times Symbols are used as one of 2 things :
- keys in Hashes (see next slide)
- names of methods / attributes of objects

---

# Hashes
<div style="text-align: right; margin-right:15%">
(you can guess the data structure...)
</div>

--

## What's a Hash ?

> A Hash is a collection of key-value pairs. It is/looks similar to an Array (sometimes it is called an associative array),
except that indexing is done via arbitrary keys of any object type, not an integer index.

More [in the docs](http://www.ruby-doc.org/core-2.4.1/Hash.html)

--

## Creating
Hash literals are created with hash rockets `=>`

```ruby
{ 'font_size' => 10, 'font_family' => 'Arial' }
# => {"font_size"=>10, "font_family"=>"Arial"}

a = 'ruby'
b = 'clojure'

h = { a => 'awesome', b => 'functional' }

{ :font_size => 10, :font_family => 'Arial' } # "old" hash-rocket style
# => {:font_size=>10, :font_family=>'Arial'}

Hash.new
# => {}

```

--

## Symbols + Hashes = ❤

```ruby
{ font_size: 10, font_family: 'Arial' } # New hash-colon style
# => {:font_size=>10, :font_family=>"Arial"}

```

--

## Default values

```ruby
h = Hash.new('Default value')
# => {}

h['key']
# => "Default value"

h = Hash.new { |hash, key| hash[key] = "Default value: #{key}" }
# => {}

h['key']
# => "Default value: key"

h = Hash.new
h.default = 'Default value'

h['key']
# => "Default value"
```

--

## Removing items

delete

```ruby
h = { a: 100, b: 200 }
h.delete(:a) # => 100
h.delete(:z) # => nil
```

delete_if

```ruby
h = { a: 100, b: 200, c: 300 }
h.delete_if { |key, value| value > 100 } # => {"a"=>100}
```

keep_if

```ruby
h = { a: 100, b: 200, c: 300 }
h.keep_if { |key, value| value > 100 } # => {"b"=>200, "c"=>300}
```

--

## Iteration

each

```ruby
h = { a: 100, b: 200 }
h.each { |key, value| puts "#{key} is #{value}" }
# a is 100
# b is 200
# => {"a"=>100, "b"=>200}
```

each_key

```ruby
h = { a: 100, b: 200 }
h.each_key { |key| puts key }
# a
# b
# => {"a"=>100, "b"=>200}
```

each_value

```ruby
h = { a: 100, b: 200 }
h.each_value { |value| puts value }
# 100
# 200
# => {"a"=>100, "b"=>200}
```

--

## Useful methods (1)

key? / include?

```ruby
h = { a: 100, b: 200 }

h.key?(:a) # => true
h.key?(:z) # => false
h.include?(:a) # => true

```

value?

```ruby
h = { a: 100, b: 200 }

h.value?(100) # => true

h.value?(999) # => false
```

--

## Useful methods (2)

keys

```ruby
h = { a: 100, b: 200 }

h.keys # => ["a", "b"]
```

values

```ruby
h = { a: 100, b: 200, c: 300 }

h.values # => [100, 200, 300]
```

values_at

```ruby
h = { a: 100, b: 200, c: 300 }

h.values_at('a', 'c') # => [100, 300]
```

--

## Useful methods (3)

length / size

```ruby
h = { d: 100, a: 200, v: 300, e: 400 }

h.length # => 4
h.size # => 4

h.delete('a') # => 200

h.length # => 3
```

merge

```ruby
h1 = { a: 100, b: 200 }
h2 = { b: 254, c: 300 }

h1.merge(h2)
# => {"a"=>100, "b"=>254, "c"=>300}
```

--

## Useful methods (4)

select

```ruby
h = { a: 100, b: 200, c: 300 }

h.select { |key, value| value > 100}
# => {"b"=>200, "c" =>300}
```

dig (2.3.0 only)

```ruby
h = { a: { b: { c: 1 } } }

h.dig(:a, :b, :c)    # => 1

h.dig(:a, :some, :c) # => nil

h[:a][:some][:c]
# => NoMethodError: undefined method '[]' for nil:NilClass

h = { a: [10, 11, 12] }

h.dig(:a, 1)
# => 11
```

---

# Ranges

> A Range represents an interval — a set of values with a beginning and an end.

More info [in the docs](http://www.ruby-doc.org/core-2.4.1/Range.html)

--

Creates a range from `1` to `10` inclusive

```ruby
1..10
(1..10).to_a
# => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

Creates a range from `1` to `10` exclusive

```ruby
1...10
(1...10).to_a
# => [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Creates a range from `a` to `e`

```ruby
('a'..'e').to_a
# => ["a", "b", "c", "d", "e"]
```


---

# Time

> Time is an abstraction of dates and times.

More info [in the docs](http://www.ruby-doc.org/core-2.4.1/Time.html)

--

## Time

```ruby
Time.now
# 2017-05-12 14:14:37 +0300

Time.new(2016)
# => 2016-01-01 00:00:00 +0200

Time.new(2016, 10)
# => 2016-10-01 00:00:00 +0300

Time.new(2016, 10, 30, 2, 2, 2, '+03:00')
# => 2016-10-30 02:02:02 +0300

Time.at(628232400) # Create with UNIX timestamp
# => 1989-11-28 08:00:00 +0300
```

--

## Time

```ruby
t = Time.new("2013-05-09 18:50:25")
# => 2013-05-09 18:50:25 +0300

t.year  # => 2013
t.month # => 5
t.day   # => 9
t.hour  # => 18
t.min   # => 50
t.sec   # => 25
t.zone  # => "EEST"

t.strftime('%Y-%m-%d %H:%M:%S')
# => "2013-05-09 18:50:25"
```

---

# File

> The `File` abstraction is closely associated with class `IO`.

More info [in the docs](http://www.ruby-doc.org/core-2.4.1/File.html)

--

## Open and close

new

```ruby
File.new('tmp.txt', 'w')
# => #<File:tmp.txt>
```

open, close

```ruby
f = File.open('tmp.txt', 'r')
# => #<File:tmp.txt>

f.closed? # => false

f.close

f.closed? # => true
```

--

## Read

read

```ruby
File.read('tmp.txt')
# => "This is line one\nThis is line two\nThis is line three\nAnd so on...\n"

File.read('tmp.txt', 20)
# => "This is line one\nThi"

File.read('tmp.txt', 20, 10)
# => "ne one\nThis is line "
```

--

## Read

readlines

```ruby
a = File.readlines('tmp.txt')

a[0]
# => "This is line one\n"

a[1]
# => "This is line two\n"
```

each

```ruby
f = File.open('tmp.txt', 'r')

f.each do |line|
  print line
end
```

--

## Write, rename, delete

write, puts

```ruby
f = File.open('tmp.txt', 'w')
f.write('new text')
```

rename

```ruby
File.rename('old_name.txt', 'new_name.txt')
```

delete

```ruby
File.delete('file.txt')
```

--

## Useful methods

ftype

```ruby
File.ftype('file.txt')
# => "file"

File.ftype('.')
# => "directory"
```

join

```ruby
File.join('usr', 'mail', 'gumby')
# => "usr/mail/gumby"
```

---

# Dir

> Objects of class Dir are directory streams representing directories in the underlying file system.

>They provide a variety of ways to list directories and their contents.

More info [in the docs](http://ruby-doc.org/core-2.4.1/Dir.html).

--

entries

```ruby
Dir.entries('testdir')
# => [".", "..", "config.h", "main.rb"]
```

glob

```ruby
Dir.glob('*.[a-z][a-z]')
# => ["main.rb"]
```

foreach

```ruby
Dir.foreach('testdir') { |x| puts "Got #{x}" }
# Got .
# Got ..
# Got config.h
# Got main.rb
```

mkdir

```ruby
Dir.mkdir(File.join(Dir.home, '.foo'), 0700)
```

---

# Variables

--

## Local

```ruby
v = 'Ruby'
# => "Ruby"

v.class
# => String

v.kind_of? String
# => true

v.is_a? String
# => true

v.instance_of? String
# => true

defined? v
# => "local-variable"
```

--

## Instance

```ruby
@i = 'Ruby'
# => "Ruby"

defined? @i
# => "instance-variable"
```

--

## Global

```ruby
$g = 'Ruby'
# => "Ruby"

defined? $g
# => "global-variable"
```

--

## Constant

```ruby
C = 'Ruby'
# => "Ruby"

defined? C
# => "constant"
```

---

# Conditional statements

--

## If, unless

```ruby
if a == 4
  a = 7
end
```

```ruby
if a == 4 then a = 7 end
```

```ruby
a = 7 if a == 4
```

```ruby
if a != 4
  a = 7
end
```

```ruby
unless a == 4
  a = 7
end
```

```ruby
a = 7 unless a == 4
```

--

## Using

Bad

```ruby
unless some_condition?
  # do something
else
  # do something else
end
```

Good

```ruby
if some_condition?
  # do something else
else
  # do something
end
```

--

## Using

Bad

```ruby
unless some.nil?
  # do something
end
```

Good

```ruby
if some
  # do something
end
```

--

## Using

Bad

```ruby
unless first_condition? && second_condition?
  # do something
end
```

Good

```ruby
if !first_condition? || !second_condition?
  # do something
end
```

--

## If, elsif, else

```ruby
a = 1
res = if a < 5
        "#{a} less than 5"
      elsif a > 5
        "#{a} greater than 5"
      else
        "#{a} equals 5"
      end
res
# => "1 less than 5"
```

--

## Ternary operator

```ruby
true ? 't' : 'f'
# => "t"

false ? 't' : 'f'
# => "f"
```

--

## and

```ruby
nil && 99
# => nil

false && 99
# => false

'cat' && 99
# => 99
```

--

## or

```ruby
nil || 99
# => 99

false || 99
# => 99

'cat' || 99
# => "cat"
```

--

> At first glance, `and` and `or` appear to be synonyms for `&&` and `||`.

> You might be tempted to use them to improve readability.

> But `and`/`or` don’t behave the same as `&&`/`||`

```ruby
one = :one
two = nil

t = one and two   # => nil

t                 # => :one

t = one && two    # => nil

t                 # => nil

t = (one and two) # => nil

t                 # => nil

(t = one) && two  # => nil

t                 # => :one
```

--

## Case, when

```ruby
a = 1
r = case
    when a < 5
      "#{a} less than 5"
    when a > 5
      "#{a} greater than 5"
    else
      "#{a} equals 5"
    end
r
# => "1 less than 5"
```

```ruby
a = 1
case a
when 0...5
  "#{a} greater than 0 less than 5"
when 5
  "#{a} equals 5"
when 5..Float::INFINITY
  "#{a} greater than 5"
else
  "#{a} less than 0"
end
# => "1 greater than 0 less than 5"
```

--

## Loop

```ruby
i = 0

loop do
  i += 1

  next if i == 5

  print "#{i} "

  break if i == 10
end
# => 1 2 3 4 6 7 8 9 10
```

--

## While

```ruby
i = 1

while i < 11
  print "#{i} "

  i += 1
end
# => 1 2 3 4 6 7 8 9 10
```
> There is is a lso a construct similar to `do` stuff `while` condition

> but `loop is prefered for these cases

--

## Until

```ruby
i = 1

until i > 10
  print "#{i} "

  i += 1
end
# => 1 2 3 4 6 7 8 9 10
```

--

## Each

```ruby
[1,2,3,4,5,6,7,8,9,10].each { |value| print "#{value} " }
# => 1 2 3 4 6 7 8 9 10
```

--

## For
~~content deleted~~
###use `each`

--

## Times

```ruby
10.times { |i| print "#{i} " }
# => 0 1 2 3 4 6 7 8 9
```

--

## Upto

```ruby
1.upto(10) { |i| print "#{i} " }
# => 1 2 3 4 6 7 8 9 10
```

---

# Methods

--

## Methods

```ruby
'Goonies has a rank of 10'
'Ghostbusters has a rank of 9'
'Goldfinger has a rank of 8'
```

```ruby
def movie_listing(title, rank = 5)
  "#{title.capitalize} has a rank of #{rank}"
end

movie_listing('goonies', 10)
# => "Goonies has a rank of 10"

movie_listing('ghostbusters', 9)
# => "Ghostbusters has a rank of 9"

movie_listing('goldfinger')
# => "Goldfinger has a rank of 5"
```

--

## Definition

```ruby
def my_method
  # Code for the method would be here
end

def my_method_with_arguments(arg1, arg2, arg3)
  # Code for the method would be here
end
```

```ruby
def cool_dude(arg1 = 'Miles', arg2 = 'Coltrane', arg3 = 'Roach')
  "#{arg1}, #{arg2}, #{arg3}"
end

cool_dude
# => "Miles, Coltrane, Roach"

cool_dude('Bart')
# => "Bart, Coltrane, Roach"

cool_dude('Bart', 'Elwood')
# => "Bart, Elwood, Roach"

cool_dude('Bart', 'Elwood', 'Linus')
# => "Bart, Elwood, Linus"
```

--

## Arguments

```ruby
def var_args(a, b, c=1, *d, e, f)
  puts "required a #{a}"
  puts "required b #{b}"
  puts "optional c #{c}"
  puts "argument array d #{d.inspect}"
end

var_args(1,2,3,4,5,6,7,8,9)
# required a 1
# required b 2
# optional c 3
# argument array d [4, 5, 6, 7]
# => nil
```

--

## Invalid order

sponge arguments `*` should be always after optional

```ruby
def invalid_args(x, *y ,z = 1) end
```

## More examples

```ruby
def split_apart(first, *split, last)
  "first: #{first.inspect}, split: #{split.inspect}, last: #{last.inspect}"
end

split_apart(1, 2)
# => "first: 1, split: [], last: 2"

split_apart(1, 2, 3)
# => "first: 1, split: [2], last: 3"

split_apart(1, 2, 3, 4)
# => "first: 1, split: [2, 3], last: 4"
```

```ruby
def split_apart(first, *, last)
  # ...
end
```

--

## Return values

```ruby
def meth_one
  'one'
end

meth_one
# => "one"
```

```ruby
def meth_two(arg)
  if arg > 0
    'positive'
  elsif arg < 0
    'negative'
  else
    'zero'
  end
end

meth_two(23)
# => "positive"

meth_two(0)
# => "zero"
```

--

## Return values

```ruby
def meth_three
  100.times do |num|
    square = num * num

    return num if square > 1000
  end
end

meth_three
# => 32
```

--

## Blocks

> A block is code that is passed to a method by using of either curly braces, `{...}`, or do...end syntax.
It's common convention to use `{...}` for single line blocks, and `do...end` for multi-line blocks,
but curly braces have higher precedence.

--

## Using blocks

1. Passed as a method argument, using the special `&` last-argument syntax sugar operator or a `block_given?`/`yield`
pair.

2. As a `Proc` object (or the `lambda`).

  **Important:**
  1. You can pass only one block to method.
  2. Block should follow method arguments braces.

3. Block hasn't access to method local variables but we can pass them to block. And They can be changed inside block.

4. If method local variable has te same name as block local variable then method local variable is not availaba inside
block.

5. Arguments number is important for method and not important for block.

6. if you want to pass as method argument you must use braces otherwise it is treated as block and rises an error.

--

## Using blocks

```ruby
def double(p1)
  yield(p1*2)
end

double(3) { |val| "I got #{val}" }
# => "I got 6"

double('tom') do |val|
  "Then I got #{val}"
end
# => "Then I got tomtom"
```

--

## Using blocks

```ruby
def try
  if block_given?
    yield
  else
    'no block'
  end
end

try
# => "no block"

try { 'hello' }
# => "hello"

try do 'hello' end
# => "hello"
```

--

## Closures

```ruby
def thrice
  yield
  yield
  yield
end

x = 5

puts "value of x before: #{x}"
# => "value of x before: 5"

thrice { x += 1 }

puts "value of x after: #{x}"
# => "value of x after: 8"
```

--

## Convert the block to a Proc

```ruby
def thrice
  yield
  yield
  yield
end

def seven_times(&block)
  block.call
  thrice(&block)
  thrice(&block)
end

x = 4

seven_times { x += 10 }
# => 74
```

```ruby
def what_am_i(&block)
  block.class
end

what_am_i {}
# => Proc
```

--

## Proc aka procedure

```ruby
square = Proc.new do |n|
  n ** 2
end

square.call(2)
# => 4

square.call(4)
# => 16
```
<!-- .element: class="left width-50" -->

```ruby
square = proc do |n|
  n ** 2
end

square.call(2)
# => 4

square.call(4)
# => 16
```
<!-- .element: class="right width-50" -->

--

## Anonymous

```ruby
bo = lambda do |param|
  "You called me with #{param}"
end

bo.call(99)
# => "You called me with 99"
```
<!-- .element: class="left width-50" -->

```ruby
bo = ->(param) { "You called me with #{param}" }

bo.call(99)
# => "You called me with 99"
```
<!-- .element: class="right width-50" -->

--

## Proc vs lambda

> Lambdas check the number of arguments

```ruby
def args(code)
  one, two = 1, 2
  code.call(one, two)
end

args(Proc.new{ |a, b, c| puts "Give me a #{a} and b #{b} and c #{c}"})
# Give me a 1 and b 2 and c

args(lambda{ |a, b, c| puts "Give me a #{a} and b #{b} and c #{c}"})
# => ArgumentError: wrong number of arguments (2 for 3)
```

--

## Proc vs lambda

> Lambdas have lesser returns

```ruby
def proc_return
  Proc.new { return 'Proc.new' }.call
  return 'proc_return return'
end

def lambda_return
  lambda { return 'lambda' }.call
  return 'lambda_return return'
end

proc_return
# => "Proc.new"

lambda_return
# => "lambda_return return"
```

--

## Proc vs lambda

### Conclusion

- `blocks` and `Procs` act like code snippets
- `lambdas` and `Methods` act like methods

--

## Method to object

```ruby
def square(n)
  n ** 2
end

square_obj = method(:square)

square_obj.class
# => Method

square_obj.call(4)
# => 16
```

--

## Naming

### `?` - return true or false

```ruby
movie = ''
movie.empty?
# => true

movie = 'Goonies'
movie.empty?
# => false

movie.include?('G')
# => true

movie.include?('x')
# => false
```

--

### `!` - change the current object

```ruby
movie = 'Ghostbusters'
# => "Ghostbusters"

movie.reverse
# => "sretsubtsohG"

movie
# => "Ghostbusters"

movie.reverse!
# => "sretsubtsohG"

movie
# => "sretsubtsohG"
```

--

## Operators

```ruby
num = 12
# => 12

num * 2
# => 24

num.*(2)
# => 24
```

---

# Ruby Koans

--

## Ruby Koans Online

The [Ruby Koans](http://rubykoans.com/) are a great way to learn about the Ruby language.

```bash
$ git clone git://github.com/edgecase/ruby_koans.git ruby_koans
$ cd ruby_koans
```

```bash
$ rake gen
$ mkdir -p koans
$ cp src/edgecase.rb koans/edgecase.rb
$ cp README.rdoc koans/README.rdoc
```

```bash
$ rake

The Master says:
You have not yet reached enlightenment.
The answers you seek...
Failed assertion, no message given.
Please meditate on the following code:
/Users/sparrow/Www/ruby_koans/koans/about_asserts.rb:10:in 'test_assert_truth'
mountains are merely mountains
your path thus far [X_________________________________________________] 0/280
```

---

# The End
