---
layout: default
title: GTrade Commands
description:
---

[back](./commands)

### /buy
>#### Description
>    * `Buy another user's item for sale in the discord server. Create a request to buy from a user, complete a user's pending sell request, or buy an item for sale in the server's market.`
>
>#### Syntax
>    * `.[buy|by] <user> <item>`
>
>#### Example
>
>    ```:
>    .by @MasterChief "gravity hammer"
>    .buy @MasterChief shield
>    ```

### /craft
>#### Description
>    * `Craft items to show off and trade. Surround name with double quotes if multiple words.`
>
>#### Syntax
>    * `.[craft|cr] <name> <value> <type>`
>    * `type options are: image`
>
>#### Example
>
>    ```
>    .cr "gravity hammer" 6.75 image
>    .craft shield 6.75 image
>    ```

### /destroy
>#### Description
>    * `Destroy an item in your inventory.`
>
>#### Syntax
>    * `.[destroy|d] <item>`
>
>#### Example
>
>    ```
>    .d "gravity hammer"
>    .destroy shield
>    ```

### /item
>#### Description
>    * `Show off an item in your inventory.`
>
>#### Syntax
>    * `.[item|i] <item>`
>
>#### Example
>
>    ```
>    .i "gravity hammer"
>    .item shield
>    ```

### /items
>#### Description
>    * `List all items in your inventory, or another user's inventory in this server.`
>
>#### Syntax
>    * `.[items|is] [user]`
>
>#### Example
>
>    ```
>    .is @MasterChief
>    ```

### /market
>#### Description
>    * `Show all market items for sale and personal trade requests in the discord server.`
>
>#### Syntax
>    * `.[market|m]`
>
>#### Example
>
>    ```
>    .m
>    ```

### /rename
>#### Description
>    * `Rename an item in your inventory.`
>
>#### Syntax
>    * `.[rename|rn] <item> <name>`
>
>#### Example
>
>    ```
>    .rn "gravity hammer" gravityHammer
>    .rename shield "my shield"
>    ```

### /sell
>#### Description
>    * `Sell an item to another user in this discord server. Create a request to sell to a user, complete a user's pending buy request, or place an item for sale in the server's market.`
>
>#### Syntax
>    * `.[sell|sl] <item> [user]`
>
>#### Example
>
>    ```
>    .sl gravityHammer @MasterChief
>    .sell "my shield"
>    ```

[back](./commands)
