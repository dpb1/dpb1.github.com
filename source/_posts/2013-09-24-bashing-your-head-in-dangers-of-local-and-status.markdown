---
layout: post
title: "Bashing Your Head In: Local is a Command"
date: 2013-09-24 16:01
comments: true
categories: code
---

[Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) has a major
conceptional drawback.  No, I'm not talking about odd syntax, overuse of
whitespace delimiters or even the slow performance.  Nearly everything in the
language is a command.  Bash works really well for executing simple Unix
commands, parsing the output, and acting on their return codes, but it
sometimes returns confusing results when you fail to remember that it's own
builtin commands use this same system for reporting output and results.

For instance, this bit of code is a very clean way to parse a syslog file for
all executions of the CRON subsystem on Ubuntu.  Quick and readable, runnable
at the command line, and just makes sense:

``` bash
output=`cat /var/log/syslog | grep CRON | wc -l`
if [ $? -eq 0 ]; then
    echo "Found $output cron log line(s)"
else
    echo "No cron log lines found"
fi

```

Notice that I am capturing the output of that command into a variable named
`output`.  Ideally, you would want that output variable to be local, since
output is a common word, and you could be trampling on some other code in a
sourced file, or even in your own file.  So, let's do this:

``` bash
local output=`cat /var/log/syslog | grep CRON | wc -l`
```

There!  All fixed.  Except, it's not.  You probably see the problem, the local
builtin is actually a command whose status is evalutated after the execution of
your log parsing.  Since `local output` will succeed in pretty much every case,
the result of the last command (`$?`) will always evaluate to 0.

The best practice is always to

  1. Use Local variables
  2. Declare local variables on their own line

So our silly example becomes:

``` bash
local output
output=`cat /var/log/syslog | grep CRON | wc -l`
if [ $? -eq 0 ]; then
    echo "Found $output cron log line(s)"
else
    echo "No cron log lines found"
fi

```

Happy Bashing!
