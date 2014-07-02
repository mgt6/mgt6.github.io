---
layout: post
title:  "Changing the Console log colour in Node.js"
date:   2013-04-22
categories: nodejs command-line
---
Changing the text colour in a console.log message in Node.js is very simple, you can do it by using ANSI escape codes for example:

{% highlight js %}
console.log("Test create error message produces valid message ...." + '\033[31;1m' + '[Failed]' + '\033[0m' )
{% endhighlight %}

or

{% highlight js %}
console.log("Test create error message produces valid message ...." + '\033[34;1m' + '[Passed]' + '\033[0m' )
{% endhighlight %}

This will print the console message with the [Failed] in red, then the colour is reset or the console message then [Passed] in blue.

It is important to remember to reset the colour when you are done!