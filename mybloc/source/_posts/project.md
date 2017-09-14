---
title: project
date: 2017-09-14 09:58:56
tags:
---



## 变换字体的大小写
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

##  让`"s"` 和 `"th"` 互换
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

## 隐藏输入的信息
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
words1 = text.split(" ")
print words1                            # => ["today", "is", "Monday"]

words2 = text.split("y")
print words2                            # => ["toda", " is Monda"]

words3 = text.split(",")
print words3                            # => ["today is Monday"]

# test
text = "today is Monday"
words = text.split(" ")
print words                            # => ["today", "is", "Monday"]

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

## 计算一句话内的单词出现的频率

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
