---
title: Ruby
date: 2024-04-25 09:50:25
background: bg-red-500
tags:
  - script
  - interpret
categories:
  - Programming
intro: |
  The [Ruby](https://www.ruby-lang.org/) cheat sheet is a one-page reference sheet for the Ruby programming language.
plugins:
  - copyCode
---

## Getting Started

### Install

```bash
# Debian, Ubuntu
$ sudo apt-get install ruby-full
# Windows
$ winget install RubyInstallerTeam.Ruby
$ brew install ruby # macOS
$ docker run -it --rm ruby:latest # Docker
```

### What is Gemfile and Gemfile.lock {.row-span-2}

- [Gemfile](https://bundler.io/v2.3/man/gemfile.5.html) Is the Bundler (also gem) configuration file that contains the
  project's gem list (dependencies)

```ruby
# Specify gem in the Gemfile in the project root directory
ruby '3.1.2'

source 'https://rubygems.org'
gem 'nokogiri'
gem 'rack', '~>3.0.10'
gem 'rspec', :require => 'spec'
```

Install all gems in Gemfile

```bash
$ bundle install
```

Solve the problem of Gemfile.lock inconsistency between mac for development and linux for production

```bash
bundle lock --add-platform x86_64-linux
```

### Install a specific version of a specific ruby gem

```bash
$ gem install bundler -v 2.4.20
$ gem install minitest -v 5.22.3
```

### Update gems using Bundler

```bash
# Updating a single gem using Bundler
$ bundle update nokogiri
# Use Bundler to update each gem in the Gemfile
$ bundle update
```

### Comment {.row-span-1}

```ruby
# This is a single line comments.
=begin
Multi-line
Comment
=end
puts "Hello world!"  # Inline comments for code
```

### mots réservés {.col-span-1} ### reserved words {.col-span-1}

| Reserved words | Description                                                                                                                                                                                                                                                           |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `__ENCODING__` | The script encoding of the current file<br><br>L'encodage du script du fichier actuel                                                                                                                                                                                 |
| `__LINE__`     | The line number of this keyword in the current file<br><br>Le numéro de ligne de ce mot-clé dans le fichier actuel                                                                                                                                                    |
| `__FILE__`     | The path of the current file<br><br>Le chemin du fichier actuel                                                                                                                                                                                                       |
| `BEGIN`        | Code enclosed in { } is run before the program is run<br><br>Le code inclus dans { } est exécuté avant l'exécution du programme                                                                                                                                       |
| `END`          | Code enclosed in { } is run at the end of the program<br><br>Le code inclus dans { } est exécuté à la fin du programme                                                                                                                                                |
| `alias`        | Create an alias for an existing method, operator, or global variable<br><br>Créer un alias pour une méthode, un opérateur ou une variable globale existante                                                                                                           |
| `and`          | Logical AND operator<br><br>Opérateur logique AND                                                                                                                                                                                                                     |
| `begin`        | Begin a block of code<br><br>Commencer un bloc de code                                                                                                                                                                                                                |
| `break`        | Terminate a loop<br><br>Terminer une boucle                                                                                                                                                                                                                           |
| `case`         | Compare an expression with matching `when` clauses, terminated with <br/> `end`<br><br>Comparer une expression avec `when`des clauses correspondantes, terminées par  <br>`end`                                                                                       |
| `class`        | Define a class<br><br>Définir une classe                                                                                                                                                                                                                              |
| `def`          | define a function/method<br><br>définir une fonction/méthode                                                                                                                                                                                                          |
| `defined?`     | Check if a variable or function exist<br><br>Vérifier si une variable ou une fonction existe                                                                                                                                                                          |
| `do`           | Start a block of code, terminated with the <br/> `end` keyword<br><br>Démarrer un bloc de code, terminé par le  <br>`end`mot-clé                                                                                                                                      |
| `else`         | Execute the following code if previous conditions are not met<br><br>Exécutez le code suivant si les conditions précédentes ne sont pas remplies                                                                                                                      |
| `elsif`        | Alternative condition for if expressions<br><br>Condition alternative pour les expressions if                                                                                                                                                                         |
| `end`          | End blocks of code starting with keywords like `begin`, `class`,`def`,`do`,`if`, etc.<br><br>Terminez les blocs de code commençant par des mots-clés tels que `begin`, `class`, `def`, `do`, `if`, etc.                                                               |
| `ensure`       | Always execute at the end of a block<br><br>Toujours exécuter à la fin d'un bloc                                                                                                                                                                                      |
| `false`        | Logical boolean value false<br><br>Valeur booléenne logique false                                                                                                                                                                                                     |
| `for`          | Start a `for` loop<br><br>Démarrer une `for`boucle                                                                                                                                                                                                                    |
| `if`           | Execute the code block `if` the condition is `true`<br><br>Exécutez le bloc de code, `if`la condition est`true`                                                                                                                                                       |
| `in`           | Used with `for` loop<br><br>Utilisé avec `for`la boucle                                                                                                                                                                                                               |
| `module`       | Define a module<br><br>Définir un module                                                                                                                                                                                                                              |
| `next`         | jump to the point before the evaluation of the loop condition<br><br>passer au point précédant l'évaluation de la condition de boucle                                                                                                                                 |
| `nil`          | Stand for null, invalid, or always false<br><br>Signifie nul, invalide ou toujours faux                                                                                                                                                                               |
| `not`          | Logical NOT operator<br><br>Opérateur logique NON                                                                                                                                                                                                                     |
| `or`           | Logical OR operator<br><br>Opérateur logique OU                                                                                                                                                                                                                       |
| `redo`         | Jump back to the loop condition evaluation<br><br>Revenir à l’évaluation de la condition de la boucle                                                                                                                                                                 |
| `rescue`       | Evaluate expressions after an exception is raised<br><br>Évaluer les expressions après la levée d'une exception                                                                                                                                                       |
| `retry`        | Repeat method calls when called outside `rescue`, jump to the top of the block when called inside `rescue`<br><br>Répéter les appels de méthode lorsqu'ils sont appelés à l'extérieur `rescue`, sauter au début du bloc lorsqu'ils sont appelés à l'intérieur`rescue` |
| `return`       | Return a value from a method or block<br><br>Renvoyer une valeur à partir d'une méthode ou d'un bloc                                                                                                                                                                  |
| `self`         | Refer to the current object<br><br>Se référer à l'objet actuel                                                                                                                                                                                                        |
| `super`        | Call the same-named method in the superclass<br><br>Appeler la méthode du même nom dans la superclasse                                                                                                                                                                |
| `then`         | Used as a separator with`if`,`unless`,`when`,`case`,`rescue`<br><br>Utilisé comme séparateur avec `if`, `unless`, `when`, `case`,`rescue`                                                                                                                             |
| `true`         | Logical boolean value true<br><br>Valeur booléenne logique true                                                                                                                                                                                                       |
| `undef`        | Undefine methods/functions within the current class<br><br>Indéfinir les méthodes/fonctions dans la classe actuelle                                                                                                                                                   |
| `until`        | Execute the code block until the condition is false<br><br>Exécutez le bloc de code jusqu'à ce que la condition soit fausse                                                                                                                                           |
| `when`         | Begin a clause under a `case` statement<br><br>Commencer une clause sous une `case`déclaration                                                                                                                                                                        |
| `while`        | Execute the code block while the condition is true<br><br>Exécutez le bloc de code tant que la condition est vraie                                                                                                                                                    |
| `yield`        | Execute the code block passed to a method<br><br>Exécuter le bloc de code passé à une méthode                                                                                                                                                                         |

### Operator {.row-span-7}

#### Opérateurs logiques / #### Logical Operators

- `and`
- `or`
- `not`
- `&&`
- `||`
- `!`

#### Opérateurs de bits / #### Bit operators

- `&`
- `|`
- `^`
- `~`
- `<<`
- `>>`

#### Opérateurs arithmétiques / #### Arithmetic operators

- `+`
- `-`
- `*`
- `/`
- `%`
- `**`

#### Opérateur de comparaison / #### Comparison operator

- `==`
- `!=`
- `>`
- `<`
- `>=`
- `<=`
- `<=>`
- `===`
- `eql?`
- `equal?`

#### Exemples d'opérateurs / #### Operator examples

```bash
# Addition
1 + 1   #=> 2
# Subtraction
2 - 1   #=> 1
# Multiplication
2 * 2   #=> 4
# Division
10 / 5  #=> 2
17 / 5    #=> 3, not 3.4
17 / 5.0  #=> 3.4
# Exponentiation
2 ** 2  #=> 4
3 ** 4  #=> 81
# Modulus (remainder of division)
8 % 2   #=> 0  (8 / 2 = 4; no remainder)
10 % 4  #=> 2  (10 / 4 = 2 remainder 2)
a = 10
b = 20
a == b #=> false
a != b #=> true
a > b #=> false
a < b #=> true
a >= b #=> false
a <= b #=> true

# Comparison operators
a <=> b #=> -1
c = 20
c <=> b #=> 0
c <=> a  #=> 1
# Equality used in when clauses for case statements
(1...10) === 5 #=> true
# True if the receiver and the argument have the same type and equal values
1.eql?(1.0) #=> false
c = a + b  #=> 30
c += a #=> 40
c -= a #=> 30
c *= a #=> 300
c /= a #=> 30
c %= a #=> 3
c **= a #=> 59049

# Ruby parallel assignment
a = 10
b = 20
c = 30
a, b, c = 10, 20, 30
# Ruby bitwise operators
a = 60
b = 13
# & Binary AND operator copies a bit to the result if it exists in both operands.
a & b #=> 12
# | Binary OR operator copies a bit if it exists in either operand.
a | b #=> 61
# ^ Binary XOR operator copies a bit if it is set in one operand but not both.
a ^ b #=> 49
# ~ Binary Ones Complement is unary and has the effect of 'flipping' bits.
~a
# << Binary Left Shift Operator. The left operand's value is moved
# left by the number of bits specified by the right operand.
a << 2
# >> Binary Right Shift Operator. The left operand's value is moved
# right by the number of bits specified by the right operand.
a >> 2

# Ruby logical operators
a and b #=> true.
a or b #=> true.
a && b #=> true.
(a || b) #=> true.
!(a && b) #=> false.
not(a && b) #=> false.
# Ruby ternary operator
# ? :
# If condition is true ? Then value X : Otherwise value Y
a == 10 ? puts 'Right' : puts 'Wrong'
# Ruby range operators
# .. Creates a range from the start point to the end point (inclusive)
1..10 #=> Creates a range from 1 to 10 (inclusive of 1 and 10)
# ... Creates an exclusive range from the start point to the end point
1...10 #=> Creates an exclusive range from 1 to 10
```

### Tableau de priorité des opérateurs / ### Operator precedence table

Du plus haut au plus bas, voici le tableau de priorité pour Ruby. Les opérations à priorité élevée se produisent avant les opérations à priorité faible. 

From highest to lowest, this is the precedence table for ruby. High precedence operations happen before low precedence
operations.

- !, ~, unary +
- \*\*
- unary -
- \*, /, %
- +, -
- <<, >>
- &
- |, ^
- > , >=, <, <=
- <=>, ==, ===, !=, =~, !~
- &&
- ||
- .., ...
- ?, :
- modifier-rescue
- =, +=, -=, etc.
- defined?
- not
- or, and
- modifier-if, modifier-unless, modifier-while, modifier-until
- { } blocks

### Variables and scope {.col-span-2}

| Name           | Scope             | Example                       | Explanation                                                                                                                                                                                                                          |
| -------------- | ----------------- | ----------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[a-z]` or `_` | Local             | `count = 10` or `_count = 10` | Local variables must be initialized<br><br>Les variables locales doivent être initialisées                                                                                                                                           |
| `@`            | Instance variable | `@id = []`                    | Instance variables have a "nil" value before initialization<br><br>Les variables d'instance ont une valeur « nil » avant l'initialisation                                                                                            |
| `@@`           | Class variable    | `@@name = []`                 | Class variables must be initialized<br><br>Les variables de classe doivent être initialisées                                                                                                                                         |
| `$`            | Global variable   | `$version = "0.8.9"`          | Global variables have a "nil" value before initialization<br><br>Les variables globales ont une valeur « nil » avant l'initialisation                                                                                                |
| `[A-Z]`        | Constant          | `PI = 3.14`                   | Constant variables must be initialized, you can change constants, but you will receive a warning<br><br>Les variables constantes doivent être initialisées, vous pouvez modifier les constantes, mais vous recevrez un avertissement |

Il existe cinq types de variables différents. Le premier caractère détermine la plage. Pour en savoir plus sur les variables, consultez [le Guide de l'utilisateur](https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/) cap 19,20,21,22,23 [Variables et constantes prédéfinies](https://ruby-doc.org/docs/ruby-doc-bundle/Manual/man-1.4/variable.html)

There are five different types of variables. The first character determines the range To read in deap about variables
check [User Guide](https://ruby-doc.org/docs/ruby-doc-bundle/UsersGuide/rg/) cap 19,20,21,22,23
[Pre-Defined Variables and Constants](https://ruby-doc.org/docs/ruby-doc-bundle/Manual/man-1.4/variable.html)

### Vérifier la portée d'une variable / ### Check the scope of a variable

```ruby
defined? count
"local-variable"
defined? @id
"instance-variable"
defined? @@name
"class variable"
defined? $version
"global-variable"
defined? PI
"constant"
```

### Types de données {.col-span-2} / ### Data Types {.col-span-2}

| -         | -                            | -                                                  | -                                                                                                               |
| :-------- | :--------------------------- | :------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------- |
| Type      | Example                      | Class                                              | Documentation                                                                                                   |
| `Integer` | a = 17                       | a.class > Integer <br>a.class.superclass > Numeric | [#](<(https://ruby-doc.org/3.3.1/Integer.html)>)                                                                |
| `Float`   | a = 87.23                    | a.class > Float <br>a.class.superclass > Numeric   | [#](https://ruby-doc.org/3.3.1/Float.html)                                                                      |
| `String`  | a = "Hello universe"         | a.class > String                                   | [#](https://ruby-doc.org/3.3.1/String.html)                                                                     |
| `Array`   | a = [12, 34]                 | a.class > Array                                    | [#](https://ruby-doc.org/3.3.1/Array.html)                                                                      |
| `Hash`    | a = {type: "tea", count: 10} | a.class > Hash                                     | [#](https://ruby-doc.org/3.3.1/Hash.html)                                                                       |
| `Boolean` | a = false<br>a = true        | a.class > FalseClass <br>a.class > TrueClass       | [TrueClass](https://ruby-doc.org/3.3.1/TrueClass.html) [FalseClass](https://ruby-doc.org/3.3.1/FalseClass.html) |
| `Symbol`  | a = :status                  | a.class > Symbol                                   | [#](https://ruby-doc.org/3.3.1/Symbol.html)                                                                     |
| `Range`   | a = 1..3                     | a.class > Range                                    | [#](https://ruby-doc.org/3.3.1/Range.html)                                                                      |
| `Nil`     | a = nil                      | a.class > NilClass                                 | [#](https://ruby-doc.org/3.3.1/NilClass.html)                                                                   |

[further reading](https://www.digitalocean.com/community/tutorials/understanding-data-types-in-ruby)

### Vérifier le type de données / ### Check data type

```ruby
# Both are synonyms
a = 37
a.kind_of? Integer
# true
a.is_a? Integer
# true
```

### Symbol

```ruby
week_days = {sunday: 11, monday: 222}
```

### Méthodes utiles pour les entiers / ### Integer useful methods

```ruby
2.even?
# true
3.even?
# false
```

### Gamme / ### Range

`..`Utilisé pour créer des plages inclusives

`..` Used to create inclusive ranges

```ruby
range = 1..10
range.to_a
# output => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

`...`Utilisé pour créer des gammes exclusives

`...` Used to create exclusive ranges

```ruby
range = 1...10
range.to_a
# output => [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

quelques méthodes utiles

some useful methods

| Method name | Output                                |
| :---------- | :------------------------------------ |
| `cover?`    | `(1..5).cover?(5)` => `true`          |
| `end`       | `('a'..'z').end` => `"z"`             |
| `first`     | `(1..5).first` => `1`                 |
| `first(3)`  | `('A'..'Z').first(2)` => `["A", "B"]` |
| `eql?`      | `((0..2).eql?(0..5)` => `false`       |

### Utilisation `step`à portée / ### Using `step` in Range

```ruby
(1..20).step(2) { |number| puts "#{number}"}
# output
# 1
# 3
# 5
# 7
# 9
# 11
# 13
# 15
# 17
# 19
```

## Contrôle de flux Ruby / ## Ruby Flow control

### if

```ruby
num = 2
puts 'two' if num == 2
```

Si la condition est vraie, exécutez le code

If the condition is true, execute the code

### si sinon si sinon / ### if elsif else

```ruby
temp = 19
if temp >= 25
  puts "hot"
elsif temp < 25 && temp >= 18
  puts "normal"
else
  puts "cold"
end
# output => normal
```

### sauf si / ### unless

```ruby
# Unless contrary to if , evaluates when the statement is false
name = "rob"
# if name != "bob"
unless name == "bob"
  puts "hello stranger"
else
  puts "hello bob"
end
# output => hello stranger
num = 6
puts 'not two' unless num == 2
# output => not two
```

### case {.row-span-2}

```ruby
# case returns the value of the last expression executed
case input
# Check for an integer, 19
when 19
  puts "It's 19"
  # 检查一个确切的字符串，“Zaman”
when "Zaman"
  puts "Hi Zaman"
when 7..11
  puts "It's between 7 and 11"
  # Check multiple values, "coffee"
when "tea", "coffee"
  puts "Happy days"
end
```

### case(syntaxe courte) / ### case( short syntax )

```ruby
case input
  when 19 then puts "It's 19"
end
```

### cas (échec facultatif) / ### case( Optional failure )

```ruby
case input
  when 19 then puts "It's 19"
else
  puts "It's not 19"
end
```

### case( Obtenir la valeur de retour ) / ### case( Get return value )

```ruby
marks = 86
result = case marks
        when 0..49 then "Fail"
        when 50..64 then "Pass"
        when 65..74 then "Credit"
        when 75..84 then "Distinction"
        when 85..100 then "High Distinction"
        else "Invalid marks"
        end

puts result
# High Distinction
```

## Chaîne / ## String

### Interpolation de chaîne / ### String interpolation

```ruby
name = "World"
puts "Hello #{name}"
puts "The total is #{1+1}"
# "the total is 2"
```

L'interpolation de chaînes vous permet de combiner des chaînes ensemble

String interpolation allows you to combine strings together

### Extraire la sous-chaîne / ### Extract substring

```ruby
string = "abc123"
string[0,3]
# "abc"
string[3,3]
# "123"
string[0..-2]
# "abc12"
#remove or replace the substring
string[0..2] = ""
puts string
# "123"
```

Une sous-chaîne est une petite partie d'une chaîne, ce qui est utile si vous ne voulez que cette partie spécifique, comme le début, le milieu ou la fin

A substring is a small part of a string, which is useful if you only want that specific part, like the beginning,
middle, or end

### Convertir une chaîne en minuscules ou en majuscules / ### Convert a string to lowercase or uppercase

```ruby
"HELLO World".downcase  # "hello world"
"hello worlD".upcase    # "HELLO WORLD"
"hEllo wOrlD".capitalize # "Hello world"
"hEllo WOrlD".swapcase  # "HeLLO woRLd"
```

### méthodes utiles {.col-span-3} / ### useful methods {.col-span-3}

| Function Name                  | Output                                                                                                | Note                                                                                                                                                                                                                                                                                                                                                                                                                  |
| :----------------------------- | :---------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| length or size                 | `"HELLO World".length` => `11` <br> `"HELLO World".size` => `11`                                      | Returns the length of the string<br><br>Renvoie la longueur de la chaîne                                                                                                                                                                                                                                                                                                                                              |
| reverse                        | `"hello worlD".reverse` => `"Dlrow olleh"`                                                            | Returns the reversed string<br><br>Renvoie la chaîne inversée                                                                                                                                                                                                                                                                                                                                                         |
| include? other_str             | `"hEllo wOrlD".include? "w"` => `true`                                                                | Returns true if the string or character exists, otherwise returns false<br><br>Renvoie vrai si la chaîne ou le caractère existe, sinon renvoie faux                                                                                                                                                                                                                                                                   |
| gsub(pattern, replacement)     | `"hEllo wOrlD".gsub(" ", "_")` => `"hEllo_wOrlD"`                                                     | gsub or global substitute replaces one or more strings with the provided string<br><br>gsub ou global substitute remplace une ou plusieurs chaînes par la chaîne fournie                                                                                                                                                                                                                                              |
| gsub(pattern, hash)            | `"organization".gsub("z", 'z' => 's')` => `"organisation"`                                            | gsub or global substitute replaces one or more strings with the provided hash<br><br>gsub ou global substitute remplace une ou plusieurs chaînes par le hachage fourni                                                                                                                                                                                                                                                |
| gsub(pattern) {\|match\|block} | `"Price of the phone is 1000 AUD".gsub(/\d+/) {\| s\| '$'+s }`<br>`"Price of the phone is $1000 AUD"` | gsub or global substitute replaces one or more strings with the provided block<br><br>gsub ou global substitute remplace une ou plusieurs chaînes par le bloc fourni                                                                                                                                                                                                                                                  |
| strip                          | `" hEllo WOrlD ".strip` <br> `"hEllo WOrlD"`                                                          | It will remove (trim) any leading and trailing characters: null (“\x00”), horizontal tab (“\t”), newline (\n), vertical tab (“\v”), form feed (f), carriage return(\r), space (" ")<br><br>Il supprimera (coupera) tous les caractères de début et de fin : null (« \x00 »), tabulation horizontale (« \t »), nouvelle ligne (\n), tabulation verticale (« \v »), saut de page (f), retour chariot (\r), espace (« ») |
| prepend                        | `a = "world" <br> a.prepend("hello ")` <br> `"hello world"`                                           | Adds the string before another string<br><br>Ajoute la chaîne avant une autre chaîne                                                                                                                                                                                                                                                                                                                                  |
| insert                         | `a = "hello" <br> a.insert(a.length, " world")` <br> `"hello world"`                                  | Inserts the string at a specific position<br><br>Insère la chaîne à une position spécifique                                                                                                                                                                                                                                                                                                                           |
| start_with?                    | `string = "ruby programming"` <br> `string.start_with? "ruby"` <br> `true`                            | Checks if the string starts with a specific prefix<br><br>Vérifie si la chaîne commence par un préfixe spécifique                                                                                                                                                                                                                                                                                                     |
| end_with?                      | `string = "ruby programming"` <br> `string.end_with? "ruby"` <br> `false`                             | Checks if the string ends with a specific prefix<br><br>Vérifie si la chaîne se termine par un préfixe spécifique                                                                                                                                                                                                                                                                                                     |
| delete_suffix                  | `string = "sausage is expensive"` <br> `string.delete_suffix(" is expensive")` <br> `"sausage"`       | Deletes the suffix from the string<br><br>Supprime le suffixe de la chaîne                                                                                                                                                                                                                                                                                                                                            |
| delete_prefix                  | `string = "sausage is expensive"` <br> `string.delete_prefix("sausage")` <br> `" is expensive"`       | Deletes the prefix from the string<br><br>Supprime le préfixe de la chaîne                                                                                                                                                                                                                                                                                                                                            |
| split                          | `string = "a b c d" <br> string.split` <br> `["a", "b", "c", "d"]`                                    | Converts the string into an array of characters<br><br>Convertit la chaîne en un tableau de caractères                                                                                                                                                                                                                                                                                                                |
| join                           | `arr = ['a', 'b', 'c'] <br> arr.join` => `"abc"`                                                      | Converts an array into a string<br><br><br>Convertit un tableau en chaîne                                                                                                                                                                                                                                                                                                                                             |
| to_i                           | `a = "49" <br> a.to_i` => `49`                                                                        | Converts the string into an integer<br><br>Convertit la chaîne en un tableau de caractères                                                                                                                                                                                                                                                                                                                            |
| chop                           | `"abcd?".chop("?")` => `"abcd"`                                                                       | Deletes the last character from the string<br><br>Supprime le dernier caractère de la chaîne                                                                                                                                                                                                                                                                                                                          |
| count                          | `str = "aaab" <br> str.count("a")` <br> `3`                                                           | Counts the characters in the string<br><br>Compte les caractères dans la chaîne                                                                                                                                                                                                                                                                                                                                       |
| to_f                           | `a = "49"` <br> `a.to_f` <br> `49.0`                                                                  | Converts the string into a floating point number<br><br>Convertit la chaîne en un nombre à virgule flottante                                                                                                                                                                                                                                                                                                          |
| to_sym                         | `a = "key"` <br> `a.to_sym` <br> `:key`                                                               | Converts the string into a symbol<br><br>Convertit la chaîne en symbole                                                                                                                                                                                                                                                                                                                                               |
| match                          | `"abcd?".match(/ab/)` => `#<MatchData "ab">`                                                          | Converts the pattern into a regular expression and calls its match method on the string<br><br>Convertit le modèle en une expression régulière et appelle sa méthode de correspondance sur la chaîne                                                                                                                                                                                                                  |
| empty?                         | `"hello".empty?` => `false`                                                                           | Returns true if the length of the string is zero<br><br>Renvoie vrai si la longueur de la chaîne est zéro                                                                                                                                                                                                                                                                                                             |
| squeeze                        | `"Booook".squeeze` => `"Bok"`                                                                         | Returns a copy of the string where runs of the same character are replaced by a single character<br><br>Renvoie une copie de la chaîne où les séquences du même caractère sont remplacées par un seul caractère                                                                                                                                                                                                       |
| \*                             | `puts "Ruby " * 4` => `Ruby Ruby Ruby Ruby`                                                           | Returns the concatenation of multiple copies of self<br><br>Renvoie la concaténation de plusieurs copies de soi                                                                                                                                                                                                                                                                                                       |
| +                              | `"sammy " + "shark"` => `"sammyshark"`                                                                | Returns the concatenation of self and the given other string<br><br>Renvoie la concaténation de soi et de l'autre chaîne donnée                                                                                                                                                                                                                                                                                       |
| eql?                           | `s = 'foo'` => `true` <br> `s.eql?('foo')` => `true`                                                  | Returns true if the objects have the same length and content; false otherwise<br><br>Renvoie true si les objets ont la même longueur et le même contenu ; false sinon                                                                                                                                                                                                                                                 |

## Méthodes / ## Methods

### Déclarer une méthode {.row-span-3} / ### Declare a method {.row-span-3}

```ruby
def method_name(parameter1, parameter2)
    puts "#{parameter1} #{parameter2}"
    parameter1 + parameter2
end
```

---

```ruby
res = method_name(20, 10)
# output => 30
def method_name(parameter1, parameter2)
    puts "#{parameter1} #{parameter2}"
    return parameter1 + parameter2
end
# output => 30
```

### Méthode d'appel / ### Call method

```ruby
res = method_name(parameter1, parameter2)
# Methods can be called without parentheses
res = method_name parameter1, parameter2
```

### Méthode de classe {.row-span-4} / ### Class method {.row-span-4}

Class methods are class-level methods. There are multiple ways to define class methods

Les méthodes de classe sont des méthodes de niveau classe. Il existe plusieurs façons de définir des méthodes de classe

```ruby
class Mobile
    def self.ring
        "ring ring ring..."
    end
end

Mobile.ring
```

---

```ruby
class Mobile
    def Mobile.ring
        "ring ring ring..."
    end
end
Mobile.ring
```

---

```ruby
class Mobile
    class << self
    def ring
        "ring ring ring..."
       end
    end
end
Mobile.ring
```

Class methods are instance methods of class objects. When a new class is created, an object of type "Class" is
initialized and assigned to a global constant (in this case Mobile)

Les méthodes de classe sont des méthodes d'instance d'objets de classe. Lorsqu'une nouvelle classe est créée, un objet de type « Class » est initialisé et affecté à une constante globale (dans ce cas Mobile)

```ruby
Mobile = Class.new do
    def self.ring
        "ring ring ring..."
    end
end
Mobile.ring
```

```ruby
Mobile = Class.new
class << Mobile
    def ring
        "ring ring ring..."
    end
end
Mobile.ring
```

### Utiliser un autre paramètre comme valeur par défaut  / ### Use another parameter as default value

```ruby
def method_name(num1, num2 = num1)
    return num1 + num2
end
res = method_name(10)
# output => 20
```

### Définir les valeurs par défaut pour les paramètres de la méthode / ### Define default values for method parameters

```ruby
def method_name(parameter1, parameter2, type = "ADD")
    puts "#{parameter1} #{parameter2}"
    return parameter1 + parameter2 if type == "ADD"
    return parameter1 - parameter2 if type == "SUB"
end
res = method_name(20, 10)
# output => 30
```

### Transmettre des arguments de longueur variable aux paramètres de la méthode / ### Pass variable length arguments to method parameters

```ruby
def method_name(type, *values)
    return values.reduce(:+) if type == "ADD"
    return values.reduce(:-) if type == "SUB"
end
numbers = [2, 2, 2, 3, 3, 3]
res = method_name("ADD", *numbers)
# output => 15
res = method_name("SUB", *numbers)
# output => -11
# Or you can provide a value like this
res = method_name("ADD", 2, 2, 2, 3, 3, 3)
# output => 15
```

### Modifier l'objet / ### Modify object

```ruby
a = ["Drama", "Mystery", "Crime",
"Sci-fi", "Disaster", "Thriller"]
a.sort
puts a
# We did not modify the object
# Drama
# Mystery
# Crime
# Sci-fi
# Disaster
# Thriller
a.sort!
puts a
# Modify object
# Crime
# Disaster
# Drama
# Mystery
# Sci-fi
# Thriller
```

When you want to modify the object, use `!` after the method

Lorsque vous souhaitez modifier l'objet, utilisez `!`après la méthode

### Méthode booléenne / ### Boolean method

In ruby, methods ending with a question mark (?) are called boolean methods, which return `true` or `false`

En Ruby, les méthodes se terminant par un point d'interrogation (?) sont appelées méthodes booléennes, qui renvoient `true`ou`false`

```ruby
"some text".nil?
# false
nil.nil?
# true
```

You can have your own boolean method

Vous pouvez avoir votre propre méthode booléenne

```ruby
def is_vowel?(char)
    ['a','e','i','o','u'].include? char
end
is_vowel? 'a'
# true
is_vowel? 'b'
# false
```

## Blocs / ## Blocks

### Exemple de bloc / ### Block example

```ruby
# return value
def give_me_data
    data = yield
    puts "data = #{data}"
end
give_me_data { "Big data" }
# output => data = Big data
```

The code between `do` and `end` (for multiple lines) or curly braces `{` and `}` (for a single line) is called a block,
and they can define multiple parameters between two pipes `( |arg1, arg2|)`

Le code entre `do`et `end`(pour plusieurs lignes) ou les accolades `{`et `}`(pour une seule ligne) est appelé un bloc, et ils peuvent définir plusieurs paramètres entre deux tuyaux`( |arg1, arg2|)`

### Bloc à une seule ligne / ### Single line block

```ruby
salary = [399, 234, 566, 533, 233]
salary.each { |s| puts s }
# puts s = block body
# |s| = block arguments
```

### Bloc multiligne / ### Multi-line block

```ruby
salary.each do |s|
    a = 10
    res = a * s
    puts res
end
# Block
# a = 10
# res = a * s
# puts res
# block parameters
# |s|
```

Blocks can be passed as method parameters or associated with method calls. block returns the last evaluated statement

Les blocs peuvent être transmis en tant que paramètres de méthode ou associés à des appels de méthode. Le bloc renvoie la dernière instruction évaluée

### Passer implicitement un bloc / ### Implicitly passing a block

```ruby
def give_me_data
    puts "I am inside give_me_data method"
    yield
    puts "I am back in give_me_data method"
end

give_me_data { puts "Big data" }

# output
# I am inside give_me_data method
# Big data
# I am back in give_me_data method
```

### Appelé plusieurs fois / ### Called multiple times

```ruby
def give_me_data
    yield
    yield
    yield
end

give_me_data { puts "Big data" }

# output
# Big data
# Big data
# Big data
```

### Appelé avec des paramètres de bloc / ### Called with block parameters

```ruby
def give_me_data
    yield 10
    yield 100
    yield 30
end

give_me_data { |data| puts "Big data #{data} TB" }

# output
# Big data 10 TB
# Big data 100 TB
# Big data 30 TB
```

### Appelé avec plusieurs paramètres de bloc / ### Called with multiple block parameters

```ruby
def give_me_data
    yield "Big data", 10, "TB"
    yield "Big data", 100, "GB"
    yield "Big data", 30, "MB"
end

give_me_data { |text, data, unit| puts "#{text} #{data} #{unit}" }

# output
# Big data 10 TB
# Big data 100 GB
# Big data 30 MB
```

### Le bloc tentera de revenir du contexte actuel / ### Block will attempt to return from the current context

```ruby
give_me_data
    puts "I'm inside the give_me_data method"
end

def test
  puts "I'm inside the test method"
  give_me_data { return 10 } # Code returns from here
  puts "I am back in test method"
end

return_value = test

# output
# I'm inside the test method
# I'm inside the give_me_data method
# 10
```

### Transmettez le bloc explicitement en utilisant le paramètre & / ### Pass the block explicitly by using the & parameter

```ruby
def give_me_data(&block)
    block.call
    block.call
end

give_me_data { puts "Big data" }

# output
# Big data
# Big data
```

### Vérifiez si le bloc est donné / ### Check if block is given

```ruby
def give_me_data
    yield
end

give_me_data

# output
# LocalJumpError: no block given (yield)
```

### Façons de gérer les exceptions et de rendre les blocs facultatifs / ### Ways to handle exceptions and make blocks optional

```ruby
def give_me_data
    return "no block" unless block_given?
    yield
end

give_me_data { puts "Big data" }
give_me_data

# output
# Big data
```

## Procédures / ## Procs

### Procédures / ### Procs

```ruby
p = Proc.new { puts "Hello World" }

def give_me_data(proc)
    proc.call
end

give_me_data p

# output
# Hello World
```

proc is like a block that can be stored in a variable

proc est comme un bloc qui peut être stocké dans une variable

### tout paramètre {.col-span-2} / ### any parameter {.col-span-2}

```ruby
p = Proc.new { |count| "Hello World " * count }

def give_me_data(proc)
    proc.call 5, 2
end

give_me_data p

# output
# "Hello World Hello World Hello World Hello World Hello World "
```

### proc tentera de revenir du contexte actuel / ### proc will attempt to return from the current context

```ruby
p = Proc.new { return 10 }
p.call
# output
LocalJumpError: unexpected return
```

### Impossible de revenir à partir du contexte de niveau supérieur / ### Cannot return from top-level context

```ruby
def give_me_data
    puts "I'm inside the give_me_data method"
    p = Proc.new { return 10 }
    p.call # Code returns from here
    puts "I am back in give_me_data method"
end

return_value = give_me_data
puts return_value

# output
# I'm inside the give_me_data method
# 10
```

## Lambdas / ## Lambdas

### Déclarer un lambda{.row-span-2} / ### Declare a lambda{.row-span-2}

```ruby
l = lambda { puts "Hello World" }
# shorthand
l = -> { puts "Hello World" }
# transfer lambda
l.call
# output => Hello World
```

There are multiple ways to call a lambda

Il existe plusieurs façons d'appeler un lambda

```ruby
l.()
l[]
```

### arguments stricts / ### strict arguments

```ruby
l = -> (count) { "Hello World " * count }
l.call 5
# output
# "Hello World Hello World Hello World Hello World Hello World "
l.call 5, 2
# output
wrong number of arguments (given 2, expected 1)
```

### déclarer un lambda dans le bloc {.row-span-2} / ### declare a lambda in block {.row-span-2}

```ruby
def give_me_data
    puts "I am inside give_me_data method"
    l = -> { return 10 }
    l.call
    puts "I am back in give_me_data method"
end

return_value = give_me_data
puts return_value

# output
# I am inside give_me_data method
# I am back in give_me_data method
# nil # because puts return nil
```

### les lambdas sont renvoyés par le lambda lui-même, tout comme les méthodes normales / ### lambdas are returned from the lambda itself, just like regular methods

```ruby
l = -> { return 10 }
l.call

# output => 10
```

## Tableau / ## Array

### Initialiser un tableau vide / ### Initialize an empty array

```ruby
array = Array.new   #=> []
# or
array = []
```

### Tableau contenant des objets de différents types / ### Array containing objects of different types

```ruby
array = [1, "two", 3.0]
#=> [1, "two", 3.0]
```

### Remplir le tableau avec la taille initiale et les objets par défaut {.row-span-2} / ### Fill array with initial size and default objects {.row-span-2}

```ruby
numbers = Array.new(3)
#=> [nil, nil, nil]
numbers = Array.new(3, 7)
#=> [7, 7, 7]
numbers = Array.new(3, true)
#=> [true, true, true]
numbers = []
numbers.fill(7, 0..2)   #=> [7, 7, 7]
```

### tableau de différents hachages {.col-span-2} / ### array of different hashes {.col-span-2}

```ruby
array_with_hashes = Array.new(2) { {} } #=> [{}, {}]
array_with_hashes[0][:name] = "Bob"
array_with_hashes[0][:id] = 10          #=> [{:name=>"Bob", :id=>10}, {}]
```

### Tableau à deux dimensions / ### Two-dimensional array

```ruby
temperature_data = [
              ["A908", 38],
              ["A909", 37],
              ["A910", 38],
          ]
temperature_data[0]    #=> ["A908", 38]
temperature_data[0][0] #=> "A908"
temperature_data[0][1] #=> 38
```

### indice de tableau / ### array index

```ruby
str_array = [
  "This", "is", "a", "small", "array"
]
str_array[0]            #=> "This"
str_array[1]            #=> "is"
str_array[4]            #=> "array"
```

### indice négatif / ### negative index

```ruby
str_array = [
  "This", "is", "a", "small", "array"
]
# Index -1 represents the last element
str_array[-1]        #=> "array"
# Index -2 represents the second to last element
str_array[-2]        #=> "small"
str_array[-6]        #=> nil
```

### méthode de tableau à / ### array method at

```ruby
str_array = [
  "This", "is", "a", "small", "array"
]

puts str_array.at(0)      #=> "This"
```

### Acquisition de portée / ### Range acquisition

```ruby
arr = [1, 2, 3, 4, 5, 6]
arr[100]                  #=> nil
arr[-3]                   #=> 4
arr[2, 3]                 #=> [3, 4, 5]
arr[1..4]                 #=> [2, 3, 4, 5]
arr[1..-3]                #=> [2, 3, 4]
```

### Méthode de récupération de tableau / ### Array method fetch

```ruby
arr = ['a', 'b', 'c', 'd', 'e', 'f']
arr.fetch(100)
#=> IndexError: Index outside array bounds 100：-6...6
arr.fetch(100, "oops")    #=> "oops"
```

Out of bounds, give default value

Hors limites, donner la valeur par défaut

### Obtenir les éléments du tableau / ### Get array elements

```ruby
arr = [1, 2, 3, 4, 5, 6]

arr.first     # first value => 1
arr.last      # last value => 6
# take Returns the first n elements
arr.take(3)   #=> [1, 2, 3]
# drop after n elements have been deleted
arr.drop(3)   #=> [4, 5, 6]
```

### Ajouter de la valeur à la fin du push du tableau / ### Add value to end of array push

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.push(11)
#=> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
numbers.push(12, 13, 14)
#=> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```

### Supprimer la valeur à la fin du tableau pop / ### Delete the value at the end of the array pop

```ruby
num_array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
num_array.pop             #=> 10
num_array
#=> [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Ajouter une valeur au début du tableau sans décaler / ### Add value to beginning of array unshift

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.unshift(0)
#=> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.unshift(-3, -2, -1)
#=> [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### Récupérer et supprimer simultanément le premier élément shift / ### Retrieve and simultaneously delete the first element shift

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.shift #=> 1
numbers
#=> [2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### Supprimer l'élément à l'index spécifique delete_at / ### Remove element at specific index delete_at

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.delete_at(2) #=> 4
numbers
#=> [2, 3, 5, 6, 7, 8, 9, 10]
```

### Supprimer un élément spécifique n'importe où dans un tableau / ### Remove a specific element anywhere in an array

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.delete(2) #=> 2
numbers           #=> [3, 5, 6, 7, 8, 9, 10]
```

### Insérer une valeur à l'index donné insert {.row-span-2} / ### Insert value at given index insert {.row-span-2}

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.insert(0, 0)
#=> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.insert(0, -3, -2, -1)
#=> [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

numbers.insert(-1, 12, 13, 14)
#=> [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 13, 14]
numbers.insert(-4, 11)
#=> [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```

### Un bloc pour remplir le tableau avec des valeurs / ### A block to fill the array with values

```ruby
numbers = Array.new(10) { |n| n = n * 2 }
#=> [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

### Le remplissage des tableaux devient plus facile / ### Filling arrays becomes easier

```ruby
numbers = Array(100..110)
#=> [100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110]

# Or we can convert the range to an array
(100..110).to_a
#=> [100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110]
```

### Supprimer la valeur nulle du tableau / ### Remove nil value from array

```ruby
arr = ['foo', 0, nil, 'bar', 7, nil]
arr.compact  #=> ['foo', 0, 'bar', 7]
arr      #=> ['foo', 0, nil, 'bar', 7, nil]
arr.compact! #=> ['foo', 0, 'bar', 7]
arr      #=> ['foo', 0, 'bar', 7]
```

### Supprimer les doublons uniq / ### Remove duplicates uniq

```ruby
arr = [2, 5, 6, 556, 6, 6, 8, 9, 0, 123, 556]
arr.uniq #=> [2, 5, 6, 556, 8, 9, 0, 123]
arr # => [2, 5, 6, 556, 6, 6, 8, 9, 0, 123, 556]
arr.uniq! #=> [2, 5, 6, 556, 8, 9, 0, 123]
arr #=> [2, 5, 6, 556, 8, 9, 0, 123]
```

### Vérifier si une valeur existe dans un tableau（`include？`） / ### Check if a value exists in an array（`include？`）

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
planets.include? "Mars"
# output => true
planets.include? "Pluto"
# output => false
```

### Obtenir la taille du tableau / ### Get array size

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
planets.size
# output => 8
planets.length
# output => 8
```

You can use size or length, both are synonyms

Vous pouvez utiliser la taille ou la longueur, les deux sont synonymes

### tableau clair / ### clear array

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.clear
# output => []
```

### Obtenir le premier élément du tableau / ### Get the first element of the array

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers[0]
# or
numbers.first
# output => 1
```

### Obtenir le dernier élément du tableau / ### Get the last element of the array

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers[-1]
# or
numbers.last
# output => 10
```

### Fusionner deux tableaux / ### Merge two arrays

```ruby
a = ["tom", "mot", "otm"]
b = [2, 3, 5]
a.zip(b)
# output
# [["tom", 2], ["mot", 3], ["otm", 5]]
```

### Trier le tableau {.row-span-3} / ### Sort array {.row-span-3}

```ruby
primes = [7, 2, 3, 5]
sorted_primes = primes.sort
puts "#{sorted_primes}"
# output => [2, 3, 5, 7]
```

or in-place sort

ou tri sur place

```ruby
primes = [7, 2, 3, 5]
primes.sort!
puts "#{primes}"
# output => [2, 3, 5, 7]
```

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
planets.sort
# output
# ["Earth", "Jupiter", "Mars", "Mercury", "Neptune", "Saturn", "Uranus", "Venus"]
planets.sort_by { |p| p }
# output
# ["Earth", "Jupiter", "Mars", "Mercury", "Neptune", "Saturn", "Uranus", "Venus"]
planets.sort_by { |p| p.length }
# output
# ["Mars", "Earth", "Venus", "Saturn", "Uranus", "Neptune", "Jupiter", "Mercury"]
```

### Obtenir la valeur maximale du tableau / ### Get maximum value from array

```ruby
primes = [7, 2, 3, 5]
primes.max_by { |p| p }
# output => 7
```

### Obtenir les éléments du tableau en utilisant la plage {.row-span-2} / ### Get array elements using range {.row-span-2}

```ruby
# numbers[start..end], both index are inclusive
puts numbers[0..3]
# 1
# 2
# 3
# 4
# numbers[start..end], end index is exclusive
puts numbers[0...3]
# 1
# 2
# 3
# or numbers[start..length]
puts numbers[0, 1]
# 1
```

### Obtenir les n premiers éléments du tableau / ### Get the first n elements of the array

```ruby
primes = [7, 2, 3, 5]
primes.take(3)
# [7, 2, 3]
```

### élément d'accès / ### access element

```ruby
primes = [7, 2, 3, 5]
primes.fetch(3)
# 5
# Fetch will throw an error if the element does not exist
primes.fetch(10)
# (index 10 outside of array bounds: -4...4)
# or get an default value
primes.fetch(10, -1)
# -1
```

### Supprimer les n premiers éléments / ### Delete first n elements

```ruby
primes = [7, 2, 3, 5]
primes.drop(3)
# [5]
```

### Supprimer le premier élément / ### Delete the first element

```ruby
primes = [7, 2, 3, 5]
primes.shift
# [2, 3, 5]
```

### Supprimer le dernier élément / ### Remove last element

```ruby
primes = [7, 2, 3, 5]
primes.pop
# [7, 2, 3]
```

### Supprimer l'élément avec l'index / ### Delete element with index

```ruby
primes = [7, 2, 3, 5]
primes.delete_at(-1)
# [7, 2, 3]
```

### Supprimer toutes les occurrences des éléments / ### Remove all occurrences of elements

```ruby
primes = [7, 2, 3, 5, 5]
primes.delete(5)
# [7, 2, 3]
```

### chaque {.row-span-3} / ### each {.row-span-3}

```ruby
# When you have single line blocks
salary = [399, 234, 566, 533, 233]
salary.each { |s| puts s }
# output
# 399
# 234
# 566
# 533
# 233
```

When you have a multi-line block, you can replace the curly braces `{}` with `do` and `end`

Lorsque vous avez un bloc multiligne, vous pouvez remplacer les accolades `{}`par `do`et`end`

```ruby
salary.each do |s|
  a = 10
  res = a * s
  puts res
end
# output
# 3990
# 2340
# 5660
# 5330
# 2330
```

Or you can do the same thing using braces {} and semicolon as separator instead of newline

Ou vous pouvez faire la même chose en utilisant des accolades {} et un point-virgule comme séparateur au lieu d'une nouvelle ligne

```ruby
salary.each { |s| a = 10 ; res = a * s ; puts res }
```

### chacun_avec_index / ### each_with_index

```ruby
salary = [399, 234, 566, 533, 233]
salary.each_with_index { |value, index| puts "#{index} #{value}" }
# output
# 0 399
# 1 234
# 2 566
# 3 533
# 4 233
```

### chaque_index / ### each_index

```ruby
salary = [399, 234, 566, 533, 233]
salary.each_index { |i| puts i}
# output
# 0
# 1
# 2
# 3
# 4
```

### carte / ### map

```ruby
salary = [399, 234, 566, 533, 233]
salary.map { |s|  s * 10  }
# return
# [3990, 2340, 5660, 5330, 2330]
# On the other hand, each returns the original value
salary = [399, 234, 566, 533, 233]
salary.each { |s|  s * 10  }
# return
# [399, 234, 566, 533, 233]
```

### collecter / ### collect

```ruby
salary = [399, 234, 566, 533, 233]
salary.collect { |s| s > 400 }
# output
# [false, false, true, true, false]
```

### pour / ### for

```ruby
for value in [2, 3, 5, 7]
    puts value
end
```

### chaque_avec_objet {.col-span-2} / ### each_with_object {.col-span-2}

```ruby
colors = [
  {color: "red", count: 3}, {color: "red", count: 5}, {color: "black", count: 4}
]
colors.each_with_object(Hash.new(0)) { |color, hash| hash["color_"+color[:color]] = color[:color].upcase; hash["count_"+color[:color]] += color[:count] }
# output
{"color_red"=>"RED", "count_red"=>8, "color_black"=>"BLACK", "count_black"=>4}

[1, 2, 3].each_with_object(0) { |number, sum| sum += number}
# output
# 0
# Because 0 is immutable, and since the initial object is 0, the method returns 0
```

### alors que / ### while

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
index = 0
while index < planets.size
    puts "#{planets[index]}"
    index += 1
end
```

---

```ruby
a = 1
star = '*'
while a <= 10
    puts star
    star += '*'
    a += 1
end
```

### faire pendant / ### do while

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
index = 0
loop do
    puts "#{planets[index]}"
    index += 1
    break if planets[index] == "Mars" or index > planets.size
end
```

### jusqu'à / ### until

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
index = planets.size - 1
until index < 0
    puts "#{planets[index]}"
    index -= 1
end
```

```ruby
a = 1
star = '*'
until star.length > 10
    puts star
    star += '*'
    a += 1
end
```

### fois / ### times

```ruby
10.times { puts "#{rand(1..100)}"}
# output
# will print 10 random numbers
```

Just because you can doesn't mean you should iterate over an array like this

Ce n'est pas parce que vous le pouvez que vous devez parcourir un tableau comme celui-ci

```ruby
data_sample = [2, 3, 5, 7]
data_sample.size.times { |index| puts "#{data_sample[index]}" }
# output
# 2
# 3
# 5
# 7
```

### jusqu'à / ### upto

```ruby
data_sample = [2, 3, 5, 7]
0.upto((data_sample.size - 1) / 2) { |index| puts "#{data_sample[index]}" }
# output
# 2
# 3
```

### jusqu'à / ### downto

```ruby
data_sample = [2, 3, 5, 7]
(data_sample.size - 1).downto(data_sample.size / 2) { |index| puts "#{data_sample[index]}" }
# output
# 7
# 5
```

### étape {.row-span-2} / ### step {.row-span-2}

```ruby
1.step(20, 2) { |number| puts "#{number}"}
# output
# 1
# 3
# 5
# 7
# 9
# 11
# 13
# 15
# 17
# 19
```

---

```ruby
19.step(1, -2) { |number| puts "#{number}"}
# output
# 19
# 17
# 15
# 13
# 11
# 9
# 7
# 5
# 3
# 1
```

### injecter {.row-span-2} / ### inject {.row-span-2}

```ruby
numbers = [2, 2, 2, 2, 2]
numbers.inject{ |res, n| res + n }
# The output is the sum of all numbers
# If no initial value is set for res, the first element of the array is used as the initial value of res.
#10
# Now set the value of res to 11
numbers = [2, 2, 2, 2, 2]
numbers.inject(11) { |res, n| res + n }
# so 11 + 2, 13 + 2, 15 + 2, 17 + 2 and 19 + 2
# 21
# using symbol
numbers = [2, 2, 2, 2, 2]
numbers.inject(:+)
# output
# 10
```

Use initial values and symbols

Utiliser les valeurs et les symboles initiaux

```ruby
numbers = [2, 2, 2, 2, 2]
numbers.inject(11, :+)
# output
# 21
```

### réduire / ### reduce

```ruby
numbers = [2, 2, 2, 2, 2]
numbers.reduce(11, :+)
# output
# 21
```

### détecter / ### detect

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
planets.detect { |name| name.start_with?("E") and name.end_with?("h") }
# output
# Earth
salary = [399, 234, 566, 533, 233]
salary.detect { |s| s > 1000 }
# output
# nil
```

### trouver / ### find

```ruby
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
planets.find { |name| name.start_with?("E") and name.end_with?("h") }
# output
# Earth
```

### sélectionner / ### select

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.select { |n| n % 2 == 0 }
# Now you have an even array
# [2, 4, 6, 8, 10]
# If there are no values that satisfy your logic, return an empty array
[1, 1, 1].select { |n| n % 2 == 0 }
# no even numbers
# []
```

### rejeter / ### reject

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.reject { |n| n % 2 == 0 }
# Reject if the number is even, so now we have an odd array
# [1, 3, 5, 7, 9]
```

### garder_si / ### keep_if

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.keep_if { |n| n % 2 == 0 }
# numbers Array contains only even numbers
# [2, 4, 6, 8, 10]
```

### supprimer_si / ### delete_if

```ruby
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
numbers.delete_if { |n| n % 2 == 0 }
# numbers Array contains only odd numbers
# [1, 3, 5, 7, 9]
```

### laisser tomber_pendant / ### drop_while

```ruby
numbers = [1, 2, 3, 1, 2, 3, 0]
numbers.drop_while { |n| n < 3 }
# is 3 less than 3, returns false, so delete 1, 2
# [3, 1, 2, 3, 0]
```

### inverser_chaque / ### reverse_each

```ruby
words = %w[first second third fourth fifth sixth]
str = ""
words.reverse_each {|word| str += "#{word} "}
p str #=> "sixth fifth fourth third second first "
```

## méthode énumérable booléenne / ## boolean enumerable method

### méthode booléenne énumérable {.row-span-2} / ### boolean enumerable method {.row-span-2}

| Name       | When to use / Quand l'utiliser                                                                                                                                                  |
| :--------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `all?`     | When you want to check if all elements meet your condition<br><br>Lorsque vous souhaitez vérifier si tous les éléments répondent à votre condition<br>                          |
| `any?`     | When you want to check if at least one item meets your condition<br><br>Lorsque vous souhaitez vérifier si au moins un article répond à votre condition                         |
| `one?`     | When you want to check if one element meets your requirement<br><br>Lorsque vous souhaitez vérifier si un élément répond à vos exigences                                        |
| `none?`    | When you want to check if no item meets your condition, the opposite of?<br><br>Lorsque vous souhaitez vérifier si aucun article ne répond à votre condition, le contraire de ? |
| `empty?`   | When you want to check if an object is empty<br><br>Lorsque vous souhaitez vérifier si un objet est vide                                                                        |
| `include?` | When you want to check if an element exists in the object<br><br>Lorsque vous souhaitez vérifier si un élément existe dans l'objet                                              |

### tous? / ### all?

```ruby
[2, 4, 6, 8, 10].all? { |num| num % 2 == 0 }
# true
[1, 4, 6, 8, 10].all? { |num| num % 2 == 0 }
# false
```

### n'importe lequel? / ### any?

```ruby
[1, 3, 5, 7, 10].any? { |num| num % 2 == 0 }
# true
[1, 3, 5, 7, 19].any? { |num| num % 2 == 0 }
# false
```

### un? / ### one?

```ruby
[1, 3, 2, 5, 7].one? { |num| num % 2 == 0 }
# true
[1, 3, 2, 5, 4].one? { |num| num % 2 == 0 }
# false
```

### aucun? / ### none?

```ruby
[1, 3, 5, 7, 9].none? { |num| num % 2 == 0 }
# true
[2, 3, 5, 7, 9].none? { |num| num % 2 == 0 }
# false
```

### vide? / ### empty?

```ruby
[].empty?
# true
[1, 3, 5, 7, 9].empty?
# false
```

## Méthode de combinaison / ## Combination method

### Méthode de combinaison {.row-span-2} / ### Combination method {.row-span-2}

- `&` Returns a new array containing each element found in array and array other_array; duplicates are omitted; use eql?
  to compare items
  
  - `&`Renvoie un nouveau tableau contenant chaque élément trouvé dans le tableau et le tableau other_array ; les doublons sont omis ; utilisez eql ? pour comparer les éléments



- `intersection` Returns a new array containing each element found in self and all given arrays other_arrays; duplicates
  are omitted; use eql? to compare items
  
  - `intersection`Renvoie un nouveau tableau contenant chaque élément trouvé dans self et tous les tableaux other_arrays donnés ; les doublons sont omis ; utilisez eql ? pour comparer les éléments



- `+` Returns an array containing all elements of self followed by all elements of the given array

- `+`Renvoie un tableau contenant tous les éléments de self suivis de tous les éléments du tableau donné



- `-` Returns an array containing all elements of self not found in the given array

- `-`Renvoie un tableau contenant tous les éléments de soi non trouvés dans le tableau donné



- `union` Returns an array containing all elements of self and all elements of the given array, with duplicates removed

- `union`Renvoie un tableau contenant tous les éléments de soi et tous les éléments du tableau donné, avec les doublons supprimés



- `difference` Returns an array containing all elements of self not found in any given array

- `difference`Renvoie un tableau contenant tous les éléments de soi non trouvés dans un tableau donné



- `product` self Returns or produces all combinations of elements from self and the given array

- `product`self Renvoie ou produit toutes les combinaisons d'éléments de self et du tableau donné


### &

```ruby
[0, 1, 2, 3] & [1, 2] # => [1, 2]
[0, 1, 0, 1] & [0, 1] # => [0, 1]
```

### intersection / ### intersection

```ruby
[0, 1, 2, 3].intersection([0, 1, 2], [0, 1, 3])
# => [0, 1]
[0, 0, 1, 1, 2, 3].intersection([0, 1, 2], [0, 1, 3])
# => [0, 1]
```

### +

```ruby
a = [0, 1] + [2, 3]
a # => [0, 1, 2, 3]
```

### -

```ruby
[0, 1, 1, 2, 1, 1, 3, 1, 1] - [1]
# => [0, 2, 3]
[0, 1, 2, 3] - [3, 0]
# => [1, 2]
[0, 1, 2] - [4]
# => [0, 1, 2]
```

### union / ### union

```ruby
[0, 1, 2, 3].union([4, 5], [6, 7])
# => [0, 1, 2, 3, 4, 5, 6, 7]
[0, 1, 1].union([2, 1], [3, 1])
# => [0, 1, 2, 3]
[0, 1, 2, 3].union([3, 2], [1, 0])
# => [0, 1, 2, 3]
```

### différence / ### difference

```ruby
[0, 1, 1, 2, 1, 1, 3, 1, 1].difference([1])
# => [0, 2, 3]
[0, 1, 2, 3].difference([3, 0], [1, 3])
# => [2]
[0, 1, 2].difference([4])
# => [0, 1, 2]
```

### produit / ### product

```ruby
a = [0, 1, 2]
a1 = [3, 4]
p = a.product(a1)
p.size # => 6 # a.size * a1.size
p # => [[0, 3], [0, 4], [1, 3], [1, 4], [2, 3], [2, 4]]
```

## Boucles / ## Loops

### boucle while / ### while loop

```ruby
# variable count
count = 4
# using while loop
# here conditional is count i.e. 4
while count >= 1
  # statements to be executed
  puts "Ruby Cheatsheet"
  count = count - 1
  # while loop ends here
end
```

output / sortir

```
Ruby Cheatsheet
Ruby Cheatsheet
Ruby Cheatsheet
Ruby Cheatsheet
```

### boucle for / ### for loop

```ruby
# loop using range as expression
text = "Ruby Cheatsheet"
# using for loop with the range
for count in 1..5 do
  puts text
end
```

output / sortir

```
Ruby Cheatsheet
Ruby Cheatsheet
Ruby Cheatsheet
Ruby Cheatsheet
Ruby Cheatsheet
```

### faire une boucle while / ### do..while loop

```ruby
# starting of do..while loop
loop do
  puts "Ruby Cheatsheet"
  val = '7'
  # using boolean expressions
  if val == '7'
    break
  end
  # ending of ruby do..while loop
end
```

output / sortir

```
Ruby Cheatsheet
```

### jusqu'à la boucle / ### until loop

```ruby
var = 7
# here do is optional
until var == 11 do
  # code to be executed
  puts var * 10
  var = var + 1
  # here loop ends
end
```

output / sortir

```
70
80
90
100
```

### Sortir de la boucle / ### Break out of loop

```ruby
salary = [399, 234, 566, 533, 233]
salary.each do |s|
  break if s == 566
  puts s
end
# output
# 399
# 234
```

By using the `break` keyword 

En utilisant le `break`mot-clé

### sauter dans la boucle / ### skip within loop

```ruby
salary = [399, 234, 566, 533, 233]
salary.each do |s|
  next if s == 533
  puts s
end
# output
# 399
# 234
# 566
# 233
```

By using next keyword

En utilisant le mot-clé suivant

### Répéter l'itération actuelle / ### Repeat current iteration

```ruby
data = [456, 3000]
retry_count = 0
status = "network failure"
sum = 0
data.each do |d|
    if retry_count == 3
        status = "connection established"
        retry_count = 0
        redo
    elsif status == "network failure" and retry_count < 5
        puts "network failure #{retry_count}"
        retry_count += 1
        redo
    elsif status == "connection established"
        puts d
        sum += d
    end
end
# output of sum
# 3456
```

### Recommencer le cycle / ### Start the cycle again

```ruby
numbers = [2, 2, 44, 44]
sum = 0
begin
    numbers.each do |s|
        if rand(1..10) == 5
            puts "hi 5, let's do it again!"
            sum = 0
            raise "hi 5"
        end
        puts s
        sum += s
    end
rescue
    retry
end
```

## Cours / ## Classes

### Exemple de classes {.row-span-2} / ### Classes Example {.row-span-2}

```ruby
class Person
    # when you create a new object, it looks for a method named initialize and executes it, like a constructor in java
    # def initialize(name, number)
    #    @name = name
    #    @number = number
    # end
    # instance variable
    # @name
    # class variable
    # @@count
    # attr_accessor acts as a getter and setter for the following instance attributes
    attr_accessor :name, :number
    # class variable must be initialized
    @@count = 0
    def self.count
        @@count
    end
    def self.count=(count)
        @@count = count
    end
    def initialize
        @@count += 1
    end
end
# create an instance of the Person class
p1 = Person.new
# set attributes of the Person class
p1.name = "Yukihiro Matsumoto"
p1.number = 9999999999
# get attributes of the Person class
puts "#{p1.name}"
puts "#{p1.number}"
puts "#{Person.count}"
# Yukihiro Matsumoto
# 9999999999
# 1
p2 = Person.new
p2.name = "Yukihiro Matsumoto"
p2.number = 9999999999
# get attributes of the Person class
puts "#{p2.name}"
puts "#{p2.number}"
puts "#{Person.count}"
# Yukihiro Matsumoto
# 9999999999
# 2
# set class variable
Person.count = 3
puts "#{Person.count}"
# 3
```

### Hériter d'une classe / ### Inherit a class

```ruby
class Person
    attr_accessor :name, :number
end
# Inherit methods and properties from parent class using < symbol
class Student < Person
    attr_accessor :id
end
s = Student.new
s.name = "James Bond"
s.number = 700
s.id = 678
puts "#{p.name}"
James Bond
puts "#{p.number}"
700
puts "#{p.id}"
678
```

### Vérifier le type d'instance / ### Check instance type

```ruby
class Vehicle; end
class Car < Vehicle; end
class Audi < Car; end
car = Car.new
car.instance_of? Vehicle
false
car.instance_of? Car
true
car.instance_of? Audi
false
a = 7
a.instance_of? Integer
true
a.instance_of? Numeric
false
```

Returns true if the object is an instance of the given class and not a subclass or superclass

Renvoie vrai si l'objet est une instance de la classe donnée et non une sous-classe ou une superclasse

### Imprimer tous les noms de méthodes d'une classe### Print all method names of a class

```ruby
puts (String.methods).sort
# Exclude methods inherited from Object class
puts (String.methods - Object.public_instance_methods).sort
```

### Vérifier si une classe a une méthode spécifique / ### Check if a class has a specific method

```ruby
String.respond_to?(:prepend)
true
String.respond_to?(:append)
false
```

## See Also

- [Ruby](https://www.ruby-lang.org/en/) _(ruby-lang.org)_
- [Ruby Cheatsheet](https://github.com/lifeparticle/Ruby-Cheatsheet) _(github.com)_