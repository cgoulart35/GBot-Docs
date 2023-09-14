# GBot 7.0
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

## Command Glossary
![Alt text](<Slash Commands Animation.gif>)
#### <ins>Config</ins>
<details>
<summary>Click to expand Config commands.</summary>

  *   <details>
      <summary>.channel</summary>

      *  Description:
         * `Set the channel for a specific GBot feature in this server. (admin only)`
      *  Syntax:
         * `.[channel|ch] <channel_type> <channel>`
         * `channel_type options are: admin, storms`
      *  Example:
         * `.ch admin #admin-channel`
      </details>

  *   <details>
      <summary>.config</summary>

      *  Description:
         * `Shows the server's current GBot configuration. (admin only)`
      *  Syntax:
         * `.[config|c]`
      *  Example:
         * `.c`
      </details>

  *   <details>
      <summary>.prefix</summary>

      *  Description:
         * `Set the prefix for all GBot commands used in this server. (admin only)`
      *  Syntax:
         * `.[prefix|pr] <prefix>`
      *  Example:
         * `.pr .`
      </details>

  *   <details>
      <summary>.role</summary>

      *  Description:
         * `Set the role for a specific GBot feature in this server. (admin only)`
      *  Syntax:
         * `.[role|rl] <role_type> <role>`
         * `role_type options are: admin`
      *  Example:
         * `.rl admin @Admin`
      </details>

  *   <details>
      <summary>.toggle</summary>

      *  Description:
         * `Turn on/off all functionality for a GBot feature in this server. (admin only)`
      *  Syntax:
         * `.[toggle|t] <feature_type>`
         * `feature_type options are: gcoin, gtrade, hype, music, storms, 'who dis', 'legacy prefix commands'`
      *  Example:
         * `.t hype`
      </details>
</details>
  
#### <ins>GCoin</ins>
<details>
<summary>Click to expand GCoin commands.</summary>
  
  *   <details>
      <summary>.history</summary>

      *  Description:
         * `Show your transaction history, or another user's transaction history in this server. Admin role needed to show other user's history. (admin optional)`
      *  Syntax:
         * `.[history|hs] [user]`
      *  Example:
         * `.hs`
         * `.hs @MasterChief`
      </details>
  
  *   <details>
      <summary>.send</summary>

      *  Description:
         * `Send GCoin to another user in this server.`
      *  Syntax:
         * `.[send|sd] <user> <amount>`
      *  Example:
         * `.sd @MasterChief 2.50`
      </details>
  
  *   <details>
      <summary>.wallet</summary>

      *  Description:
         * `Show your wallet, or another user's wallet in this server.`
      *  Syntax:
         * `.[wallet|w] [user]`
      *  Example:
         * `.w`
         * `.w @MasterChief`
      </details>
  
  *   <details>
      <summary>.wallets</summary>

      *  Description:
         * `Show wallets of all users in this server.`
      *  Syntax:
         * `.[wallets|ws]`
      *  Example:
         * `.ws`
      </details>
</details>

#### <ins>GTrade</ins>
<details>
<summary>Click to expand GTrade commands.</summary>

  *   <details>
      <summary>.buy</summary>

      *  Description:
         * `Buy another user's item for sale in the discord server. Create a request to buy from a user, complete a user's pending sell request, or buy an item for sale in the server's market.`
      *  Syntax:
         * `.[buy|by] <user> <item>`
      *  Example:
         * `.by @MasterChief "gravity hammer"`
         * `.buy @MasterChief shield`
      </details>
  
  *   <details>
      <summary>.craft</summary>

      *  Description:
         * `Craft items to show off and trade. Surround name with double quotes if multiple words.`
      *  Syntax:
         * `.[craft|cr] <name> <value> <type>`
         * `type options are: image`
      *  Example:
         * `.cr "gravity hammer" 6.75 image`
         * `.craft shield 6.75 image`
      </details>
  
  *   <details>
      <summary>.destroy</summary>

      *  Description:
         * `Destroy an item in your inventory.`
      *  Syntax:
         * `.[destroy|d] <item>`
      *  Example:
         * `.d "gravity hammer"`
         * `.destroy shield`
      </details>
  
  *   <details>
      <summary>.item</summary>

      *  Description:
         * `Show off an item in your inventory.`
      *  Syntax:
         * `.[item|i] <item>`
      *  Example:
         * `.i "gravity hammer"`
         * `.item shield`
      </details>
  
  *   <details>
      <summary>.items</summary>

      *  Description:
         * `List all items in your inventory, or another user's inventory in this server.`
      *  Syntax:
         * `.[items|is] [user]`
      *  Example:
         * `.is @MasterChief`
      </details>
  
  *   <details>
      <summary>.market</summary>

      *  Description:
         * `Show all market items for sale and personal trade requests in the discord server.`
      *  Syntax:
         * `.[market|m]`
      *  Example:
         * `.m`
      </details>
  
  *   <details>
      <summary>.rename</summary>

      *  Description:
         * `Rename an item in your inventory.`
      *  Syntax:
         * `.[rename|rn] <item> <name>`
      *  Example:
         * `.rn "gravity hammer" gravityHammer`
         * `.rename shield "my shield"`
      </details>
  
  *   <details>
      <summary>.sell</summary>

      *  Description:
         * `Sell an item to another user in this discord server. Create a request to sell to a user, complete a user's pending buy request, or place an item for sale in the server's market.`
      *  Syntax:
         * `.[sell|sl] <item> [user]`
      *  Example:
         * `.sl gravityHammer @MasterChief`
         * `.sell "my shield"`
      </details>
