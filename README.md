# Strava
Analysis of my personal Strava data (running). 
**Please note - this repository is written in a form of stream of consciousness. i.e. As I write it I am taking steps in order as I did them.**

This repository contains my Strava data (running only) exported from the app to Excel. I wanted to use the data as a source for learning more about functions and in particular if I could extract any findings from the data.

The downloaded data is attached. 

My first step was to clean the data by creating a copy into a new sheet, and filtering the data by activity type to remove non-running activities. 

I used a filter to highlight all the non-running data (using the activity column) and then use the Find and Select, Go to special, visisble cells only - then I could safely delete all non-running data. 

I then removed columns where there was either no data or the data wasn't relevant.

I wanted to find out the following:

* On which day of the week have I run most often?
* On which day of the week have I run the most miles?
* On which day of the week was I, on average, running the fastest?
* Do I run more in the evening than the morning?
* How has my running behaviour and performance changed over time - noting that between 2016 and 2019 I had to largely stop running due to injuries?


The first challenge is that the data is not in a format that is easily interrogable. For example dates are expressed in the spreadshet as Apr 24, 2016, 9:09:53 AM. 

However, there's clearly a pattern we can use.

So what I want to do is find a way to extract the AM or PM from the date and add that into a separate column. 

I also want to use the date and find a mechanism to grab the day of the week. That way I can then think about counting how many runs, distance and pace I run at per day of the week.

