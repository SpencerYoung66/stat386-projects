---
layout: post
title:  "\"Choose Your Fighter\": Analysis of Reviews Between Unity and Unreal Engines"
date:   2022-12-05
author: Spencer Young
description: Final Analysis of Games made in Unity vs. Unreal
image: /assets/images/DataStory/Controller.png
---

# Meet the Fighters

One of the biggest media industries in the current day and age is that of video games. While most gamers have only been able to play games, engines to develop games have become increasingly available. With these engines available, many gamers who want to turn their hobby into a career suddenly have the means to. However, the question becomes where to start, specifically which engine to develop with. While there are many more than just these, the engines I will focus on in this blog post are Unity and Unreal. While both engines are used for all kinds of games, a quick Google search shows that the most popular games in Unity tend to be Indie titles, while the most popular games made in Unreal tend to be AAA games.  

Over the course of the past few blog posts, I have collected and done exploratory analysis on data related to video games made in these engines. I started with finding Wikipedia pages that contain lists of games made in Unity and Unreal. Unfortunately, those lists are both gone now. Then, I used the Steam API to get the information related to those games. After some data cleaning and additional gathering, I performed an exploratory data analysis. To me, the most meaningful metrics available are which engine was used (obviously), how much the game costs, and the number of positive vs. negative reviews. 


# Comparing Games by Engine, Price, and Reviews

Now, the moment we've all been waiting for, time to see how Unity and Unreal compare in regard to price and reviews. Reviews is an important indicator because the number of reviews a game has is strongly related to how many copies of the game have been sold (see [vginsights](https://vginsights.com/insights/article/how-to-estimate-steam-video-game-sales) for a more in-depth explanation). Because Steam does not release the number of copies sold, the closest we can get is looking at the number of reviews. This graph shows the relationship between game engine, price, and median amount of reviews.

![Figure](https://github.com/SpencerYoung66/stat386-projects/raw/main/assets/images/DataStory/PriceEngineReviewGraph.png)

As can be seen in the graph, the number of reviews for games made with Unity have an overall higher amount of median reviews for the lower price buckets. This supports the assumption already described, which is that the most popular Unity games tend to be Indie games that inevitably cost less. Then, as the price increases, we see a massive increase in Unreal game reviews, and a decrease in Unity game reviews. 

While this is not an exhaustive list of games made in either engine, the trend shows that Unity is favored by Indie game makers (who tend to have cheaper games), while Unreal is preferred by bigger studios. It could be beneficial for a person to start developing in Unity and eventually move towards Unreal if the goal is to work with bigger companies. However, which engine is used by the new game developer should be decided by their goals. If they only want to work with a big company, then maybe they should dive right into Unreal to get the experience. If they want to make Indie games, then they should consider starting with Unity. 

If you are interested in checking out this data for yourself, or seeing the code used to make this graph, check out the GitHub repo [here](https://github.com/SpencerYoung66/UnityUnrealSteamData).


#### Title Photo
Photo by Igor Karimov on Unsplash
  
  



