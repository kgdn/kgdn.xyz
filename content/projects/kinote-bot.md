+++
title = 'Kinote'
summary = 'Multi-purpose, multi-media Discord bot'
description = 'Multi-purpose, multi-media Discord bot'
+++

# Introduction

Kinote (Kino + Note) is a work-in-progress, asynchronous Discord bot that I am developing for several Discord servers, one with hundreds of users. The bot is designed to be multi-purpose and support multiple servers at a time, with features such as music playback, managing film watchlists, getting the latest xkcd comic, and more. The bot interacts with the Discord API using the discord.py library, the [TMDb API](https://www.themoviedb.org/?language=en-GB) for film data, and uses a PostgreSQL database to store data, and Redis/Valkey for caching.

# Technologies Used

- **Programming Language**: Python 3.12
- **Libraries**: discord.py
- **Database**: Any database supported by SQLAlchemy, SQLite3 used for development and testing, PostgreSQL used for production
- **Cache**: Redis/Valkey
- **Media Playback**: Lavalink
- **Deployment**: Docker, Docker Compose

# Basic Features

- **Music Playback**: Play music from YouTube
- **Film Watchlist**: Add, remove, and view films in a watchlist
- **xkcd Comic**: Get the latest xkcd comic
- **Interactive Commands**: Use reactions to interact with other users
- **Unix Timestamps**: Convert between Unix timestamps and human-readable dates
- **Cowsay**: Generate ASCII art of a cow saying a message
- **Dice Roller**: Roll dice with custom sides and number of dice
- **Birthday Reminder**: Set and view birthday reminders for users in the server