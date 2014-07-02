---
layout: post
title:  "Continuous Testing in Node.js"
date:   2013-04-16
author: Mark Taylor
categories: nodejs command-line
---

Using nodemon it is possible to monitor a directory for changes to files and run a specific file on any change.

nodemon will need to be installed globally to do this, in order to install node modules globally, to do this using linux simply run:

{% highlight bash %}
sudo npm install -g nodemon
{% endhighlight %}

This will then allow you to start nodemon to start a node application, for example:

{% highlight bash %}
nodemon server.js
{% endhighlight %}

This will restart the server.js file when it detects a change to this file.

Building on this we can add files or directories to watch by using the watch flag. My current usage is:

{% highlight bash %}
nodemon --watch src test/mocha.js
{% endhighlight %}

This is run from the root directory of the application. It starts by running the file provided, then any time the files in the src directory are changed the test file is re-run. Each file or directory you want to monitor will need to be added with an additional watch. This way it could be configured so that any changes to the src or test directory will re-run the tests. Just be careful if you have any output from the script you run being written into one of these directories.