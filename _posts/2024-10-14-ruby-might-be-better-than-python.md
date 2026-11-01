---
layout: post
title: Ruby might be better than python for new learners
---

Every few months someone asks me which language a beginner should start with, and I give the same answer I've given for years: it depends, but if you want the shortest path from "I've never written code" to "I built something and I understand why it works," Ruby is the better bet. Not because Python is bad. Python is a fine language with a bigger job market and better type tooling. But the specific things that trip up beginners are, almost without exception, things Ruby does not do to them. Below are the ones I've actually watched people hit, with code.

## 1. The `self` parameter

This is the first wall in Python and it has no equivalent in Ruby. Every Python method takes `self` as its first argument, but you never pass it at the call site. Beginners spend a week asking why.

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):
        return f"Hello, {self.name}!"

alice = Person("Alice")
alice.greet()   # works, but why no argument here?
```

Now watch what happens when a beginner, having internalized that methods take the parameters they're defined with, writes one without `self`:

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greet():
        return "Hello!"

alice = Person("Alice")
alice.greet()
# TypeError: greet() takes 0 positional arguments but 1 was given
```

The error is technically correct and completely useless to someone who hasn't yet learned that `alice.greet()` is `Person.greet(alice)` under the hood. To explain the fix you have to teach the descriptor protocol, which is a lot of machinery to deploy in week one. Ruby's version:

```ruby
class Person
  def initialize(name)
    @name = name
  end

  def greet
    "Hello, #{@name}!"
  end
end

alice = Person.new("Alice")
alice.greet  # => "Hello, Alice!"
```

The method signature has no phantom parameter. `@name` is scoped to the instance, so there's nothing to pass and nothing to forget. The call and the definition match. That's the whole lesson, and it takes about four minutes instead of a week.

## 2. Ruby's object model is uniform; Python's has holes

If you're teaching objects, Ruby is a better classroom because it never has to say "except." In Ruby:

```ruby
1.class        # => Integer
nil.class      # => NilClass
1.+(2)         # => 3
"abc".length   # => 3
```

Everything is an object, operators are methods, `nil` is an object with methods (`nil.to_a` is `[]`, `nil.to_s` is `""`). You can send a message to anything.

Python claims the same thing and then introduces built-in functions that are not methods on the objects they operate on:

```python
len([1, 2, 3])    # not [1,2,3].length()
str(42)           # not (42).to_string()
int("42")         # not "42".to_i()
print("hello")    # not "hello".print()
```

You *can* write `(1).__add__(2)` in Python, but nobody does, and the double-underscore method is not what you'd teach a beginner. So a Python learner gets two mental models: "everything is an object" and "except for the dozen functions the language gives you." Ruby gives them one.

## 3. Mixins: one method in, a library out

This is the best teaching device Ruby has and the reason I'd hand a beginner Ruby before anything else. Define `each` and you get roughly fifty methods for free, because `Enumerable` is included:

```ruby
class Playlist
  include Enumerable

  def initialize(songs)
    @songs = songs
  end

  def each(&block)
    @songs.each(&block)
  end
end

list = Playlist.new(["Blue", "Amber", "Cerulean"])
list.map(&:upcase)            # => ["BLUE", "AMBER", "CERULEAN"]
list.select { |s| s.start_with?("B") }   # => ["Blue"]
list.sort                     # => ["Amber", "Blue", "Cerulean"]
list.include?("Amber")        # => true
list.min                      # => "Amber"
list.count                    # => 3
```

Fifty methods from one. That is abstraction made visible. A beginner who implements `each` and then calls `.map` has learned something about code reuse that no amount of explanation gets across.

Same trick with `Comparable`. Define `<=>` and you get every comparison operator:

```ruby
class Version
  include Comparable

  attr_reader :major, :minor

  def initialize(major, minor)
    @major, @minor = major, minor
  end

  def <=>(other)
    [major, minor] <=> [other.major, other.minor]
  end
end

Version.new(1, 2) < Version.new(1, 10)      # => true
Version.new(2, 0) > Version.new(1, 99)      # => true
Version.new(2, 0).between?(Version.new(1, 0), Version.new(3, 0))  # => true
```

Two methods, a full set of operators, and no mystery about where `<` comes from. Python's iterator protocol gets you `map`, `filter`, and `sum` through built-ins, but it doesn't show the learner that they just *received* a library for implementing one method. The lesson is invisible.

## 4. Truthiness: one sentence versus a table

Ruby's falsy values are `nil` and `false`. That's it. `0`, `""`, `[]`, and `{}` are all truthy.

```ruby
puts "this runs" if 0
```

