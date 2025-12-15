---
title: "This Week in Music"
date: 2025-12-15
draft: true
type: 'blog'
featured: true
tags: 
  - machinelearning
  - programming
  - personal
---

I love listening to concerts, but it's often tough to find concerts, let alone decide if I think it's worth it to spend my time and money to go and support new artists. Luckily there are plenty of city-specific websites that have info on upcoming concerts! My idea was simple: write a program that would load the artists for the next week and make a Spotify playlist using [spotipy](https://spotipy.readthedocs.io/en/2.25.2/). Easy enough, right?

## Unfortunately We Need an LLM
Well, not exactly an LLM by 2025 standards, but we do need a model that can be adapted to understand band names. This is an issue because the formatting of artists is remarkably inconsistent. For example:

 > Australian punk night presents: THE CHATS / COSMIC PSYCHOS / THE SCHIZOPHONICS

Is hard to parse because there's text at the beginning, the bands are separated from each other by slashes, and they're in all caps. None of this is guaranteed to be consistent, so I finetuned a BERT model to identify these band names. By using a pretrained network, all I had to do was label a few hundred band names (plenty of podcasts were consumed during this) and without too much training, I had a model that could find band names that I could run on my local machine!

## Making the Playlist
Making the actual playlist presented more problems than I initially accounted for. For one, there are way more artists than you would want to stuff in a playlist. Ulimately, I landed on using 100 songs, with the top 15 artists (from Spotify's metrics) getting 3 songs each, and 55 random artists getting one song. The goal of this project is to be one part music discovery and one part informative. I think this allows smaller artists to be discovered while highlighting bigger artists so you know who's playing in your city. I don't think this is a perfect system but I've found plenty of artists so far that I've enjoyed listening to. 

## What's Next?
At this point, there are many options for the TWiM project. What I'm focusing on now is generating more focused playlists. The current playlists tend to be weighted towards specific genres as well as big artists that I don't enjoy as much. For example, it's much easier to find country music in Austin and it tends to flood the list with smaller country artists. 

A huge opportunity is personalization, which I'm currently testing with my profile. There's no reason to look out over a period of 3-6 months and find artists that I like so I can build a playlist that has music I already listen. This fulfills the "informative" mandate. However, I can also begin to aggregate a personal profile and find new artists that fit this profile. 

If you like this idea, please give the playlist a listen or a follow!