</details>  
  
#### <ins>Music</ins>
<details>
<summary>Click to expand Music commands.</summary>

  *   <details>
      <summary>.elevator</summary>

      *  Description:
         * `Toggle elevator mode to keep the last played sound on repeat.`
      *  Syntax:
         * `.[elevator|e]`
      *  Example:
         * `.e`
      </details>
  
  *   <details>
      <summary>.pause</summary>

      *  Description:
         * `Pauses the current sound being played.`
      *  Syntax:
         * `.[pause|ps]`
      *  Example:
         * `.ps`
      </details>
  
  *   <details>
      <summary>.play</summary>

      *  Description:
         * `Play videos/music downloaded from YouTube. No playlists or livestreams.`
      *  Syntax:
         * `.[play|p] [args...]`
      *  Example:
         * `.p halo theme song`
         * `.play https://youtu.be/dQw4w9WgXcQ`
      </details>
  
  *   <details>
      <summary>.queue</summary>

      *  Description:
         * `Displays the current sounds in queue.`
      *  Syntax:
         * `.[queue|q]`
      *  Example:
         * `.q`
      </details>
  
  *   <details>
      <summary>.resume</summary>

      *  Description:
         * `Resumes the current sound being played.`
      *  Syntax:
         * `.[resume|r]`
      *  Example:
         * `.r`
      </details>
  
  *   <details>
      <summary>.skip</summary>

      *  Description:
         * `Skips the current sound being played.`
      *  Syntax:
         * `.[skip|s]`
      *  Example:
         * `.s`
      </details>
  
  *   <details>
      <summary>.spotify</summary>

      *  Description:
         * `Play current spotify activity downloaded from YouTube. Songs are added to the queue as the user's activity changes.`
      *  Syntax:
         * `.[spotify|sp] [user]`
      *  Example:
         * `.sp`
         * `.spotify @MasterChief`
      </details>

  *   <details>
      <summary>.stop</summary>

      *  Description:
         * `Stops the bot from playing sounds and clears the queue.`
      *  Syntax:
         * `.[stop|st]`
      *  Example:
         * `.st`
      </details>
</details>
  
#### <ins>~~Halo~~ (DISCONTINUED)</ins>
<details>
<summary>Click to expand Halo commands.</summary>

  *   <details>
      <summary>.halo</summary>

      *  ~~Description:~~
         * ~~`Participate in or leave the weekly GBot Halo competition. (admin optional)`~~
      *  ~~Syntax:~~
         * ~~`.[halo|h] [action] [user]`~~
         * ~~`action options are: <gamertag>, rm`~~
      *  ~~Example:~~
         * ~~`.h XboxGamerTag`~~
         * ~~`.h rm`~~
         * ~~`.halo XboxGamerTag @MasterChief`~~
         * ~~`.halo rm @MasterChief`~~
      </details>
</details>
  
