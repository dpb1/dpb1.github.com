---
layout: post
title: "Timezone math on a grid: tzgrid"
comments: false
categories:
  - productivity
  - code
  - ubuntu
---


I love my [current job][1], an engineering manager at [Canonical][2].
It's been a blessing to our family that I can work from my house.  I get
to do just enough traveling to places I likely would have never gone on
my own.  And I get to work on a product that I love ([Ubuntu Server][3])
with people I love that are just some of the brightest, friendliest and
fun people in the industry.

... need more here ...

Simple, just memorize these timezones.
-----------

{% img center /images/timezone-map.png Timezones! %}


So what's the problem?  Maybe you don't have this problem, but for me,
timezone math is hard.  It's simple addition and subtraction, why should
it be hard?   I suspect there are a few reasons for this:

 * My sense of time is very focused on myself and the sunrise/light
   here.
 * When I do time calculations in my head like "3 hours from now" or "2
   hours ago", I don't do them as integer math problems, but instead
   somewhat visually - like adding and removing beans in a bowl.  So,
   the question "What time was it 3 hours ago in Germany", makes me
   first have to get the right time in Germany, then do the visual
   subtraction on the clock.  I then can't easily repeat that for "What
   about London?"
 * 12 hour vs 24 hour clocks don't help.
 * Time resetting to 0 (or 12!) every night at midnight also doesn't
   help.

Whatever the cause, the easiest solution I have found is to see times
visually on a screen or paper for different timezones.  A site
worldtimebuddy actually has a very nice layout for this that I really
clicked with, and I still use.  But, I wanted something that worked from
the command line as that is where I spend a lot of my day.

Introducing tzgrid
-----------

<< tzgrid icon >>


Do you know what `cal` is?  Do you run it?  I do.  So ya, that's why the
world now has...  [tzgrid][4].  It's a very simple python module that's
primary purpose is to display output that looks like this:

<< image of tzgrid here >>

It has a few neat facilities:

<< copy some blurbs from readme.md >>


Wow, I'm sold, where do I send money?
-------

Put that money back in your pocket sirs and madams, it's free and simple
to install.  If you are using Ubuntu 16.04 or newer:

    sudo snap install tzgrid

Ubuntu 14.04?

<< how to do that >>

Another Linux distro?

<< how to do that >>

If you are using mac or windows, well, I think the python module should
work, but I haven't tested.  Let me know via github if you try.



[1]: https://www.linkedin.com/in/david-britton-6b88818/
[2]: https://canonical.com/
[3]: https://ubuntu.com/server
[4]: https://github.com/dpb1/tzgrid


