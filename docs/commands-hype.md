---
layout: default
title: Hype Commands
description:
---

[back](./commands)

### /hype
>#### Description
>    * `Set a regular expression to match against new messages in this server, and a list of possible responses to reply to it with. Surround regex and response each with double quotes if multiple words. (admin only)`
>
>#### Syntax
>    * `.[hype|hy] [regex] [reply]`
>
>#### Example
>
>    ```
>    .hy "Hello there!" "General Kenobi!" "You fool! I've been trained in your Jedi arts by Count Dooku."
>    .hype "It's over Anakin, I have the high ground." "You underestimate my power!"
>    ```

### /react
>#### Description
>    * `Set a regular expression to match against new messages in this server, and a list of possible emojis to react to it with. Surround regex with double quotes if multiple words. (admin only)`
>
>#### Syntax
>    * `.[react|re] [regex] [emoji]`
>
>#### Example
>
>    ```
>    .re "How are you feeling?" 😊🙁
>    .react "Vrrm vrrm" 🚗
>    ```

### /unmatch
>#### Description
>    * `Remove an existing regular expression match response in this server. (admin only)`
>
>#### Syntax
>    * `.[unmatch|um]`
>
>#### Example
>
>    ```
>    .unmatch
>    ```

[back](./commands)
