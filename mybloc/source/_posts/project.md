---
title: project for Ruby
date: 2017-09-14 09:58:56
tags:
---



## Introduction to Ruby （变换字体的大小写）
> PUTTING THE FORM IN FORMATTER
Read a user's input and correct his or her capitalization.

``` ruby
print "What is your name? "    
name = gets.chomp
name.capitalize!

print "What city are you from? "				
city = gets.chomp
city.upcase!

puts "Your name is #{name} and you are from #{city}!"
```

``` bash
What is your name?                    # $ katherine
What city are you from?               # $ guangzhou

# =>Your name is Katherine and you are from GUANGZHOU!
```


1. 提示用户输入信息 `print "What is your name? " `
2. 获得用户的信息  `variable_name = gets.chomp`
   `gets`    gets input from the user. (会自动换行)
   `chomp` removes that extra line.（移除多余的行数）
3. 转换大小写
  `.capitalize` 显示单词的第一个字母为大写，其他的为小写
  `.upcase` 显示单词的所有字母为大写
  `!` at the end of the method name so that Ruby will change the string in-place.
4. 输出内容：插入字串（string interpolation） `#{variable_name}`

---

##  Control Flow in Ruby（让`"s"` 和 `"th"` 互换）
> THITH MEANTH WAR!
Daffy Duckify a user's string, replacing each `"s"` with `"th"`

``` ruby
print "Pleathe enter a thtring: "
user_input = gets.chomp
user_input.downcase!

if user_input.include? "th"
  user_input.gsub!(/th/, "s")
else
  puts "Nothing to do here!"
end

puts "Your string is: #{user_input}"
```

``` bash
Pleathe enter a thtring:          # $ thtring
# => Your string is: string

Pleathe enter a thtring:          # $ haha
# => Nothing to do here!
# => Your string is: haha
```

1. 把用户输入的内容全部转换为小写 `.downcase!`
2. 设置条件 `if string_to_check.include? "substring"`
    `?` 按照惯例，通常表示判断 `true` 和 `false`，
3. 条件内容：如果`true`就执行 `string_to_change.gsub!(/s/, "th")`   
   `.gsub!` stands for global substitution(替换字符中的单词)

---

## Looping with Ruby（隐藏输入的信息）
> REDACTED!
> Hiding information is a major part of programming: protecting passwords, establishing secure connections, and securing programs against tampering all rely on controlling access to information.
> change a user's input with the tools we have now: arrays and iterators.

``` ruby
puts "Text to search through: "
text = gets.chomp
puts "Word to redact: "
redact = gets.chomp

words = text.split(" ")

words.each do |word|
  if word != redact
    print word + " "
  else
    print "REDACTED "
  end
end
```

``` bash
Text to search through:           # $ today is Monday
Word to redact:                   # $ Monday
# => today is REDACTED

```

- `.split`  将字串(string)转换为数组(array).
    **delimiter** :`string.split()` 括号中可添加内容，若`sting`中有对应括号中的内容，`.split`会移除与内容对应的字串元素。
``` ruby
# example
text = "today is Monday"
words1 = text.split(" ")              # => ["today", "is", "Monday"]
words2 = text.split("y")              # => ["toda", " is Monda"]
words3 = text.split(",")              # => ["today is Monday"]

# test
text = "today is Monday"
words = text.split(" ")
print words                           # => ["today", "is", "Monday"]

```

- 打印信息
``` ruby
# example
letters = ['a', 'b', 'c', 'd']
letters.each do |letter|
  print letter                           # => abcd
end

# test
words = ["today", "is", "Monday"]
words.each do |word|
    print word + " "                     # => today is Monday
end
```

- 添加筛选条件
``` ruby
# test
words = ["today", "is", "Monday"]
redact = "Monday"

words.each do |word|
  if word != redact
    print word + " "                     # => today is
  end
end
```


- 添加判断语句（Control Flow Know-How）
``` ruby
# example
if var == 10
   print "Variable is 10"
else
   print "Variable is something else"
end
```

---

## Arrays and Hashes（计算字符串出现的频率）

>  Create a Histogram
>  Show the number of times that word occurs
>  takes a user's input, then builds a hash from that input.
>  Each key in the hash will be a word from the user;
>  each value will be the number of times that word occurs.

``` ruby
puts "Text please: "
text = gets.chomp

words = text.split(" ")
frequencies = Hash.new(0)
words.each { |word| frequencies[word] += 1 }
frequencies = frequencies.sort_by {|a, b| b }
frequencies.reverse!
frequencies.each { |word, frequency| puts word + " " + frequency.to_s }
```

``` bash
Text please:                # $ what do you mean ohh ohh ohh
# => ohh 3
# => mean 1
# => you 1
# => do 1
# => what 1
```
A visual representation of data like this is called a ***histogram***.


