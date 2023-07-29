<h1 align="center">ModMail</h1>
<p align="center"><img src="icon.png" width="128"></p>
<p align="center"><i>A Discord bot for members to contact the staff of a server.</i></p>
<p align="center">
<a href="https://github.com/BrackeysBot/ModMail/releases"><img src="https://img.shields.io/github/v/release/BrackeysBot/ModMail?include_prereleases&style=flat-square"></a>
<a href="https://github.com/BrackeysBot/ModMail/actions/workflows/dotnet.yml"><img src="https://img.shields.io/github/actions/workflow/status/BrackeysBot/ModMail/dotnet.yml?branch=main&style=flat-square" alt="GitHub Workflow Status" title="GitHub Workflow Status"></a>
<a href="https://github.com/BrackeysBot/ModMail/issues"><img src="https://img.shields.io/github/issues/BrackeysBot/ModMail?style=flat-square" alt="GitHub Issues" title="GitHub Issues"></a>
<a href="https://github.com/BrackeysBot/ModMail/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/BrackeysBot/ModMail?style=flat-square" alt="MIT License" title="MIT License"></a>
</p>

## About
We all know ModMail. It's a bot that allows members to contact the staff of a server discreetly. This is a custom
implementation of ModMail, written in C# using the [DSharpPlus](https://github.com/DSharpPlus/DSharpPlus) library.

## Installing and configuring ModMail
ModMail runs in a Docker container. There is a [docker-compose.yml](docker-compose.yml) file which simplifies this
process, but you can also run the container manually. The `DISCORD_TOKEN` environment variable is required for the bot
to authenticate. Two persistent volumes should be set up which point to the container's **/app/data** directory and
**/app/logs** directory. The **/app/data** directory contains the SQLite database file and config file, and the
**/app/logs** directory contains the log files. Log files are stored in a format similar to a Minecraft server, where
the log file is rotated every day and compressed. The current log file is always named **latest.log**.

### Setting things up
Copy the example `config.example.json` to and bind it to `/app/data/config.jon`. The following is a breakdown of the
config file schema:
```json
{
  "GUILD_ID": {
    "logChannel": /* The ID of the log channel */,
    "modMailCategory": /* The ID of the category where ModMail channels will be created */,
    "prefix": /* The prefix used to invoke bot commands */,
  }
}
```

## License
This bot is under the [MIT License](LICENSE.md).

## Disclaimer
This bot is tailored for use within the [Brackeys Discord server](https://discord.gg/brackeys). While this bot is open
source and you are free to use it in your own servers, you accept responsibility for any mishaps which may arise from
the use of this software. Use at your own risk.