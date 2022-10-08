---
title: "Ruby on Rails"
lastmod: 2022-10-08T00:00:00+08:00
draft: false
tags: [ruby, rails]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

## Overview

* Rails is a full-stack application
* Created in 2004 by DHH
* Values "convention over configuration"
* Model - View - Controller
  * Three main components of the web application
  * Controller talks to the model, model talks to the database, model returns to the controller, controller gets the view, then returns that to the browser

### Rails Flavored Ruby

* Ruby is object-oriented
* Rails is Ruby with a ton of DSLs that basically make it a dialect of Ruby

These lovely examples were shared with me by [@jtamsut](https://github.com/jtamsut).

### Components of Rails

* **ActiveRecord:** `ActiveRecord` is the ORM Rails uses to work with the database. You search for stuff inside of models. I like to think of models as basically being database tables. `ActiveRecord` supports all your typical SQL stuff.
* **ApplicationController:** Creates controllers that take in and route requests.
* **ActionView:** Creates the HTML templates using ERB.

### Example One

```ruby
class Car
  def vroom
    puts "vrooom"
  end
end

class Toyota < Car
  attr_reader :color, :wheels
  
  def self.call
    puts "I am a class method"
  end
  
  def initialize(color:)
    @wheels = 4
    @color = color
  end
  
  def toyota_specific_stuff
    puts "I love Toyota"
  end
end

my_car = Car.new
my_car.vroom #=> "vroom"
my_toyota = Toyota.new(color: "blue")
my_toyota.vroom #=> "vroom"
my_toyota.toyota_specific_stuff #=> "I love Toyota"
puts my_toyota.wheels #=> 4
puts my_toyota.color #=> blue
Toyota.call #=> "I am a class method"
```

* things to note:
  * can share methods with `SubClass < SuperClass`
  * the `initialize` method creates objects
  * instance variables begin with the `@` symbol
  * named parameters (`named_parameter:`)
  * **symbols** are immutable, reusable constants represented internally by an integer value
  * `attr_reader` creates `color` and `wheels` methods (`attr_writer` and `attr_accessor` also exist)
  * `self` refers to the current object
  * `call` is a class method

### Example Two

```ruby
require 'digest'

module Encryption 
  def encrypt(string)
    Digest::SHA2.hexdigest(string)
  end
end

class Login
  include Encryption 

  def initialize(username:, password:)
    @username = username
    @password = password 
  end

  def save_user
    puts "saving #{@username} & #{hashed_password}"
  end

  def hashed_password
    encrypt(@password)
  end
  
  def user_allowed?
    true
  end
end

login = Login.new(username: "githubrocks", password: "123abc")
login.save_user #=> saving githubrocks & dd13...
```

* things to note:
  * modules allow you to create mixins with `include`
  * string interpolate with "some string #{variable}"
  * the last statement is returned from methods (`return` also exists)

### Other Things

* `ApplicationJob` is used for async jobs
* Rails does some autoloading of constants and classes so that you don't need to require them
* "Rails magic" has a bunch of conventions for file naming that makes a lot of things work automatically
* Modules create a namespace which provides some differentiation for your code
* You use mixins for injecting some type of behavior into a class.
* Methods that return a boolean typically have a question mark, like `object.present?`
* Methods that have an exclamation point usually mean that they are mutating the object that it's called on, like `user.update!`
* Use object.method.inspect to get more details about it, like `t.name.inspect`
* `rescue` is the way of catching errors in ruby
* Ambersand is a safe access operator: `puts t&.name&.`

## Commands

* `rails server` starts the server
* `rails routes` loads Rails routes

### Rails Console

* `rails console` or `rails c` starts the console
* `rails console --sandbox` starts the console in sandbox mode, where any modifications that are made will be rolled back when exiting
* Creating new objects:
  * `User.new(name: "Brittany Ellich", email: "brittany.ellich@outlook.com")`
    * Note when using new, you must also do: `user.save` on the object, as User.new will only create the object in memory
  * `User.create(name: "Brittany Ellich", email: "brittany.ellich@outlook.com")`
    * `create` does the new and save all in one step
* Deleting objects:
  * `foo.destroy`
    * Removes the item from the database, but the object will still exist in memory.
    * Returns the object from the destroy method
* Finding objects:
  * `User.find(1)`
    * Finds the object by the ID that you pass in
  * `User.find_by(email: "brittany.ellich@outlook.com")`
    * Finds by whichever attribute you pass in. You'll probably want an index on this attribute in the database if it's done a lot.
  * `User.first`
    * Returns the first user in the DB
  * `User.all`
    * Returns all users in the DB
* Updating objects
  * `user.email = "brittany.ellich@outlook.com"`
    * This requires a `user.save` to actually save to the DB
    * You can reload with the DB value by doing `user.reload`
  * `user.update(name: "Awesome", email: "awesome@example.com")`
    * Updates multiple attributes and saves in a single step
* Find issues with an objext
  * `user.errors.full_messages`
    * Shows any error messages on the user object

## Learning Resources

### Articles

* [ ] [Ruby on Rails Guide](https://guides.rubyonrails.org/getting_started.html)
* [ ] [Upcase by Thoughtbot](https://thoughtbot.com/upcase)
* [ ] [Learn x in y minutes for Ruby](https://learnxinyminutes.com/docs/ruby/)

### Books

* [ ] [Sustainable Rails](https://sustainable-rails.com/)
* [ ] [Michael Hartl's Ruby on Rails Tutorial](https://www.railstutorial.org/book)

### Courses

* [ ] [Owning Rails](http://owningrails.com/#packages)
* [ ] [Go Rails](https://gorails.com/)
* [ ] [Graceful Dev Ruby](https://graceful.dev/courses/the-freebies/)

### Practice

* [ ] [Exercism Ruby](https://exercism.org/tracks/ruby)