1. 从控制面板获得句子 (get input from the user)
   ``` ruby
   puts "Text please: "
   text = gets.chomp            # $ what do you mean ohh ohh ohh
   print text                   # => what do you mean ohh ohh ohh
   ```

2. 用`.split` 将字串换成数组(Building the Words Array)

   ``` ruby
   text = "what do you mean ohh ohh ohh"
   words = text.split(" ")
   print words                  
   # => ["what", "do", "you", "mean", "ohh", "ohh", "ohh"]
   ```

3. 建立散列（用于计算数组内单词发生的频率）
  Creating the Frequencies Hash( create a hash mapping strings to integers.)
``` ruby
# example
h = Hash.new("nothing here")         # 建立新的空散列，默认值为“nothing here”
puts h                               # => {}
puts h["kitty"]                      # => nothing here

# test
frequencies = Hash.new(0)             # 设定单词频率的默认值为0
puts frequencies                      # => {}
puts frequencies["ohh"]               # => 0
```

4. 把数组转变成有频率的散列(Iterating Over the Array)
    iterate over `words`to add each word to our `frequencies` hash, one at a time.
``` ruby
# test
colors = { "red" => 2, "blue" => 3 }      # 假定一个散列（键为字串，值为整数）
colors["blue"] += 1                       # 增值value（为"blue"的值添加1）
puts colors["blue"]                       # => 4

# try 1
frequencies = Hash.new(0)                 # 默认值为0
frequencies["kaka"] += 1 						 
puts frequencies["kaka"]                  # => 1

# try 2
words = ["what", "do", "you", "mean", "ohh", "ohh", "ohh"]
frequencies = Hash.new(0)
words.each { |word| frequencies[word] += 1 }
print frequencies					 
# => {"what"=>1, "do"=>1, "you"=>1, "mean"=>1, "ohh"=>3}
```

5. 对散列内的字串和频率排列顺序（Sorting the Hash）
  `.sort_by` returns an array of arrays:
  sort `colors` into green, red, and blue, from smallest to largest by count
  `.reverse` the array order so that the colors with the largest counts are first.
``` ruby
# example
colors = {                    # 建立以"color"为键，整数为对象的散列
  "blue" => 3,  
  "green" => 1,
  "red" => 2
}
colors = colors.sort_by do |color, count|  
  count
end
print colors                  # => [["green", 1], ["red", 2], ["blue", 3]]

colors.reverse!
print colors                  # => [["blue", 3], ["red", 2], ["green", 1]]


# test
frequencies = {"what"=>1, "do"=>1, "you"=>1, "mean"=>1, "ohh"=>3}
frequencies = frequencies.sort_by do |frequencies, count|
  count
end
frequencies.reverse!

print frequencies             
# => [["ohh", 3], ["mean", 1], ["you", 1], ["do", 1], ["what", 1]
```

6. 将散列转换为histogram(Iterating Over the Hash)
  iterate over `.each` key/value pair, storing the key as `name` and the value as `count`.
  `puts name + " "` print out the key and value separated by a space.
  `.to_s` convert the value from a number to a string
``` ruby
# example
fruit = {                           # 建立以水果为键，整数为对象的散列
  "apple" => 2,
  "banana" => 3,
  "cherry" => 5
}

fruit.each do |name, count|
  puts name + " " + count.to_s      # => apple 2     banana 3     cherry 5
end

# test
frequencies = [["ohh", 3], ["mean", 1], ["you", 1], ["do", 1], ["what", 1]]

frequencies.each do |word, frequency|
  puts word + " " + frequency.to_s    
end

# => ohh 3
# => mean 1
# => you 1
# => do 1
# => what 1
```
---

## Blocks and Sorting（为书籍排序）
 > Order your libary

``` ruby
def alphabetize(arr, rev=false)
  if rev
    arr.sort { |item1, item2| item2 <=> item1 }
  else
    arr.sort { |item1, item2| item1 <=> item2 }
  end
end

books = ["Heart", "Code Complete", "The Lorax", "The Prophet", "Absalom!"]

puts "A-Z: #{alphabetize(books)}"
puts "Z-A: #{alphabetize(books, true)}"

# => A-Z: ["Absalom!", "Code Complete", "Heart", "The Lorax", "The Prophet"]
# => Z-A: ["The Prophet", "The Lorax", "Heart", "Code Complete", "Absalom!"]

```
1. 定义方法（Defining Our Method）
``` ruby
def alphabetize
  # Do something
end
```

2. 设置参数（Default Parameters）
`arr` (for "array")
`rev=false`
`rev` (for "reverse")如果使用者没有输入两个参数，`rev`默认为 `false`
``` ruby
def alphabetize(arr, rev=false)
  # Do something
end
```

