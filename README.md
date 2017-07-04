# hashes_mau
# Challenge: Useful Methods
Go ahead and try the following methods:

.delete(key) => deletes and returns a value associated with the key
e.g.  ruby h = {:first_name => "Coding", :last_name => "Dojo"} h.delete(:last_name) print h # => {:first_name => "Coding"}
.empty? => returns true if hash contains no key-value pairs
.has_key?(key) => true or false
.has_value?(value) => true or false
The Evolution of Ruby
Instantiating a Hash
As we saw in the example above we can declare a hash using the following syntax:

our_hash = {:first_name => "Coding", :last_name => "Dojo"}
In the name of elegance, we now have a new way of creating a hash:

our_hash = {first_name: "Coding", last_name: "Dojo"}
No more hash rockets! Well, sort of. The latter syntax is just syntactic sugar to the former way of creating hashes in Ruby. At the fundamental level, both are instantiating a new Hash object. We can test this in IRB:

2.3.1> our_hash = {first_name: "Coding", last_name: "Dojo"} # press enter
=> {:first_name=>"Coding", :last_name=>"Dojo"} 

A hash as an Input
Because of the changes on how Ruby interprets hashes, we can also pass hashes as an argument to a method. Let's look at an example:

def new_user user = {first_name: "first", last_name: "last"}
  puts "Welcome to our site, #{user[:first_name]} #{user[:last_name]}!"
end
our_user = {first_name: 'Oscar', last_name: "Vazquez"}
new_user # => "Welcome to our site, first last!"
new_user our_user # => "Welcome to our site, Oscar Vasquez!"

Now, this is kind of cool. We're passing in a hash as an argument to our method and printing a message using its values. If we don't have any arguments, we will just use the default values. However, Ruby allows us to refactor this code even more:

def new_user first_name: "first", last_name: "last"
  puts "Welcome to our site, #{first_name} #{last_name}!"
end

Now, this is much cleaner! In Ruby version 2, we were introduced to keyword arguments. Technically, it's the same thing but with much cleaner syntax, and a couple of added features.

Before we would have to fetch our values out of the hash, now ruby fetches them for you and sets it as a local variable.
Before we could set a hash as a default input, now we can set default values as keyword arguments.
Now, we can still use regular parameters with keyword arguments

def new_user greeting="Welcome", first_name: "first", last_name: "last"
    puts "#{greeting}, #{first_name} #{last_name}"      
end
our_user = {first_name: "Oscar", last_name: "Vazquez"}
new_user                  # => Welcome, first last
new_user "Hello", our_user # => Hello, Oscar Vazquez