#### <ins>Hype</ins>
<details>
<summary>Click to expand Hype commands.</summary>

  *   <details>
      <summary>.hype</summary>

      *  Description:
         * `Set a regular expression to match against new messages in this server, and a list of possible responses to reply to it with. Surround regex and response each with double quotes if multiple words. (admin only)`
      *  Syntax:
         * `.[hype|hy] [regex] [reply]`
      *  Example:
         * `.hy "Hello there!" "General Kenobi!" "You fool! I've been trained in your Jedi arts by Count Dooku."`
         * `.hype "It's over Anakin, I have the high ground." "You underestimate my power!"`
      </details>

  *   <details>
      <summary>.react</summary>

      *  Description:
         * `Set a regular expression to match against new messages in this server, and a list of possible emojis to react to it with. Surround regex with double quotes if multiple words. (admin only)`
      *  Syntax:
         * `.[react|re] [regex] [emoji]`
      *  Example:
         * `.re "How are you feeling?" 😊🙁`
         * `.react "Vrrm vrrm" 🚗`
      </details>

  *   <details>
      <summary>.unmatch</summary>

      *  Description:
         * `Remove an existing regular expression match response in this server. (admin only)`
      *  Syntax:
         * `.[unmatch|um]`
      *  Example:
         * `.unmatch`
      </details>      
</details>

#### <ins>Help</ins>
<details>
<summary>Click to expand Help commands.</summary>

  *   <details>
      <summary>.help</summary>

      *  Description:
         * `Type .help command for more info on a command. You can also type .help category for more info on a category.`
      *  Syntax:
         * `.help [command]`
      *  Example:
         * `.help`
         * `.help GTrade`
         * `.help cr`
      </details>
</details>

#### <ins>Patreon</ins>
<details>
<summary>Click to expand Patreon commands.</summary>

  *   <details>
      <summary>.patreon</summary>

      *  Description:
         * `In the GBot Patreon server, specify a server's ID to enable GBot functionality in that server. (patrons only)`
      *  Syntax:
         * `.[patreon|pt] <server_id>`
      *  Example:
         * `.pt 012345678910111213`
      </details>
</details>

#### <ins>Storms</ins>
<details>
<summary>Click to expand Storms commands.</summary>

  *   <details>
      <summary>.bet</summary>

      *  Description:
         * `Make a guess. If you win, you earn the amount of points bet within your wallet. If you lose, you lose those points. Multiplier applied for guesses made in 4 attempts or less.`
      *  Syntax:
         * `.[bet|b] <gcoin> <number>`
      *  Example:
         * `.b 5.00 65`
      </details>

  *   <details>
      <summary>.guess</summary>

      *  Description:
         * `Make a guess with a winning reward of 1.00 GCoin. Multiplier applied for guesses made in 4 attempts or less.`
      *  Syntax:
         * `.[guess|g] <number>`
      *  Example:
         * `.g 50`
      </details>

  *   <details>
      <summary>.umbrella</summary>

      *  Description:
         * `Start the incoming Storm and earn 0.25 GCoin.`
      *  Syntax:
         * `.[umbrella|u]`
      *  Example:
         * `.u`
      </details>
</details>

#### <ins>Who Dis</ins>
<details>
<summary>Click to expand Who Dis commands.</summary>

  *   <details>
      <summary>.whodis</summary>

      *  Description:
         * `Start or end a mini-game where you try to guess a random user in the server you are paired with. You have 1 guess, and if you guess correctly you earn GCoin.`
      *  Syntax:
         * `.[whodis|wd]`
      *  Example:
         * `.whodis`
      </details>

  *   <details>
      <summary>.dis</summary>

      *  Description:
         * `Guess the name of the user you are paired with for a chance to win GCoin.`
      *  Syntax:
         * `.[dis|ds] <user>`
      *  Example:
         * `.ds jonsnow1234`
      </details>

  *   <details>
      <summary>.leavedis</summary>

      *  Description:
         * `Remove the server's 'Who Dis?' role opting you out of any future games.`
      *  Syntax:
         * `.[leavedis|ld]`
      *  Example:
         * `.ld`
      </details>

  *   <details>
      <summary>.report</summary>

      *  Description:
         * `Report a user to server admins for bad behavior. The reported user's last 5 messages will be captured from the channel sent in, or an ongoing Who Dis game.`
      *  Syntax:
         * `.[report|rp]`
      *  Example:
         * `.report`
         * `.rp @CerseiLannister`
      </details>
</details>

# GBot Development

## Changelog

#### GBot 7.0
- (NEW) <ins>Who Dis</ins> random user chat mini-game functionality

#### GBot 6.0
- <ins>Slash command</ins> functionality for all commmands (Config, GCoin, GTrade, Hype, Music, Patreon, and Storms)
- <ins>Storms</ins> enhancements to show all Storm activity only in the configured channel & purge messages all at once
- <ins>Config</ins> enhancement allowing admins to enable or disable legacy prefix commands in their servers

