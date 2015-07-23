# Student Session for the Rails Console

## Learning Goals

* How to use awesome_print in your development and test environments to make the output more readable
* Using the console in --sandbox mode and with different ENVs
* Workflow tricks, including:
 - Underscore
 - reload!
 - Tabbing to see options for Classes, and their associated methods
 - Calling .methods and filtering through them
 - Using Ctrl+R to search for previous commands
 - irb object_name to set a 'default object'
* See the output of your helper methods by calling them on the helper object
* See the path associated with a certain route helper
* How to log in through the console


### Inside this repo is: Storedom

Storedom is a simplistic e-commerce application used
for various lessons and tutorials at Turing.

### Setup

To get set up with the storedom application, clone it
via `git` and pull in gem dependencies with `bundler`:

```
git clone https://github.com/turingschool-examples/storedom.git
cd storedom
bundle
```

And set up the database and included seed records:

```
bundle exec rake db:setup
```

## Let's Play!

Once you've cloned, bundled, and set up your database with the seed records, fire up a console session in your terminal by typing:

```
rails c
```

### Awesome Print

You should have:

```
gem 'awesome_print'
```
in your Gemfile, which loaded the [Awesome Print](https://github.com/michaeldv/awesome_print) gem into your app on bundle.

Now if you preface anything with 'ap' in your console, you'll see a colorized, formatted output. Try:

```
ap User.first
```

### Sandbox Mode and Different ENV Setups

If you want the chance to interact with your database without actually making any lasting changes, run your console in sandbox mode:

```
rails c --sandbox
```

This is especially helpful for running the console for your Production environment:

```
rails c production --sandbox
```

Substitute other environments in place of production as needed.

### Improving Your Workflow

Have you ever made an outrageously long ActiveRecord query and forgotten to store it to a local variable?
Underscore '_' holds the last thing that was returned from your console. This works with pry and IRB, too.

```
User.first.orders.last.order_items.last.item
item = _
```

Reload the environment without restarting the console with the command:

```
reload!
```

The console has an auto-complete functionality that will finish methods, or suggest methods based on your input.
Try typing:

```
User.a
```
...and then press tab two times.

Filtering through methods -

User.public_methods - Object.public_methods

Awesome print is great because it shows you whether the method takes any arguments.

Ctrl+R will let you search through previous commands, so you don't have to hit your up arrow key a zillion times.

Saying:

```
u = User.first
irb u
```
Will set user to your default object, so you can call methods on it without having to reference it. Instead of 'u.name', simply 'name' will work.
To terminate this and return to your original context, just type 'exit'.


### See what your helper methods are doing

Use the helper object to see what your helper methods return.

```
helper.number_to_currency(3)
```

### See the path associated with a certain helper

app.users_path == '/users'


### How to log in through the console?
