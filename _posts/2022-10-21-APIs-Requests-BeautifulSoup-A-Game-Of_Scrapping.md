---
layout: post
title:  "APIs, Requests, and Beautiful Soup: A Game of Scrapping"
date:   2022-10-21
author: Spencer Young
description: My experience using Steam’s API, Requests, and Beautiful Soup to gather data to compare games made in Unity game engine vs. Unreal engine.
image: /assets/images/TutorialPhotos/CodePhoto.png
---

# The Game Begins

Data surrounds us on every front. It can be found as part of everything we do. Data can lead us to learn about and optimize whatever we love. Something I enjoy doing is playing video games. I have also very recently started making games. While learning some of the basics of game making, I learned about some of the various game engines available. To learn more about these engines, I started looking on the internet. I thought that it would be interesting to compare the reception and popularity of games made in two of the more popular engines: Unity and Unreal. So, I started looking for data about these game engines. This led me to finding some lists on Wikipedia, as well as the Steam API. I will cover my process of getting first the Unity game list, then the Steam game list, followed by the Unreal game list, and finally combining and filtering the data. 

# Unity Engine

For the list of Unity games, I went to the following [link](https://en.wikipedia.org/wiki/List_of_Unity_games). Unfortunately, this list has now been deleted. However, the following code is what I used to get the information. 

[insert code]

I sent a request to the website with the requests library. This enabled me to get all of the html. I then converted the html to a Beautiful Soup object. 
Converting the html to a Beautiful Soup object is preferred because Beautiful Soup (referred to hereafter as BS) has many methods that allow you to search through the html for the information you want. 

After looking at the html, I noticed that the titles for the games all were contained in unordered list elements. This is something that you will want to do when scrapping. By right-clicking the text, you can click “inspect” and see in the html what type of element you desired data is. 

[insert code]

Within the lists, the actual titles of the games were within “a” elements. Every website has a different format, to use the model I used to apply to your own data. The structure may be different, but the principles are the same. Get as unique of elements as possible that describe all of your data, then keep getting more and more descriptive until you can access the data. 


# Steam Game

Getting the Steam games was a different process entirely. Steam has a very nice API that is open to use. The documentation for the API can be found [here](https://partner.steamgames.com/doc/home). The easiest way to get a list of games from Steam, is to get a list of all of the apps available on Steam. 

[insert code]

While this may not be ideal, given the options available, this is the easiest route. This [link](https://stackoverflow.com/questions/46330864/steam-api-all-games) talks more about why. 

With this giant list of games, I needed to filter it down. An important step is to convert the response to a json file. In Python, this will show up as a dictionary. For me, this was a triple-nested dictionary. 

Part of the data cleaning process involves making the data, even data from APIs, usable. For me, I ended looping through the outer dictionary and list so I could convert the inner lists to dictionaries for later use. I also made a list of the Steam games and a list of AppIDs  for later comparison use. 

 ![Figure](https://github.com/SpencerYoung66/stat386-projects/raw/main/assets/images/TutorialPhotos/GitStatusRepo.png)

# Unreal Engine

Next, for the last scrape, I scrapped Wikipedia again for a list of Unreal Engine games from the following link. Unfortunately, this page has also been deleted. Fortunately, however, after my first successful scrape, I saved all of my data to a CSV for later use. 

This is an example of different webpages of the same website being different. The games in this list were stored as tables, instead of unordered lists. This was actually a benefit to me, because it is easier to just get tables with pandas than to use requests and BS.

The tables were stored as a list of DataFrames. So, I looped through this list and combined all the DataFrames.

I then proceeded to filter my complete DataFrame to erase missing platforms, only get PC games, and get rid of games that hadn’t released yet. I continued to clean my data, as was best to do while getting the data. 


1.	Saved 
2.	Added to Staging Area
3.	Committed to Git


# Combining Unity and Unreal

To combine the two lists of games, I used the property of sets known as intersection. By converting the two lists of games to sets and comparing those with the set of games from Steam, I could get all of the games that Steam had and that were also in the Unreal and Unity lists. 

Then, with my finished game list and appID list (which I was able to make due to having the game list), I was able to make a DataFrame with these two lists.


# Getting Game Review Info

Now, with a DataFrame with game title and appID, I could request the information from Steam’s API for the ratings and reviews of the games. So, using a slightly different endpoint for the API than before (shown [here](https://stackoverflow.com/questions/53451458/get-positive-and-negative-review-from-steam-api)), I got the total ratings, positive ratings, negative ratings, review scores, and review score descriptions for each game. 

From the number of total reviews, it is possible to estimate the number of units sold for the game, as described by [vginsights](https://vginsights.com/insights/article/how-to-estimate-steam-video-game-sales). To be safe, I used 20 times the number of reviews, instead of 30 like the link says, because the multiplier was trending downwards, and the article is a couple years old. I also added the engine of the game to the DataFrame. With all of this data, I finally had my data. I saved to it a CSV, which I did not realize would be such an important step until the time of writing. 


# The Game Ends

Finally, after all of the different scrapping techniques employed, I have my dataset. While I did not realize when starting, this project would be important to help preserve some of the information about these games that has now been lost. In a future blog post I will be analyzing this data to see how Unity vs. Unreal compare. If you are interested in seeing the code used for this post, or the data created, check out my GitHub repository [here](https://git-scm.com/docs).


#### Title Photo
Photo by Mohammad Rahmani on Unsplash 
  