#### GBot 5.0
- <ins>Storms</ins> (randomly timed mini-games) have returned from [StormBot](https://github.com/cgoulart35/StormBot)
- <ins>Music bot</ins> enhancement to sync music with user Spotify activity

#### GBot 4.0
- GBot <ins>Patreon</ins> member tracking functionality
- <ins>Hype</ins> message regex matcher functionality for automated replies and reactions

#### GBot 3.0
- User-specific <ins>GCoin currency</ins> and transaction functionality
- User-specific <ins>GTrade items</ins> and crafting functionality
- ~~<ins>Halo Infinite</ins> competition enhancement with <ins>GCoin integration</ins>~~ (DISCONTINUED)

#### GBot 2.0
- <ins>Music bot</ins> functionality to play YouTube videos

#### GBot 1.0
- Server-specific <ins>configuration</ins> settings
- ~~Weekly <ins>Halo Infinite competitions</ins> with random challenges~~ (DISCONTINUED)
- ~~Daily <ins>Halo Infinite Message of the Day</ins> checks~~ (DISCONTINUED)

## Setup Guide
1. Clone GBot.
2. Install Docker (and Docker compose if on Linux).
3. Create a [Google Firebase Realtime Database](https://console.firebase.google.com/) project.
4. Create a user for authentication and a service account in project settings.
5. Download the service account key .json file to the GBot/Shared/ directory and rename it to serviceAccountKey.json.
6. Navigate to project settings and copy your Firebase configuration variables into the following json string respectively and save it:
{"apiKey":"","authDomain":"","databaseURL":"","projectId":"","storageBucket":"","messagingSenderId":"","appId":"","measurementId":"","serviceAccount":"/GBot/Shared/serviceAccountKey.json"}
7. Create a Discord bot project in the [Discord Developer Portal](https://discord.com/developers/applications) and save the bot token.
8. Under the Discord bot project's bot settings, enable all intents and add the bot to your server with administrator privileges.
9. Move GBot's role above other roles you create in the server that GBot will assign to server members.
10. ~~Sign up for an Autocode token to utilize the free [Halo API](https://autocode.com/lib/halo/infinite/) service.~~
11. Update the GBot/Shared/gbot.env file with your Discord bot token, ~~Autocode token~~, and Firebase data.
12. Set your preferred time zone (TZ) in the GBot/Shared/gbot.env file. (Ex: TZ=America/New_York)
13. Set your preferred log level for the logged info and error messages. (Ex: LOG_LEVEL=INFO)
14. Set your preferred port for the Quart API to run on. (Ex: API_PORT=5004)
15. Set the Git Project Update Handler URL if you would like to utilize streamlined Git upgrades. (Ex: GIT_UPDATER_HOST=http://\<INSERT-HANDLER-HOSTNAME-AND-PORT\>)
16. Set the Patreon URL to promote subscribing when users are unable to execute commands. (Ex: PATREON_URL=https://www.patreon.com/\<INSERT-PATREON-PAGE-NAME\>)
17. Set the Discord IDs of the guild and role that will be used for Patreon integration. (Ex: PATREON_GUILD_ID=012345678910111213 and PATRON_ROLE_ID=012345678910111213)
18. Set the comma delimited list of Discord guild IDs that will bypass Patreon validation. (Ex: PATREON_IGNORE_GUILDS=012345678910111213,012345678910111213,012345678910111213)
19. Set your preferred timeout for user responses to GBot messages. (Ex: USER_RESPONSE_TIMEOUT_SECONDS=300 if you want the bot to stop listening for a user response after 5 minutes)
20. ~~Set your preferred Halo MOTD and Competition trigger times in the GBot/Shared/gbot.env file. (Ex: HALO_INFINITE_COMPETITION_DAY=5 if you want competitions to start/end on Saturdays)~~
21. Set your preferred music bot timeout in the GBot/Shared/gbot.env file. (Ex: MUSIC_TIMEOUT_SECONDS=300 if you want the music bot to leave after 5 minutes of inactivity)
22. Set your preferred cached music timeout for deletion in the GBot/Shared/gbot.env file. This timeout should be set to a higher length of time than the length of the longest videos being played in elevator mode to ensure downloaded sounds aren't deleted before they should be used. (Ex: MUSIC_CACHE_DELETION_TIMEOUT_MINUTES=180 if you want the music bot to delete cached song downloads after 3 hours of not being used, and to prevent songs over 3 hours long from being played.)
23. Set your preferred transaction request timeout for buy and sell requests to be cancelled. (Ex: GTRADE_TRANSACTION_REQUEST_TIMEOUT_MINUTES=5 if you want transaction requests to be cancelled after 5 minutes of not being accepted.)
24. Set your preferred market sale timeout for market sales to be taken down. (Ex: GTRADE_MARKET_SALE_TIMEOUT_HOURS=3 if you want market sales to be taken down after 3 hours of no completed transaction.)
25. Set your preferred minimum amount of time between random Storms minigames. (Ex: STORMS_MIN_TIME_BETWEEN_SECONDS=3600 if you want there to be at least 1 hour between each Storm.)
26. Set your preferred maximum amount of time between random Storms minigames. (Ex: STORMS_MAX_TIME_BETWEEN_SECONDS=14400 if you want there to be at most 4 hours between each Storm.)
27. Set your preferred amount of time for Storms-related messages to be deleted after. (Ex: STORMS_DELETE_MESSAGES_AFTER_SECONDS=60 if you want Storm-related messages to be deleted after 60 seconds.)
28. Set your preferred 'Who Dis?' timeout in the GBot/Shared/gbot.env file. (Ex: WHODIS_TIMEOUT_MINUTES=5 if you want Who Dis games to timeout after 5 minutes)
29. If you are a developer, set your development guild IDs in the GBot/Shared/gbot.env file. (Ex: SLASH_COMMAND_TEST_GUILDS=012345678910111213,012345678910111213,012345678910111213 if you want to register the slash commands only in specific guilds)
30. Verify all files have read/write/execute permissions.
31. From the GBot directory, run 'docker-compose -f docker-compose-prod.yml up -d' to start the bot!

 ## Unit Tests
 * To execute all unit tests (for all cog suites), use the "Python: Current File" run configuration to run tests.py.
 * To execute unit tests for a single cog suite (replace \<cog\> with the cog you would like to test):
   * use the "Python: Current File" run configuration to run \<cog\>_test.py.
   * or execute the following command from the "GBot" directory:
      * python -m unittest GBotDiscord/test/\<cog\>/\<cog\>_test.py
      * Note: To avoid import errors, please make sure to run the above command from the "GBot" directory.

## Quart API

#### <ins>Development</ins>
<details>
<summary>Click to expand /GBot/private/development endpoints.</summary>

  *   <details>
      <summary>GET (/doc)</summary>

      *  Description:
         * `Returns available options to be used in POST request.`
      *  Syntax:
         * `GET - http://localhost:5004/GBot/private/development/doc`
      *  Response:
         * `{"options":{"action":[{"name":"rebuildLatest"},{"name":"setProperty","property":"LOG_LEVEL","value":"DEBUG"}]},"postBodyTemplate":{"action":{"name":"setProperty","property":"LOG_LEVEL","value":"DEBUG"}}}`
      </details>

  *   <details>
      <summary>POST</summary>

      *  Description:
         * `Use development features.`
      *  Syntax:
         * `POST - http://localhost:5004/GBot/private/development`
      *  Body:
         * `{"action":{"name":"rebuildLatest"}}`
      *  Response:
         * `{"action": "rebuildLatest", "status": "success", "message": "<shows Git changes made>"}`
      </details>
</details>

#### <ins>Discord</ins>
<details>
<summary>Click to expand /GBot/private/discord endpoints.</summary>

  *   <details>
      <summary>GET (/doc)</summary>

      *  Description:
         * `Returns available options to be used in POST request.`
      *  Syntax:
         * `GET - http://localhost:5004/GBot/private/discord/doc`
      *  Response:
         * `{"options":{"action":[{"name":"leaveGuild","serverId":"012345678910111213"},{"name":"sendMessage","message":"Hello world!","channelId":"012345678910111213","optionalMessageIdForReply":"012345678910111213"}]},"postBodyTemplate":{"action":{"name":"sendMessage","message":"Hello world!","channelId":"012345678910111213","optionalMessageIdForReply":"012345678910111213"}}}`
      </details>

  *   <details>
      <summary>POST</summary>

      *  Description:
         * `Use Discord features.`
      *  Syntax:
         * `POST - http://localhost:5004/GBot/private/discord`
      *  Body:
         * `{"action":{"name":"sendMessage","message":"Hello world!","channelId":"012345678910111213","optionalMessageIdForReply":"012345678910111213"}}`
      *  Response:
         * `{"action": "sendMessage", "status": "success"}`
      </details>
</details>

#### <ins>~~Halo~~ (DISCONTINUED)</ins>
<details>
<summary>Click to expand /GBot/private/halo/competition endpoints.</summary>

  *   <details>
      <summary>GET (/doc)</summary>

      *  ~~Description:~~
         * ~~`Returns available options to be used in POST request.`~~
      *  ~~Syntax:~~
         * ~~`GET - http://localhost:5004/GBot/private/halo/competition/doc`~~
      *  ~~Response:~~
         * ~~`{"options":{"serverId":["012345678910111213","all"],"startCompetition":[true,false]},"postBodyTemplate":{"serverId":"012345678910111213","startCompetition":false}}`~~
      </details>

  *   <details>
      <summary>POST</summary>

      *  ~~Description:~~
         * ~~`Trigger Halo competition status update for individual or all servers.`~~
      *  ~~Syntax:~~
         * ~~`POST - http://localhost:5004/GBot/private/halo/competition`~~
      *  ~~Body:~~
         * ~~`{"serverId":"012345678910111213","startCompetition":false}`~~
      *  ~~Response:~~
         * ~~`{"action": "haloPlayerStatsGetRequests(012345678910111213, False)", "status": "success"}`~~
      </details>
</details>
<details>
<summary>Click to expand /GBot/private/halo/motd endpoints.</summary>

  *   <details>
      <summary>GET (/doc)</summary>

      *  ~~Description:~~
         * ~~`Returns available options to be used in POST request.`~~
      *  ~~Syntax:~~
         * ~~GET - http://localhost:5004/GBot/private/halo/motd/doc`~~
      *  ~~Response:~~
         * ~~`{"options":{"serverId":["012345678910111213","all"]},"postBodyTemplate":{"serverId":"012345678910111213"}}`~~
      </details>

  *   <details>
      <summary>POST</summary>

      *  ~~Description:~~
         * ~~`Trigger Halo MOTD update for individual or all servers.`~~
      *  ~~Syntax:~~
         * ~~`POST - http://localhost:5004/GBot/private/halo/motd`~~
      *  ~~Body:~~
         * ~~`{"serverId":"all"}`~~
      *  ~~Response:~~
         * ~~`{"action": "haloMotdGetRequest(all)", "status": "success"}`~~
      </details>
</details>

#### <ins>Storms</ins>
<details>
<summary>Click to expand /GBot/private/storms/start endpoints.</summary>

  *   <details>
      <summary>GET (/doc)</summary>

      *  Description:
         * `Returns available options to be used in POST request.`
      *  Syntax:
         * `GET - http://localhost:5004/GBot/private/storms/start/doc`
      *  Response:
         * `{"options":{"serverId":["012345678910111213","all"]},"postBodyTemplate":{"serverId":"012345678910111213"}}`
      </details>

  *   <details>
      <summary>POST</summary>

      *  Description:
         * `Trigger a new Storm for individual or all servers.`
      *  Syntax:
         * `POST - http://localhost:5004/GBot/private/storms/start`
      *  Body:
         * `{"serverId":"012345678910111213"}`
      *  Response:
         * `{"attemptsMap":{},"fiveMinuteWarning":false,"oneMinuteWarning":false,"stormState":0,"triggerTime":"08/03/22 01:22:24 PM","winningNumber":54}`
      </details>
</details>
<details>
<summary>Click to expand /GBot/private/storms/state endpoints.</summary>

  *   <details>
      <summary>GET (/doc)</summary>

      *  Description:
         * `Returns available options to be used in POST request.`
      *  Syntax:
         * `GET - http://localhost:5004/GBot/private/storms/state/doc`
      *  Response:
         * `{"options":{"serverId":["012345678910111213","all"]},"postBodyTemplate":{"serverId":"012345678910111213"}}`
      </details>

  *   <details>
      <summary>POST</summary>

      *  Description:
         * `Get an individual or all servers' Storm states.`
      *  Syntax:
         * `POST - http://localhost:5004/GBot/private/storms/state`
      *  Body:
         * `{"serverId":"all"}`
      *  Response:
         * `{"012345678910111213":{"attemptsMap":{},"fiveMinuteWarning":false,"oneMinuteWarning":false,"stormState":0,"triggerTime":"08/03/22 03:51:22 PM","winningNumber":13},"012345678910111214":{"attemptsMap":{},"fiveMinuteWarning":false,"oneMinuteWarning":false,"stormState":1,"triggerTime":"08/03/22 01:22:24 PM","winningNumber":54}}`
      </details>
</details>