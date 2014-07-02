---
layout: post
title:  "Command Line Applications in Node.js"
date:   2013-05-23
author: Mark Taylor
categories: nodejs command-line
---

Node.js is a powerful language and can be used for many different purposes, not just server side applications. For example using its built in readline library you can interact with the user on the command line. This library is powerful and easy to use, for example using the question function will display text to the user and wait for their input, when the user has returned some data callback is then called. Using this I was able to create a simple (and not very fun) guessing game in about 5 minutes.

{% highlight js %}
var readline = require('readline');

var rl = readline.createInterface({
        input: process.stdin,
        output: process.stdout
});

console.log("I am thinking of a number between 1 and 10");

askQuestion("Take a guess");

var number = Math.floor((Math.random()*10)+1);

function askQuestion(question){
        rl.question(question + "\n", function(answer) {
                if(answer == number) {
                        console.log("Well done! The answer was %s", answer);
                        rl.close();
                } else if(answer < number) {
                        askQuestion("Too low, Guess again");
                } else {
                        askQuestion("Too high, Guess again");
                }

        });
}
{% endhighlight %}
This is simple and easy to follow, the interesting part being the rl.question, with the callback returning the answer to the application. Combining this with Nodes ability to run local commands in child processes and handle the output it should be relatively easy to create useful, interactive scripts which run local commands.