3. 排序（Sorting）
`.sort` simply returns a sorted array while leaving the original array alone
`.sort!` modifies the actual array
``` ruby
# example 1
numbers = [5, 1, 3, 8]
numbers.sort!                   # => [1, 3, 5, 8]
numbers.reverse!                # => [8, 5, 3, 1]

# test 1
books = ["Heart", "Code Complete", "The Lorax", "The Prophet", "Absalom!"]
books.sort!
# => ["Absalom!", "Code Complete", "Heart", "The Lorax", "The Prophet"]

books.reverse!
# => ["The Prophet", "The Lorax", "Heart", "Code Complete", "Absalom!"]
```

  `<=>` the *combined comparison operator* ,to compare two Ruby objects.
``` ruby
# test 2
books = ["Heart", "Code Complete", "The Lorax", "The Prophet", "Absalom!"]

# To sort our books in ascending order(A – Z ), in-place
books.sort! { |firstBook, secondBook| firstBook <=> secondBook }
# => ["Absalom!", "Code Complete", "Heart", "The Lorax", "The Prophet"]

# Sort your books in descending order(Z – A ), in-place below
books.sort! { |firstBook, secondBook| secondBook <=> firstBook }
# => ["The Prophet", "The Lorax", "Heart", "Code Complete", "Absalom!"]
```


4. 添加条件控制（Sorting With Control Flow）
  `if-else` statement. If `rev` is true, call `reverse!` on `arr`, `else` return `arr`.
``` ruby
# example
def alphabetize(arr, rev=false)
  if rev
    arr.sort { |item1, item2| item2 <=> item1 }
  else
    arr.sort { |item1, item2| item1 <=> item2 }
  end
end
```
---

## Hashes and Symbols（查询电影）
> A NIGHT AT THE MOVIES: Keep track of our movie ratings
It'll do one of four things: add a new movie to a hash, update the rating for an existing movie, display the movies and ratings that are already in the hash, or delete a movie from the hash. If it doesn't receive one of those four commands, the program will output some kind of error message.

``` ruby
movies = {
  Memento: 3,
  Primer: 4,
  Ishtar: 1
}

puts "What would you like to do?"
puts "-- Type 'add' to add a movie."
puts "-- Type 'update' to update a movie."
puts "-- Type 'display' to display all movies."
puts "-- Type 'delete' to delete a movie."

choice = gets.chomp.downcase
case choice
when 'add'
  puts "What movie do you want to add?"
  title = gets.chomp
  if movies[title.to_sym].nil?
    puts "What's the rating? (Type a number 0 to 4.)"
    rating = gets.chomp
    movies[title.to_sym] = rating.to_i
    puts "#{title} has been added with a rating of #{rating}."
  else
    puts "That movie already exists! Its rating is #{movies[title.to_sym]}."
  end
when 'update'
  puts "What movie do you want to update?"
  title = gets.chomp
  if movies[title.to_sym].nil?
    puts "Movie not found!"
  else
    puts "What's the new rating? (Type a number 0 to 4.)"
    rating = gets.chomp
    movies[title.to_sym] = rating.to_i
    puts "#{title} has been updated with new rating of #{rating}."
  end
when 'display'
  movies.each do |movie, rating|
    puts "#{movie}: #{rating}"
  end
when 'delete'
  puts "What movie do you want to delete?"
  title = gets.chomp
  if movies[title.to_sym].nil?
    puts "Movie not found!"
  else
    movies.delete(title.to_sym)
    puts "#{title} has been removed."
  end
else
  puts "Sorry, I didn't understand you."
end
```
``` bash
What would you like to do?
-- Type 'add' to add a movie.
-- Type 'update' to update a movie.
-- Type 'display' to display all movies.
-- Type 'delete' to delete a movie.


# $ add
What movie do you want to add?	                    # => StarWars
What is  the rating? (Type a number 0 to 4.)        # => 3
StarWars has been added with a rating of 3.
# $ add
What movie do you want to add?                      # => Primer
That movie already exists! Its rating is 4.

# $ update
What movie do you want to update?                   # => Primer
What is the new rating? (Type a number 0 to 4.)     # => 3.8
Primer has been updated with new rating of 3.8.
# $ update
What movie do you want to update?                   # => Cat
Movie not found!

# $ display
                                                    # => Memento: 3
                                                    # => Primer: 4
                                                    # => Ishtar: 1

# $ delete
What movie do you want to delete?                   # => Ishtar
Ishtar has been removed.
# $ delete  
What movie do you want to delete?                   # => Cat
Movie not found

# $ "others"
Sorry, I did not understand you.
```
1. 建立基本信息（Setting Up）
``` ruby
# example
favorite_foods = {
  'vegetable' => 'broccoli'
}
puts "Do you like coding in Ruby?"
answer = gets.chomp
```

