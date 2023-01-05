# Seita data engineering assignment

Thanks for taking the time to apply at Seita Energy Flexibility! This task is the technical part of the application procedure.

This task hopefully takes not more than half a day. What we really want is to discuss the results and your choices. You can stop after half a day ― we'll be interested in discussing how well you spent that time, looking at usable results.

The task tests some data engineering (understanding and querying data mainly), but as we build software that runs in the wild on a daily basis, and we do that in a team, it also tests your software engineering skills.

## Form

We'd like you to put your code in a git repository on the web. This can be Github, Gitlab or Bitbucket etc.
Great if it's public (putting yourself out there is good!) but if you can't, then we prefer a closed repository on Github, where you add our accounts so we are able to read.

The code should be self-contained, apart from dependencies.
There should be a Readme telling us what to see and do.

## The task

We want you to build two API endpoints for GETting weather information.
We have prepared [a dataset with weather forecasts in CSV](weather.csv) to be used. It contains forecasts for temperature, wind speed, irradiance - up to 48 hours in advance.

As target audience, you can think about frontend developers wanting to show the responses to users. They don't know Python.

You have free choice of tooling (libraries / frameworks), as long as you use Python3.

You might choose to (partially) use the stack we are developing within Seita (it's open source and documented), but you don't have to.
It might save you some time, though, but of course learning it costs some time, as well. Most of all, we want you to deliver something that works, so we can discuss it.
Options are to look at timely-beliefs for data representation and FlexMeasures for embedding an endpoint (here you'd probably develop a FlexMeasures plugin).

## Endpoint 1: GET /forecasts

Given two parameters ("now" and "then", both datetimes), return the three kinds of forecasts that are most relevant for "then", given the knowledge at "now".

Note: The ``belief_horizon`` field matters here. It tells you how much earlier the forecast for a specific time slot (``event_start``) was made.

## Endpoint 2: GET /tomorrow

Given one parameter "now", a datetime, return three booleans, telling us if the next day (the one after "now") is expected to be "warm", "sunny" and "windy".
Use three internal thresholds to determine the answer and you can also decide if the threshold (likely) being breached once is already enough for the boolean to be true.

## Deliverables

What will we take into consideration when we rate this assignment?

* The first priority is of course that the logic behaves correctly (input leads to the correct output). But there are more priorities, and they do matter a lot for successful software development, see below.
* The endpoints should be demonstratable by you. But they should also be easy to start up for us (to see if they work). So please include clear instructions for somebdy who is not you how to run this toy application (this begins with installing dependencies).
* Both endpoints need clear documentation for users (think of the frontend developers mentioned above), at least in the docstring. How to use, how input looks like, what to expect if things go well and what if they don't.
* Testing is crucial. Time might not allow you to test all aspects, but please provide unit tests which test the basic behaviour. They should use dummy test data, not the real data.
