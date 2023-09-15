---
layout: default
---

Welcome to GBot! A multi-server Discord bot, Dockerized and written in Python! GBot utilizes Google Firebase Realtime Database to save server and user data. Spice up your Discord server today!

## Main Features

#### <ins>Configuration Settings</ins>
- Enable or disable any of the features described below to your liking (Hype, GCoin, GTrade, Storms, Who Dis, Music).
- All commands are slash commands, however you can enable legacy prefix support to allow commands to be triggered with a prefix.
- Ability to configure an admin role & channel for admin notifications/user reports, a channel for Storm mini-games, a role for 'Who Dis?' participants, and a desired command prefix.

#### <ins>Automated & Randomized Reactions & Replies</ins> (Hype)
- Utilize and configure regular expressions to match against incoming messages to automate replies and reactions.
- Provide multiple replies or reactions for one regular expression to randomize the bot's response.

#### <ins>Currency & User Items</ins> (GCoin & GTrade)
- Every user can earn, spend, and send their GCoin balance the way they want to.
- A user's GCoin balance is carried across all Discord servers and not just limited to one server.
- Create image items and trade them with other users across all Discord servers (more coming soon).

#### <ins>Mini-Games</ins>
- Random Storm mini-games where you guess or bet on a random number from 1-200 to win GCoin.
  - In addtion to enabling Storms functionality, a channel must be configured for incoming Storms for the mini-game work.
- 'Who Dis?' mini-games where you guess a random user in the server you are anonymously paired with to win GCoin.
  - In addtion to enabling 'Who Dis?' functionality, a role must be configured for GBot to know which users are opted into 'Who Dis?'.
- Mini-games that reward users with GCoin require GCoin functionality to be enabled.

#### <ins>Music Bot</ins>
- Ability to play sounds downloaded from YouTube to your active voice channel by providing a URL or generic description.
- Type less! Use Spotify activity syncing functionality to add songs playing in your Spotify activity to the bot's music queue.

#### <ins>Patreon Subscription Model</ins>
- In order to have access to GBot, you must be in a Discord server subscribed to GBot.
- GBot will leave Discord servers that are not subscribed. When GBot leaves a server, all server configuration settings will be lost.
- To add GBot to a Discord server, you must subscribe to the [GBot patreon tier here](https://www.patreon.com/StormerG). You will be prompted to join the GBot Patreon Discord Server with your Patreon-linked Discord account where you will register the desired Discord server.