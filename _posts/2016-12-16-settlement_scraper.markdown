---
layout: post
title:  "Settlement Scraper"
date:   2016-12-16 06:04:18 +0000
---


Settlement Scraper is a tool that scrapes a list of class action settlements from an external source and allows you to quickly see which settlements you may qualify to file a claim for.

This requires using Nokogiri to pull the external data and then choosing the correct CSS selectors to extract the needed data. 

One of the biggest challenges was allowing the CLI to switch between the list view and the detail view. This required class variables to allow the program to remember what was last on the screen when switching views. 

Another big problem was breaking the list down into "pages," because the full list has too much information to display all at once. The program creates a new "page" for every 5 items in the list. When switching between the list view and detail view, it was challenging getting the program to remember which "page" it was on, and to display the correct index number for each item (instead of starting over from 1).

When switching from detail view back to list view, the program makes a recursive call to the method that displays the settlements, and uses class variables to remember which items should be displayed. The recursive calls presented a problem for the "while" loops that prompt the user for input. When exiting the recursive calls, the program would repeatedly prompt for input for each call. This was resolved by using a class variable to tell the "while" loops to exit and not prompt for input when exiting the recursive calls.

A big limitation of the program is that the external source I'm using is slow to load. Initially, I scraped everything on start up and it took a very long time for the program to load. I changed it to only scrape what's needed at the given moment, so the details of a settlement aren't scraped unless you select the detail view. Of course, the user would then have to wait for the detail view to load. Perhaps the next version of my program will allow it to scrape data in the background so the loading is not noticeable to the user.
