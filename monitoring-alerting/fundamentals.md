# Monitoring and Alerting Fundamentals 

_notes from fundamentals of monitoring and alerting by sean allen [(abstract)](http://conferences.oreilly.com/velocity/devops-web-performance-ny-2015/public/schedule/detail/45348)_

collect information that you can use later on (some people use more info than others)

most important thing to remember is that there is a cost to any system you put in place. (not just financial—people have to maintain those systems). 

small teams need to be able to support the system, the information needs to be the be what’s most important. (you don’t need to monitor everything)

“what is it do you need to know? what do you need to be made sure it works”
^ thats what you need to monitor

You can collect all the info you want but you need to think about WHY you care about this? 

Some file might be growing huge but if it’s not affecting anything else, why monitor it? (Ups carrying cost). Plenty of other things important to monitor.

two real philosophies about what to monitor:

1. monitor everything that you possibly can (costly, many systems required, , lots of people to maintain them, monitor a WIDE variety of things) “more data you have, more difficult to correlate"
2. Picking your really important things you want to know. (ex, if you are sending emails, you want to know they are going out/coming in). Then expand and go past that

“is my site up and running?” -> pingdom
“is my site up and actually functioning?” -> something that walks through critical paths (selenium, etc)

Top level problem: my site isn’t running (Signals an issue)
Bottom levels get more into the WHY of the problem.

Example in talk was the web team knew that something was wrong with the database whenever they were seeing massive spike in DB connection resets. Web team knew before database team. DB teams monitoring alerts hadn’t gone off yet. Bottom level monitoring needed to be adjusted.

measure the right metrics. yeah the site is up and running, but if it’s taking 3 minutes to bring up the page, the end user isn’t going to feel like it’s working.

Come up with SLAs. Be careful of what you’re actually monitoring. just measuring http response isn’t an accurate representation of what the user sees.how long does a PAGE LOAD take is a better metric.

if you are trying to make sure your metrics are from a customer standpoint, make sure you are actually taking those metrics

logs useful for monitoring AND debugging

Log history can help you track if it’s a new issue or an issue that’s been re-occurring but you missed it before (or due to technical debt) and is “normal”. Especially helpful in computer fires.

Centralized store for logs + way to search them is important. 

saved searches + running them overtime in a log cumulation tool. essentially a monitoring tool. if i see x y times over z timeperiod, raise an alert. can be a real problem if situations change by time.

Database monitoring - can you put the data in and pull it out? Am I getting the performance out of my queries? Am I able to connect to the DB? ANything more specific is what you need to solve problems when things could go wrong.

coda hale’s metrics: https://github.com/codahale/metrics / https://godoc.org/github.com/codahale/metrics

application metrics: for example, web apps: response time, percentiles.

#### Anomaly detection:
There are some services available for this
Best anomaly detection is a human being with access to a LOT of data to correlate
If you put enough data at the hands of people, the more info they have, and they watch what’s going on, visualizations of the errors, people get in sync with how your systems normally run.

**determine WHEN to alert to a problem**

alerts need to be informative so that you know what to fix right away, not wait a while figuring out

**#1 rule of alerting, never send an alert if a human being can’t do something about it.**

if some alerts are ignorable, you run the risk of people ignoring ALL them

There’s a balance though that must be achieved. Some of these things that can’t be fixed are indicative of things being on fire. So strictly adhering to the rule may make you miss something everything, but sending alerts for everything trains people to ignore the alerts.

Can tier alerts by priority/impact. Different responses to the alerting, some alerts wake people up, some just go to pager, etc.

Can be more liberal in alerting during peak and/or work hours, use caution outside those hours.

PagerDuty: Setup rotations for who gets alerted, has escalations/fallbacks in case they don’t respond. 

Can send alerts to phone, email, etc. depending on severity.

Waking people up in the middle of the night can have costs like super tired people during work hours which cuts down on productivity!

Alerts should be informative of how to resolve it, especially in the case that someone is trying to fix an issue in the middle of the night. For instance, “foo is on fire” alert should contain documentation for “what to do when foo is on fire”

Make sure the person who is on call can handle everything, has all the accounts/permissions possibly needed. FIND OUT BEFORE THIS HAPPENS!

Technical problems are not hard to solve, people ones are. Like all areas of tech, the hardest problems are the people ones to solve. For example: who decides who to alert who and when? Requires empathy. Things get fixed a lot quicker when people understand exactly what’s going on and multiple teams/areas are involved.

Good monitoring is important and should be in place before something new. Even if that new thing is tested and passing tests, without good monitoring ahead of time, you might miss some serious errors when you put up said new thing.

Before you invest time in anything beyond basic testing, invest in monitoring. Especially for all critical points in the system.

When tons of things go wrong but it doesn’t affect the things that make money, it has less of an impact.

### How Not to Measure Latency by Gil Tene (https://www.youtube.com/watch?v=lJ8ydIuPFeU):

I was going to write notes but I think this blog post: http://highscalability.com/blog/2015/10/5/your-load-generator-is-probably-lying-to-you-take-the-red-pi.html covers most of the important stuff. 

Some highlights from the video and the post:

95% charts hide 5% of the story, often the most important part of the story. 95% is not good for monitoring systems. Especially relevant for latency systems where we want the whole story.

Never get rid of the maximum value! (the rest is noise).

Can’t average percentiles! These “statistics” are misleading.

It’s a misconception that 99%ile experiences are rare.

99.9% seems too high to measure but it enough of a common experience that 95% is a lie.

Medians are pointless metrics for response times.
