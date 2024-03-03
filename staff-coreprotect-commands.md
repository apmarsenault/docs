# CoreProtect Commands

---

You can access the following commands by using `/co`.

---

## Command Overview

|Command|Description|
|---|---|
|[/co help](https://docs.coreprotect.net/commands/#co-help)|Display a list of commands|
|[/co inspect](https://docs.coreprotect.net/commands/#co-inspect)|Toggle the inspector|
|[/co lookup](https://docs.coreprotect.net/commands/#co-lookup)|Lookup block data|
|[/co rollback](https://docs.coreprotect.net/commands/#co-rollback)|Rollback block data|
|[/co restore](https://docs.coreprotect.net/commands/#co-restore)|Restore block data|
|[/co purge](https://docs.coreprotect.net/commands/#co-purge)|Delete old block data|
|[/co reload](https://docs.coreprotect.net/commands/#co-reload)|Reload the configuration file|
|[/co status](https://docs.coreprotect.net/commands/#co-status)|View the plugin status|
|[/co consumer](https://docs.coreprotect.net/commands/#co-consumer)|Toggle consumer processing|

### Alias Commands

|Command|Description|
|---|---|
|/co near|Performs a lookup with a radius of 5|
|/co undo|Revert a rollback/restore via the opposite action|

---

## Command Details

_Detailed command information is listed below._

### /co help

Display a list of commands in-game.

---

### /co inspect

Enable the inspector. Type the command again to disable it. You can also use just "/co i".

---

### /co lookup

Perform a lookup. Nearly all of the parameters are optional.

|Command|Parameters|
|---|---|
|/co lookup|`u:<user> t:<time> r:<radius> a:<action> i:<include> e:<exclude>`|
|/co l|_`/co lookup <params>`_|

#### Parameters

|Parameter|Description|
|---|---|
|[`u:<user>`](https://docs.coreprotect.net/commands/#uuser)|Specify the user(s) to lookup.|
|[`t:<time>`](https://docs.coreprotect.net/commands/#ttime)|Specify the amount of time to lookup.|
|[`r:<radius>`](https://docs.coreprotect.net/commands/#rradius)|Specify a radius area to limit the lookup to.|
|[`a:<action>`](https://docs.coreprotect.net/commands/#aaction)|Restrict the lookup to a certain action.|
|[`i:<include>`](https://docs.coreprotect.net/commands/#iinclude)|Include specific blocks/entities in the lookup.|
|[`e:<exclude>`](https://docs.coreprotect.net/commands/#eexclude)|Exclude blocks/entities from the lookup.|
|[`#<hashtag>`](https://docs.coreprotect.net/commands/#hashtag)|Add a hashtag to perform additional actions.|

#### Pagination

If multiple pages are returned, use the command `/co lookup <page>` to switch pages.  
To change the number of lines displayed on a page, use `/co lookup <page>:<lines>`.

> _For example, `/co l 1:10` will return 10 lines of data, starting at the first page._

---

### /co rollback

Perform a rollback. Uses the same [parameters](https://docs.coreprotect.net/commands/#parameters) as /co lookup.  
_Rollbacks can be used to revert player actions._

|Command|Parameters|
|---|---|
|/co rollback|`u:<user> t:<time> r:<radius> a:<action> i:<include> e:<exclude>`|
|/co rb|_`/co rollback <params>`_|

---

### /co restore

Perform a restore. Uses the same [parameters](https://docs.coreprotect.net/commands/#parameters) as /co lookup.  
_Restoring can be used to undo rollbacks or to restore player actions._

|Command|Parameters|
|---|---|
|/co restore|`u:<user> t:<time> r:<radius> a:<action> i:<include> e:<exclude>`|
|/co rs|_`/co restore <params>`_|

---

### /co purge

Purge old block data. Useful for freeing up space on your HDD if you don't need the older data.

|Command|Parameters|
|---|---|
|/co purge|`t:<time> r:<world>`|

For example, `/co purge t:30d` will delete all data older than one month, and only keep the last 30 days of data.

> If used in-game, only data older than 30 days can be purged.  
> If used from the console, only data older than 24 hours can be purged.

**Purging Worlds**  
You can also optionally specify a world in CoreProtect v19+.  
For example, `/co purge t:30d r:#world_nether` will delete all data older than one month in the Nether, without deleting data in any other worlds.

**MySQL Optimization**  
In CoreProtect v2.15+, adding "#optimize" to the end of the command (e.g. `/co purge t:30d #optimize`) will also optimize your tables and reclaim disk space. This option is only available when using MySQL, as SQLite purges do this by default.

_Please note adding the #optimize option will significantly slow down your purge, and is generally unnecessary._

---

### /co reload

Reloads the configuration file.

---

### /co status

Displays the plugin status and version information.

---

### /co consumer

Console command to pause or resume consumer queue processing.

---

## Parameter Details

### `u:<user>`

_You can specify a single user or multiple users._

- Example: `u:Notch`
- Example: `u:Notch,Intelli`
- Example: `u:#fire,#tnt,#creeper,#explosion`

---

### `t:<time>`

_You can specify weeks, days, hours, minutes, and seconds._  
_Time amounts can be combined, and decimals may be used._

- Example: `t:2w,5d,7h,2m,10s`
- Example: `t:5d2h`
- Example: `t:1h-2h` _(between one to two hours)_
- Example: `t:2.50h` _(two and a half hours)_

---

### `r:<radius>`

_A numeric radius targets within that many blocks of your player location._

- Example: `r:10` _(target within 10 blocks of your location)_
- Example: `r:#world_the_end` _(target a specific world)_
- Example: `r:#global` _(target the entire server)_
- Example: `r:#worldedit` or `r:#we` _(target a WorldEdit selection)_

---

### `a:<action>`

_Restrict the command to a specific action_

- Example: `a:+block` _(only include placed blocks)_

#### Actions

|Action|Description|
|---|---|
|`a:block`|blocks placed/broken|
|`a:+block`|blocks placed|
|`a:-block`|blocks broken|
|`a:chat`|messages sent in chat|
|`a:click`|player interactions|
|`a:command`|commands used|
|`a:container`|items taken from or put in chests|
|`a:+container`|items put in chests|
|`a:-container`|items taken from chests|
|`a:inventory`|items added or removed from player inventories|
|`a:+inventory`|items added to player inventories|
|`a:-inventory`|items removed from player inventories|
|`a:item`|items dropped, thrown, picked up, deposited, or withdrawn by players|
|`a:+item`|items picked up or withdrawn by players|
|`a:-item`|items dropped, thrown, or deposited by players|
|`a:kill`|mobs/animals killed|
|`a:session`|player logins/logouts|
|`a:+session`|player logins|
|`a:-session`|player logouts|
|`a:sign`|messages written on signs|
|`a:username`|username changes|

---

### `i:<include>`

_Can be used to specify a block/item/entity._

- Example: `i:stone` _(only include stone)_
- Example: `i:stone,oak_wood,bedrock` _(specify multiple blocks)_

> You can find a list of block names at [https://coreprotect.net/wiki-blocks](https://coreprotect.net/wiki-blocks).  
> You can find a list of entity names at [https://coreprotect.net/wiki-entities](https://coreprotect.net/wiki-entities).

---

### `e:<exclude>`

_Can be used to exclude a block/item/entity/user._

- Example: `e:tnt` _(exclude TNT)_

---

### `#<hashtag>`

Add a hashtag to the end of your command to perform additional actions.

- Example: `#preview` _(perform a rollback preview)_

#### Hashtags

|Hashtag|Effect|
|---|---|
|`#preview`|Preview a rollback/restore|
|`#count`|Return the number of rows found in a lookup query|
|`#verbose`|Display additional information during a rollback/restore|
|`#silent`|Display minimal information during a rollback/restore|

---

## Example Commands

### Example Rollback Commands

By default, if no radius is specified, a radius of 10 will be applied, restricting the rollback to within 10 blocks of you. Use `r:#global` to do a global rollback.

- `/co rollback Notch t:1h`  
    _(rollback Notch 1 hour (with default radius of 10))_
- `/co rollback u:Notch,Intelli t:1h #preview`  
    _(PREVIEW rolling back both Notch & Intelli 1 hour (with default radius of 10))_
- `/co rollback u:Notch t:23h17m`  
    _(rollback Notch 23 hours and 17 minutes (with default radius of 10))_
- `/co rollback u:Notch t:1h i:stone`  
    _(rollback ONLY stone placed/broken by Notch within the last hour (with default radius of 10))_
- `/co rollback u:Notch t:1h i:stone a:-block`  
    _(rollback ONLY stone BROKEN by Notch within the last hour (with default radius of 10))_
- `/co rollback u:Notch t:1h r:#global e:stone,dirt`  
    _(rollback EVERYTHING Notch did in the last hour EXCEPT for stone and dirt placed/broken)_
- `/co rollback u:Notch t:1h r:20`  
    _(rollback griefing Notch did in the last hour that is within 20 blocks of you)_
- `/co rollback u:Notch t:1h r:#nether`  
    _(rollback griefing Notch did in the last hour ONLY in the Nether)_
- `/co rollback u:Notch t:5m a:inventory`  
    _(rollback inventory transactions by Notch in the last 5 minutes)_
- `/co rollback t:15m r:30`  
    _(rollback everything done in the last 15 minutes by anyone within 30 blocks of you)_
- `/co rollback t:15m r:#worldedit`  
    _(rollback everything done in the last 15 minutes in a WorldEdit selection)_

---

### Example Lookup Commands

Lookup commands are generally the same as rollback commands. The primary difference is that a default radius is not applied to lookups, meaning all lookup commands do a global search by default.

- `/co lookup i:diamond_ore t:1h a:-block`  
    _(lookup all diamond ore mined in the last hour)_
- `/co lookup u:Notch t:30m a:chat`  
    _(lookup chat messages sent by Notch in the last 30 minutes)_
- `/co lookup u:Notch t:3d a:inventory`  
    _(lookup inventory transactions by Notch in the last 3 days)_
- `/co lookup u:Notch a:login`  
    _(lookup all logins ever done by Notch)_
- `/co lookup u:Notch a:login`  
    _(lookup all logins ever done by Notch)_
- `/co lookup u:Notch a:username`  
    _(lookup previous usernames used by Notch)_s