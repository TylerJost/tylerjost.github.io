---
title: "This Week in Music (TWiM)"
date: 2025-12-20
draft: false
type: 'blog'
featured: true
tags: 
  - machinelearning
  - programming
  - personal
---

I love listening to concerts, but it's often tough to find bands playing in time to buy tickets, let alone decide if I think it's worth it to spend my time and money to go and support new artists. So I built TWiM, a tool that finds concerts and builds playlists for them automatically. Fortunately for me, there are plenty of city-specific websites that have info on upcoming concerts! My idea was simple: write a program that would load the artists for the next week and make a Spotify playlist using [spotipy](https://spotipy.readthedocs.io/en/2.25.2/). Easy enough, right?

## Unfortunately We Need an LLM
Well, not exactly an LLM by 2025 standards, but we do need a model that can be adapted to understand band names. This is an issue because the formatting of artists is remarkably inconsistent. For example:

 > Australian punk night presents: THE CHATS / COSMIC PSYCHOS / THE SCHIZOPHONICS

This is challenging to parse with traditional methods because there's text at the beginning, the bands are separated from each other by slashes, and they're in all caps. None of this is guaranteed to be consistent, which further complicates the problem. At this point, this project graduates from a simple task to a named entity recognition (NER) problem. Even though this seems daunting, all I really had to do was download a pretrained network and adapt it to figure out what parts of a sentence belonged to an artist. After labeling a few hundred band names (plenty of podcasts were consumed during this) and without too much training, I had a model that could find band names that I could run on my local machine. This ends up being a robust solution: a small, locally hosted language model that is flexible to all kinds of inputs. It runs incredibly quickly, even on older hardware and had a >90% precision on my holdout set. 

## Making the Playlist
Making the actual playlist presented more problems than I initially accounted for. For one, there are way more artists than you would want to stuff in a playlist. Ulimately, I landed on using 100 songs, with the top 15 artists (from Spotify's metrics) getting 3 songs each, and 55 random artists getting one song. The goal of this project is to be one part music discovery and one part informative. I find this allows smaller artists to be discovered while highlighting bigger artists so you know who's playing in your city. I don't think this is a perfect system but I've found plenty of artists so far that I've enjoyed listening to. 

## What's Next?
At this point, there are many options for the TWiM project. The first goal is to generate more focused playlists. The current playlists tend to be weighted towards specific genres as well as big artists that I don't enjoy as much. For example, it's much easier to find country music in Austin and it tends to flood the list with smaller country artists. 

A huge opportunity is personalization, which I'm currently testing with my profile. There's no reason to not look out over a longer period of 3-6 months and find artists that I like so I can build a playlist that has music I already listen. This fulfills the "informative" mandate. However, I can also begin to aggregate a personal profile and find new artists that fit this profile. 

## Music Discovery With Less Algorithms
The music discovery aspect of this project is actually an emergent feature of this project. When I first started looking for a way to compile upcoming artists into a playlist, I mostly was thinking about how I didn't want to miss out on another concert. However, every week or so I find a new artist with a song I really enjoy and end up adding to my liked songs. 

The idea of "algorithmless" music discovery doesn't really make sense to me. I understand the desire to not be stuck in the same handful of songs, which undeniably happens all the time on Spotify. I think the TWiM project strikes a good balance here. The algorithm is completely transparent in how music is selected, enabling new music to be discovered without limitations on artist popularity or other unseen metrics. A final challenge for this project will be striking a better balance between 3 categories of artists that appear: huge artists with millions of plays, upcoming artists who are just gaining traction, and complete unknowns.

If you like this idea, please give the playlist a listen or a follow! You can find the playlists on my website using [TWiM tab](https://jost.engineer/twim/) or access the [Boston shows](https://open.spotify.com/playlist/1dMrLRiRtzAq1Ad9Mx6A95?si=f6ab2e97bbd34f68) or [Austin shows](https://open.spotify.com/playlist/7oWlCMpyEMTjvu1GwIoDMN?si=705b111c456e4e53) directly using the provided links. If you want to see some of the code, check out my GitHub repo at https://github.com/TylerJost/twim/. 