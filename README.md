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

I also wanted to use the date and find a mechanism to grab the day of the week. That way I can then think about counting how many runs, distance and pace I run at per day of the week.

## BIG PROBLEM NUMBER 1.

So I spent hours trying to convert Apr 24, 2016, 9:09:53 AM into a date format I could use. I tried variations on grabbing bits of the text string (=LEFT, =RIGHT, =MID) and then re-assembling using "&-" but could not get it to work. I also tried to use =datevalue but that kept returning an error.

In the end I turned to Twitter and Slack. And quickly got a result....

Ben Smith, a mutual follower on Twitter, sent me this: "=DATEVALUE(MID(A1,5,2)&"-"&MID(A1,1,3)&"-"&MID(A1,9,4))"

Essentially that function forces a date value from a string, and the use of MID with &"-" assembled the text into a string the function could recognise! 

The only manual built was having to adjust the function where the date was a single character rather than two. i.e. "1" rather than "10". That meant I had to adjust where MID was pulling the text.

Two and a half hours later and I was close to having a spreadsheet I could actually query!

## BIG PROBLEM NUMBER 2

Now I had my dates expressed as, for example, Saturday, 8 September 2018 the next problem I had was in counting how many times the days of the week appear. And that's because now the strings are dates Excel doesn't actually see the text it's only aware of the underlying data value.

So this is where I used the =TEXT function. So =TEXT(B2,"DDDD") converts the data in B2 to just a day in text in the cell. Now I had a list of all the days of the week I had run.

This then meant I could use =COUNTIF. And from that I could asily see that Sunday is my most regular day to run while Thursday is my least typical day to run. 

Progress!

## BIG PROBLEM NUMBER 3

So I've built some pivot tables to analyse my data by day of the week, and by year. And I realised something... there's a lot of missing data. A quick investigation into why my 2015 data looked so thin and it became obvious: I wasn't really using Strave for a period of time in 2015. So where was it?