Python has six or seven falsy values and the list depends on what the object's `__len__` or `__bool__` does. The consequence is real bugs:

```python
def process(items=None):
    if not items:
        print("nothing to process")   # also true for an empty string, 0, False...

process([0])   # fine
process(0)     # "nothing to process" — but 0 isn't nothing
```

Ruby's version is unambiguous:

```ruby
def process(items = [])
  puts "nothing to process" if items.empty?
end
```

Ruby learners still have to learn what `nil` means, but they never have to learn a table of falsy values and they never hit the "empty list is falsy" bug that every Python beginner hits at least once.

## 5. Terseness: fewer lines, less to debug

Ruby does a lot per line. A getter/setter pair:

```ruby
class Person
  attr_accessor :name
end
```

Python:

```python
class Person:
    def __init__(self, name):
        self._name = name

    @property
    def name(self):
        return self._name

    @name.setter
    def name(self, value):
        self._name = value
```

The Python version isn't hard, but it's sixteen lines for a concept that fits in one. Every line is something a beginner has to read, understand, and debug.

Value objects show the same gap. Ruby:

```ruby
Point = Struct.new(:x, :y)
p1 = Point.new(1, 2)
p1.x                     # => 1
p1 == Point.new(1, 2)    # => true
```

Python needs an import and a decorator:

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int

Point(1, 2) == Point(1, 2)   # => True
```

Dataclasses are good, and I'd rather write Python dataclasses than Ruby structs for anything real. But for a first lesson on what a value is, one line beats four plus an import.

## 6. Indentation is syntax, and copy-paste breaks it

Python uses whitespace to delimit blocks. That's fine once you're used to it, and it produces pretty code. It also means a paste with the wrong indentation is a `SyntaxError` before it's a logic error:

```python
def check(n):
    if n > 0:
        print("positive")
    print("always runs")
```

Move that second `print` one level in or out and the meaning changes. Paste a snippet that mixes tabs and spaces and you get `TabError: inconsistent use of tabs and spaces in indentation`, which is a confusing message for someone who just copied an answer from a forum and didn't touch the whitespace. Ruby has structural rules, but indentation isn't one of them, so a pasted snippet is more likely to fail for a reason related to what it does rather than where its spaces are.

The flip side is real and worth saying: Python's forced indentation means Python code is uniformly readable, which matters a lot once you're on a team. That's a cost-benefit trade, not a bug. For a solo beginner, though, it's friction.

## 7. Mutable default arguments

This one produces bug reports that read like the language is broken:

```python
def add_tag(tag, tags=[]):
    tags.append(tag)
    return tags

add_tag("a")   # => ['a']
add_tag("b")   # => ['a', 'b']
```

The default list is created once, at function definition, and shared across calls. Every Python teacher has a story about this. The fix is `tags=None` plus a guard, which is boilerplate you have to remember before you understand why. Ruby evaluates default arguments on every call, so the trap doesn't exist:

```ruby
def add_tag(tag, tags = [])
  tags << tag
end

add_tag("a")   # => ["a"]
add_tag("b")   # => ["b"]
```

## 8. `if __name__ == "__main__":`

Every Python tutorial includes this line and every Python tutorial hand-waves it:

```python
def main():
    run()

if __name__ == "__main__":
    main()
```

A beginner cannot evaluate it. To understand it you need modules, the import system, and the difference between running a file and importing it — three topics that are weeks away. So they copy it, and it becomes cargo. Ruby has no equivalent incantation: you write the code, it runs when you run the file.

## 9. Rails gets you to a working full-stack app in an afternoon

The usual counterargument to Ruby is that Rails is old. It is. It's also still the fastest way to show a beginner the whole stack. Three commands:

```ruby
rails new blog
bin/rails generate scaffold Post title:string body:text
bin/rails db:migrate
```

You now have routes, a controller, views, a schema, and a form that creates records. Run `bin/rails server` and it's live. A beginner can click through it, change the title field, watch the database update, and start asking questions about the pieces.

Django's equivalent takes longer before you see anything, and the step that trips people up is invisible: you have to register the app in `INSTALLED_APPS` before models work, and nothing tells you that's the problem.

```bash
django-admin startproject blog
cd blog
python manage.py startapp posts
# edit settings.py to add "posts" to INSTALLED_APPS  <- forget this and nothing works
# edit models.py
python manage.py makemigrations
python manage.py migrate
```

Flask is lighter but means assembling pieces by hand: routing, templates, an ORM, forms, migrations.

Two honest caveats. Django's admin is genuinely better than anything in the Rails ecosystem out of the box, and it's a great thing to show a beginner. And Rails' "magic" is a real cost once something goes wrong — a beginner debugging Rails has to learn where the conventions live before they can find the code that's failing. Python's explicitness is an advantage there. For the first month, though, Rails wins on momentum, and momentum is what keeps beginners going.

## 10. RSpec reads like the sentence you're trying to write

Testing is where beginners learn to state behavior in plain language, so the syntax of the test framework matters more than you'd think.

```ruby
RSpec.describe Person do
  it "greets by name" do
    expect(Person.new("Alice").greet).to eq("Hello, Alice!")
  end
