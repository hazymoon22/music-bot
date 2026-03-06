# Music Bot

A simple Discord music bot built with Node.js, `discord.js` (v12), and `ytdl-core`.

## Features

- Joins a voice channel and streams audio from a YouTube URL
- Uses a default YouTube track at startup
- Lets users change the current URL with a command
- Shows the current song title and URL
- Includes a help command with available bot actions

## Requirements

- Node.js 14+ (recommended for this dependency set)
- A Discord bot token
- Bot permissions in your server:
  - `CONNECT`
  - `SPEAK`

## Installation

```bash
npm install
```

## Configuration

Set these environment variables before starting the bot:

- `TOKEN`: your Discord bot token
- `PREFIX`: command prefix (example: `!`)

Example:

```bash
export TOKEN="your_discord_bot_token"
export PREFIX="!"
```

## Run

```bash
node client.js
```

When the bot is ready, it logs `Ready!`.

## Commands

Assuming `PREFIX="!"`:

- `!play`: join your current voice channel and start playback
- `!stop`: leave the voice channel and stop playback
- `!url <youtube_url>`: change the active YouTube source
- `!song`: show current song title and URL
- `!help`: show command help

## Project Structure

- `client.js`: Discord client setup and command routing
- `music_bot.js`: music bot logic (playback, URL update, help, status)
- `emoji.json`: emoji strings used in chat responses

## Notes

- The bot holds one active voice connection at a time.
- Playback is looped by replaying the same URL after each finish event.
- A minimal HTTP server runs on port `3000` and returns `ok` (useful for simple uptime checks).

## Troubleshooting

- If `play` does nothing, make sure you are in a voice channel.
- If permissions fail, verify the bot can `CONNECT` and `SPEAK` in that channel.
- If a URL fails, confirm it is a valid YouTube URL accessible by `ytdl-core`.
