---
layout: default
title: Rails Kids Lesson 1 Random Numbers
permalink: first-guide-random
---

# Rails Kids Lesson 1 Random Numbers

*Created by Sorcha Abel & Darren Oliver  <a href="https://twitter.com/hellorails" class="twitter-follow-button" data-show-count="false">Follow @hellorails</a>
                                         <script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>

## Welcome!!
Hi and welcome back. This is our first 'proper' guide where you get to write you first ruby program. How exciting!!! 
Firstly this program is short and that's all part of our plan. We will introduce you to some of the ruby code structures and syntax. It's 
important to have a basic understanding of ruby before we can move to the more exciting world of rails. Lets get started..

## This Program
This code is a little game between you and the computer. The computer will pick a number between 1 and 10 and you will have 3 changes to guess it correctly. 

## Nitrous
We will start by signing into Nitrous and creating a new workspace. Most of these steps are explained in the Nitrous Setup Guide [Nitrous Setup](/nitrous-guide) 
but as we know this is all still new to you below so here are some tips to get your started. 

Click on the + icon as shown below

<img src="/images/plus_icon.png" width="600">

The `New Project` page will appear

Lets name your new project _Random Numbers_, and make sure you are creating a __Ruby__ workspace. Then click `Create Project`.

### Ruby 

From the file explorer window create a new file, right click on the code folder and select new file

<img src="/images/explorer.png" width="30%">

In the new file type in the following

{% highlight sh %}
class RandomNumber
  MAX_ATTEMPTS = 3
  
  def initialize
    @number_of_tries = 0
    self.start_game
  end

  def start_game
    until @number_of_tries == MAX_ATTEMPTS
      puts "enter a number between 1 and 10"
      number = gets
      number = number.chomp
      computer_number = rand(10)+1

      if number.to_i == computer_number.to_i
        puts "Contrats you entered #{number} and the computer picked #{computer_number}"
        return
      else
        puts "Oops better luck next time, you entered #{number} and the computer picked #{computer_number}"
      end
      @number_of_tries += 1
      puts "the value of number of tried is #{@number_of_tries} "
    end

    puts "THE END"
  end
end
{% endhighlight %}

Save the file (by using File -> Save on the menu bar and call it random_numbers.rb)

### Running your code
In the terminal window type in the following commands

{% highlight sh %}
cd code
irb -I .
require 'random_numbers'
start_game = RandomNumber.new
{% endhighlight %}

### Explanation
Ok so we've typed a lot of code but that's only half of story. Lets explain it so that you really understand what you've just
done. This is sooooo important, if you don't understand it then it will be very hard to write it again (without a guide) and 
it will be equally hard to debug it. Debugging is a big part of a developers life, it involves finding a piece of your code
that is doing exactly what you expected it to do. Believe it or not, its actually good fun :)

#### Step 1 - The class
Ruby is an object oriented programming language and while that's in itself is a big topic right now all you need to know is 
that ruby programs tend to live inside a class. Therefore the first piece of code that we write is;
{% highlight sh %}
  class RandomNumber
  
    code goes here
    
  end
{% endhighlight %}

#### Step 2 - A CONSTANT
In ruby a constant is a value that **never** changes. It's a ruby convension to put this constant in uppercase. This tells other programmers
who look at your code at first glance that it's a constant. Ruby is full of these 'convensions' but don't worry too much about them for now. 
In this case we call the constant variable `MAX_ATTEMPTS` and set the value to 3

#### Step 3 - Initialize
The next step is to create a new method called initialize. In ruby we create a method using the `def` keyword. This 
method is the first one that will be called when we run our program. You might have noticed that we ran our code using 
the `new` keyword in the terminal window like so

{% highlight sh %}
  start_game = RandomNumber.new
{% endhighlight %}

where `RandomNumber` is our class name and by appending a .new to it actually tells ruby to run the initialize method. 
Pretty slick eh!

Inside our initialize method we are declaring another variable, this time its called an instance variable. An instance variable is different to
a constant because its value **can** change. 
We will use this variable to keep track of how many attemps to guess the number you have made. Remember you only have 3 chances :)
To start the game we set its value to 0

We also call another method from within the initialize one. We use `self.start_game` to call the method. This method is where all the fun is

#### Step 4 - Method start_game
We start this method with a control loop called an `until` loop. It will keep looping from start to the end until a condition is met. In this case
it will loop until you have used up your 3 chances. 

The next statement uses `puts` to **put** a message to the terminal window. 
Similarily `gets` is used to **get** input from the terminal window. In this case we are getting the first guessed number (PS chomp just removes the newline
character)

The next line generates the random number and stores it in a local variable called `computer_number`. rand is a build in method that comes with Ruby. Its purpose
is to generate a random number and the bit inside the parentheses is called an argumment. In this case we have given it an argument of 10. This tells the computer
to generate a random number between 1 and 10

#### Step 5 - If statements
If statements are called controlled structrues in ruby (and most other programming languages). Here we are simply saying this; if the number you entered via the
terminal window is the same as the random number that the conputer generated then you win, yay. We then use the `return` keyword to exit out of the loop because you 
have just won! 
 
or else..

The computer wins..boo

You may have noticed the to_i bit at the end. This is a nifty way to converting the value to an integer. An integer is just a number

At the end of the `if` block we add the value of 1 to the instance variable `number_of_tries`. Below is a shorthand way of doing it

{% highlight sh %}
  @number_of_tries += 1
{% endhighlight %}

but really it would be the exact same if we did it like this

{% highlight sh %}
  @number_of_tries = @number_of_tries + 1
{% endhighlight %}

Finally when your 3 chances are up the until loop ends and we use `puts` again to let you know that the game is over. 

## The End
That's it. We understand that we have introduced lots of new concepts so we have an explaination / cheat sheet [Cheat Sheet](/explainations-guide) that you
can refer to regardless of the lesson you are on. Oh you can also ask one of the instructors to explain any of it, we love questions

See you in lesson 2

Darren & Sorcha