end
```

That reads close to the English you'd say out loud. The `unittest` version in Python is noisier:

```python
import unittest

class TestPerson(unittest.TestCase):
    def test_greet(self):
        self.assertEqual(Person("Alice").greet(), "Hello, Alice!")
```

In fairness, `pytest` closes most of the gap:

```python
def test_greet():
    assert Person("Alice").greet() == "Hello, Alice!"
```

And plain `assert` is a better first lesson than `self.assertEqual`. So this one is closer to a tie than it looks — but the default that ships with the language, and therefore the one a tutorial will show, is the clunky one.

## 11. Packaging: one story versus three

Ruby's story for a beginner's project is a `Gemfile` and `bundle install`:

```ruby
source "https://rubygems.org"
gem "rails", "~> 7.1"
gem "pg"
```

```bash
bundle install
bundle exec rails server
```

Python's story is pip, venv, and requirements, and you have to know which order to hold them in:

```bash
python -m venv .venv
source .venv/bin/activate     # or .venv\Scripts\activate on Windows
pip install -r requirements.txt
pip freeze > requirements.txt
```

Then someone mentions `pyproject.toml`, `setup.py`, `setup.cfg`, Poetry, or `uv`, and the beginner has to figure out which era of Python packaging the tutorial they're following was written in. This is a solved problem in the abstract and an unsolved problem in practice. Ruby has its own issues (`bundle exec` is a wart), but the beginner has one file and one command.

## 12. `case`/`when` matches on more than equality

Ruby's `case` uses `===`, which is defined by the class on the right. So ranges and classes match directly:

```ruby
case value
when 1..10   then "small number"
when String  then "some text"
when nil     then "nothing"
else              "something else"
end
```

Python only got pattern matching in 3.10, and the same logic is longer and needs a guard clause:

```python
match value:
    case int(n) if 1 <= n <= 10:
        label = "small number"
    case str():
        label = "some text"
    case None:
        label = "nothing"
    case _:
        label = "something else"
```

Ruby's version also works on any object that defines `===`, which is a nice hook for later: a beginner can define their own `===` and the `case` statement picks it up. Python's `match` is more powerful for structural destructuring, so this isn't a knockout — but for the branching a beginner actually writes, Ruby's is shorter and has fewer moving parts.

## 13. The console is a better classroom than a REPL

`bin/rails console` puts you inside your application with your models loaded:

```ruby
bin/rails console

Post.count
Post.first.title
Post.create!(title: "Hello", body: "...")
reload!   # after editing a model, no restart
```

You can inspect a record, see its associations, and change data without writing a script. With Pry in a plain Ruby project you also get `ls` (what's on this object), `show-source` (where does this method come from), and `cd` (step into an object). Those three commands teach object introspection better than anything else I know. IPython closes part of this gap and is genuinely good, but a beginner following a Python tutorial gets the plain REPL, where `dir()` is the closest thing and it tells you much less.

## Where Python actually wins

I'd be lying if I said this was one-sided. Python wins on type hints: mypy and Pyright give a beginner real feedback in an editor, and there's no equally mature equivalent in Ruby for most projects. Python's documentation is more consistent, and the standard library is more coherent. The job market is bigger, and if the learner is heading toward data work or machine learning, Python isn't optional. `pytest` and dataclasses are both genuinely nicer than their Ruby counterparts, and the `match` statement, while verbose in the example above, does destructuring that Ruby can't touch. If someone told me they wanted to learn programming specifically to work with data, I'd hand them Python and not think twice.

## So which one

If the goal is to teach someone the concepts — objects, blocks, abstraction, testing, how a web app is put together — Ruby gets out of the way more often. The `self` parameter, the uniform object model, `Enumerable`, truthiness, and mutable defaults are five concrete places where a Ruby learner spends their attention on programming instead of on the language's rules. Rails then lets them build something real before they've lost interest.

Python is the better language to have on your CV. Ruby is the better language to learn on. Those are different questions, and I wish more people asked the second one before answering the first.