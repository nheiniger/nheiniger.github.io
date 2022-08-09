---
layout: post
title:  "Using python to plot hiking maps"
date:   2022-08-08 12:00:00 +0000
categories: [ Misc ]
tags: [ python, folium, hiking, geek, gps, en ]
---
TL;DR: Look at the Jupyter notebook here <https://github.com/nheiniger/gpx-presenter>, it shows what I did to map my GPS data.

I've been using [Gaia GPS](https://www.gaiagps.com) to track my hikes from my mobile phone for a while now. One feature that I like a lot is the ability to display a map with all hikes shown in colors. For me it's more than a hundred hikes over the last 4 years. After someone showed me a map of their runs and hikes and bike tours on the web I thought that this shouldn't be too hard to do for myself too. And here I am :)

First, let's give credit where it's due, most of my code is adapted from the work presented here: <https://towardsdatascience.com/build-interactive-gps-activity-maps-from-gpx-files-using-folium-cf9eebba1fe7>. I've improved the code to be able to plot TCX files too. This includes the heart rate data and gives nice maps showing on which part of the track I was really suffering!

If you don't want to read the code -- but I encourage you to do it -- I used [folium](https://python-visualization.github.io/folium) to build maps based on the data parsed by [gpxpy](https://github.com/tkrajina/gpxpy) and [tcxparser](https://github.com/vkurup/python-tcxparser). The end result can be an HTML page with a single track (I use it to plot the last track only). For TCX files it looks like this with the heart rate data:
![TCX map at la dent de Morcles](/images/2022-08-09_dent-de-morcles.png)

The other option is to map all the tracks in a single HTML file:
![All my example tracks mapped](/images/2022-08-09_all-tracks.png)
Here we also see that we can change the background map. By default I like the black and white Swiss topographic map but other options can be chosen too. It's also possible to filter the tracks by year.

One last feature is the statistics about the track, when clicking on the path, some data are displayed:
![Tooltip with some statistics](/images/2022-08-09_tooltip.png)

Note that those are computed by the parsing libraries and can be quite inaccurate, especially when the GPS data is not perfect. Going through tunnels or doing climbs on via ferrata are some examples I've had where the statistics are completely wrong.

Overall I'm happy with the results and it now runs on my private web server. I can easily upload the tracks via SSH and regenerate a new map via a script.