2. 建立情景（The Case Statement）
  `if` and `else` are powerful, but we can get bogged down in `if`s and `elsif`s if we have a lot of conditions to check.
  The `case` statement: The `else` is what the `case` statement will do if it doesn't match any of its `when` statements to the `case`
``` ruby
# example
case language
  when "JS"
    puts "Websites!"
  when "Python"
    puts "Science!"
  when "Ruby"
    puts "Web apps!"
  else
    puts "I don't know!"
end

# test
puts "Type add/update/display/delete here. "
choice = gets.chomp.downcase

case choice
  when "add"
  puts "Added!"
  when "update"
  puts "Update!"
  when "display"
  puts "Movies!"
  when "delete"
  puts "Deleted!"
  else
  puts "Error!"
end
```

3. 细化 `add` (Prompting: Redux!)
从使用者中获得电影名称和评级的字串`string`并且转换成了散列`hash`  
创建变量`title`，并提示使用者输入电影名称（a movie title）
创建变量`rating`，并提示使用者输入电影评级（the rating of the movie）
创建空的`movies` 散列（包含电影名称和电影评级）（movie/rating pair）
测试添加电影名称和评级是否成功
``` ruby
# example
numbers = {}
numbers["one"] = 1
puts 3 + numbers["one"]                     # => 4

# test
movies = {}

puts "Enter a movie"                        # $ Cat
title = gets.chomp
puts "Enter a number "                      # $ 2
rating = gets.chomp
movies[title] = rating       
puts movies                                 # => {"Cat"=>"2"}
```
4. 转换类型（Not My Type）
将散列中的字符串，转换为符号`symbols`或整数`integers`
 `.to_sym`  can convert a string to a symbol  on  `title`
 `.to_i`     will convert a string to an integer on `rating`
``` ruby
movies = {}

puts "Enter a movie"                        # $ Cat
title = gets.chomp
puts "Enter a number "                      # $ 2
rating = gets.chomp
movies[title.to_sym] = rating.to_i     
puts movies                                 # => {:Cat=>2}
```

4. 优化`add`条件情景，添加 `if`/`else` (Error! Error!)
  若电影名称已存在，提示该电影已经存在。
  若不存在（ `movies[title.to_sym]` is `nil`），即可添加电影。
   `.nil?`  will return `true` if the object it's called on is `nil`, and `false` otherwise
``` ruby
# example
nil_variable = nil
age = 26

nil_variable.nil?                  # => true
age.nil?                           # => false

# test
movies = {
  StarWars: 4.8,
  Divergent: 4.7
  }

puts "What movie do you want to add?"
title = gets.chomp
if movies[title.to_sym].nil?
  puts "What's the rating? (Type a number 0 to 4.)"
  rating = gets.chomp
  movies[title.to_sym] = rating.to_i
  puts "#{title} has been added with a rating of #{rating}."
else
  puts "That movie already exists! Its rating is #{movies[title.to_sym]}."
end

# 终端输出
What movie do you want to add?                     # $ Cat
What is the rating? (Type a number 0 to 4.)        # $ 2
# => Cat has been added with a rating of 2.

What movie do you want to add?                     # => StarWars
# => That movie already exists! Its rating is 4.8.
```

5. 细化`update`,和`add`差不多
``` ruby
puts "What movie do you want to update?"
title = gets.chomp
if movies[title.to_sym].nil?
  puts "Movie not found!"
else
  puts "What's the new rating? (Type a number 0 to 4.)"
  rating = gets.chomp
  movies[title.to_sym] = rating.to_i
  puts "#{title} has been updated with new rating of #{rating}."
end

# 终端显示
What movie do you want to update?                 # $ Cat
# => Movie not found!

What movie do you want to update?                 # $ StarWars
What is the new rating? (Type a number 0 to 4.)    # $ 3
# => StarWars has been updated with new rating of 3.
```

6. 细化 `display`
``` ruby
movies = {
  Memento: 3,
  Primer: 4,
  Ishtar: 1
}

movies.each do |movie, rating|
  puts "#{movie}: #{rating}"
end

# => Memento: 3
# => Primer: 4
# => Ishtar: 1
```

7. 细化`delete`
``` ruby
movies = {
  Memento: 3,
  Primer: 4,
  Ishtar: 1
}
puts "What movie do you want to delete?"
title = gets.chomp
if movies[title.to_sym].nil?
  puts "Movie not found!"
else
  movies.delete(title.to_sym)
  puts "#{title} has been removed."
end

# 终端输出
What movie do you want to delete?		# $ Cat
# => Movie not found!

What movie do you want to delete?		# $ Memento
# => Memento has been removed.

```


---

## 参考

+ [CodeCademy](https://www.codecademy.com/learn/learn-ruby)
