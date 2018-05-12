---
layout: post
title: "Timezone math on a grid: tzgrid"
comments: false
categories:
  - productivity
  - code
  - ubuntu
---


I love my [current job][1] as an engineering manager at [Canonical][2].
It's been a blessing to our family that I can work from my house.  I get
to do just enough traveling to places I likely would have never gone on
my own.  And I get to work on a product that I love ([Ubuntu Server][3])
with people I love that are just some of the brightest, friendliest and
fun people in the industry.

My team at Canonical speaks 5 different languages natively and spans 6
"standard" timezones.  It's such a cool experience to work with people
from many different cultural backgrounds.

As the person who has the pleasure of managing this team, one of my
responsibilities is knowing when we can schedule things like standups or
team meetings where everyone can attend.


Simple, just memorize these timezones.
-----------

{% img center /images/timezone-map.png Timezones! %}

Back to those 6 standard timezones, those are more richly referred to by
their [IANA tz database zone][5] names, which carry historical
information as well as correct current political time changes in their
definitions.  My team's time zones:

 * Mountain: America/Denver
 * Central: America/Chicago
 * Eastern: America/New_York
 * Eastern: America/Toronto
 * Brazilian: America/Sao_Paulo
 * British: Europe/London
 * Central European: Europe/Rome
 * Central European: Europe/Berlin

Basically, if you can map where the person lives to their IANA zone
name, you know what "time" people that live in that area think it is
**now**, or even at some point in the past 100 years or so (timezones
weren't really formalized until trains let us travel across distances so
quickly, and on schedules, that it mattered to know).

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
   about Brazil in the summer?"
 * 12 hour vs 24 hour clocks don't help.
 * Time resetting to 0 (or 12!) every night at midnight also doesn't
   help.

Whatever the cause, the easiest solution I have found is to see times
visually on a screen or paper for different timezones.  A site
[worldtimebuddy][6] actually has a very nice layout for this that I
really clicked with, and I still use.  But, I wanted something that
worked from the command line as that is where I spend a lot of my day.

Introducing tzgrid
-----------

{% img center /images/tzgrid.png tzgrid! %}

Do you know what `cal` is?  It looks like this:

```
$ cal
      May 2018
Su Mo Tu We Th Fr Sa
       1  2  3  4  5
 6  7  8  9 10 11 12
13 14 15 16 17 18 19
20 21 22 23 24 25 26
27 28 29 30 31
```

I use that a lot, and that's why the world now has...  [tzgrid][4].
It's a very simple python module that's primary purpose is to display
output that looks like this:

{% img center /images/tzgrid2.png tzgrid-screenshot! %}

It has a few neat features:

 * Includes database of cities with more than 100,000 people to ease in
   looking up timezones.
 * Colored output in the terminal
 * Pass in arbitrary time/day or rely on default of 'now'
 * DST offsets are calculated correctly
 * Workday hours highlighting helps to know when to schedule a meeting.

And the usage of it is very simple, I can set up a config file to show
all my team's timezones with `tzgrid`, or if I have a meeting to arrange
with someone in Seattle and in Wellington (NZ), and I can type `tzgrid
Denver Wellington Seattle` and see my 3 timezones displayed right there.

Wow, I'm sold, where do I send money?
-------

Put that money back in your pocket sirs and madams, it's free and simple
to install.  If you are using **Ubuntu 16.04** or newer:

    sudo snap install tzgrid


Older Ubuntu or non-Ubuntu?
-------

Head over to the [snapstore page][7] for tzgrid to see more instructions
for older Ubuntu or other linux distros.

Mac or Windows?  Well, I think the python module should work, but I
haven't tested.  Let me know via github if you try.


More Information
----

 * `tzgrid` [github page][4]
 * `tzgrid` [snapstore page][7]
 * `tzgrid --help` -- after you install


[1]: https://www.linkedin.com/in/david-britton-6b88818/
[2]: https://canonical.com/
[3]: https://ubuntu.com/server
[4]: https://github.com/dpb1/tzgrid
[5]: https://www.iana.org/time-zones
[6]: https://worldtimebuddy.com
[7]: https://snapcraft.io/tzgrid

