# Personal Plugin Recommendations

This is a much more opinion-based guide than the others, since it's my own _personal_ recommendations, rather than a walkthrough for something. You're free to disagree and I welcome things like typo corrections and clarification requests, but please don't try to "correct" my opinions in this article.

## Custom Plugin Repositories

I use several "custom" plugin repositories, which is a feature that Dalamud recently (as of this writing) implemented. In addition to the base "official" repo, plugin authors can now publish their own repos with the same structure and provide the URL to it. In your in-game plugin browser, hit the _Settings_ button, go to the _Experimental_ tab, and you can paste those URLs in to tell Dalamud to read those repos and their plugins as well. Any of these "third party" or "unofficial" plugins will show up in the plugin browser list like the "official" ones do, and can be automatically updated by Dalamud the same way.

Plugins that require custom repositories will indicate the repository they require. Each is given a number, but that's only to identify them in this document - you can add them in any order, skip ones you don't want, add others first, whatever you want. Just right click the "custom repo \<whatever\>" link, copy the address, and paste it into the Dalamud settings window, in the _Experimental_ tab, then hit the `+` button to add it.

## Recommended Plugins

### Adventurer In Need

If you do a lot of duty roulettes, you'll love this one. It adds a chatlog message whenever a configured roulette switches to a selected role bonus. You can toggle each roulette individually so you only get alerts for the ones you want to play (nobody ever wants to do the MSQ roulettes, right?) _and_ only for the specific roles you want. More specifically, you toggle alerts overall for a roulette, and then select the roles you're interested _for_ that roulette, so you can pick different roles for different duty roulettes.

<details>
<summary>Advanced</summary>

You can also congifure _webhooks_ that this plugin will post messages to for the role/roulette alerts that you enable. In fact, you can even tell it not to do chatlog messages and _only_ do webhooks. The posted message is in the kind of format for a basic discord webhook and can't be changed, so while you can easily have your client post alerts about roulette bonuses to a discord channel if you want, any other (custom) receivers will need to be able to extract the roulette and role from a human-readable message in a string in a JSON object. You might be interested in the [webhook] utility for that if you need a translation layer.

</details>

### Burning Down The House

> :exclamation: **Requires [custom repo #1]**

BDTH is a tool that allows you to position furnishings (indoor _and_ outdoor, but be careful not to be obvious about it!) _anywhere_ as long as you can place it down. You can float things in midair, half-bury stuff in the ground, overlap items, whatever you like. This is the plugin version of it, rather than the external program version. Once installed, just use `/bdth` to open the interface. It's fairly self-explanatory, but if you want to use the coordinate controls, switch to _rotation_ mode in the furnishing editor and select the item.

### Chat Bubbles

This is a bit niche, but if you have trouble tracking who's talking or you just like the slight immersion of having player speech show up in bubbles over the speaker's head, this is for you. Once installed, you can configure it to choose which chat channels get bubbles, as well as the _text_ colour of the speech in those bubbles - no background colour control, so light text is basically unreadable - as well as how long the bubble stays. You can even make additional messages from the same person show up in the _same_ bubble, expanding it to fit, instead of adding another one.

### ChatCoordinates

This one is mostly useful if you end up with world coordinates _outside_ the game that you want to place a flag at _inside_ the game. For instance, if you use wikis or the like to locate specific things, you can take the coordinates and use the `/coord` command to place your map marker there without having to find the actual site on your map and control-click there yourself.

<details>
<summary>Usage</summary>

The `/coord` command is very lax. It tries _really_ well to extract coordinates from what you write, and can even take a partial map-zone name as well if you're not marking your current area. Basically, looks for the first number (which can include a decimal point) and treats that as the _x_ coordinate, then looks for the second (again, can have a decimal) and uses that as the _y_ coordinate, and then _if_ there's a colon (`:`) after that, everything _past_ the colon is a partial map-zone name to look for and put the flag in. So, for example, you can paste in `/coord x30, y=12.2:dhona` and get a map flag at `(30.0, 12.2)` in Mor Dhona. Or you could say `/coord 10.4 19.5` to put your marker at `(10.4, 19.5)` in whatever map zone you're currently in.

</details>

### FPS Plugin

Nice and simple, this just shows you what your immediate and average FPS is. It can even show your minimum FPS within the same tracking period for your average, if you want. You can style it (font size, background opacity, text colour...) and place it wherever you want on your screen. You can even use chat commands (`/pfps` with either `show`, `hide`, or `toggle`) to control its visibility, so you can macro them and assign them to a hotbar with a key control.

### Gatherbuddy

A gatherer's best friend indeed, this one will let you search timed MIN/BTN nodes (including filtering to one or the other _and_ by expansion pack!), find out what bait, location, time, weather, and skill you want for fish, set in-game alarms (managed by the plugin) for timed nodes going up, and even provide a weather forecast for the next half-dozen weather changes in the game - for _every_ zone.

On top of that, the `/gather` command takes a partial item name, finds the best match, and tells you about it - along with, optionally, applying the relevant gearset, starting a teleport to the nearest aetheryte, and opening your map, complete with a pinned location. There's also `/gathermin` and `/gatherbtn` for items that can be gathered by either, to force only looking at one type of node.

And finally, if you've got GP to burn, there's `/gathergroup` for things like "find whatever node is currently up that'll give me white scrips", including again the ability to limit it to only MIN or BTN nodes.

### Glamaholic

No, sorry, you can't save more than fifteen glamour plates in the game. That's on SE, plugins can't help. What plugins _can_ do, and what this particular plugin _does_, is save your glamour plates (and let you create them more easily) so that you can effectively backup, create, edit, and then restore/load plates into the _actual_ glamour plate set.

This plugin lets you create a glamour plate with a much nicer editor, including even a feature to look for gear that shares the same model (in case you have something you want but that's hard to get). You can name and even tag your plugin-saved plates to search through them later, because there's _no_ limit - and you can even create a plate directly from an examine window, to copy someone's look, if you want.

You can instantly try on the entire plate at once in the fitting room, just like the [_Item Search_](#item-search) plugin used to do, but you can also "apply" the plate when you have the in-game plate editor open, which will replace it with the items from the plugin's list. Finally, you can _share_ plates too, by copying a chunk of JSON describing the items in it, which someone else can then import to make a Glamaholic plate that's a copy of yours.

### Globetrotter

A treasure hunter's _best_ friend - when you decipher a map or use the `/tmap` command with one in your inventory, Globetrotter will open your game map and place a flag where the treasure is located. Just like that. No more searching and squinting, no more wondering if the map matches that site or you're just seeing things, no more trying to recognise tiny fragments of maps... Globetrotter will tell you _exactly_ where to go.

### Good Memory

Have you ever been in an instance and an orchestrion roll comes up in the loot and you just _can't remember_ if you've already gotten that one? _Good Memory_ adds a line to the tooltip on things like orchestrion rolls and minions telling you whether you've already acquired it or not. No configuration, no checklists, no keeping notes, no gambling and hoping you're right - just look at the tooltip and it'll tell you straight. ~~And SE said they couldn't implement it...~~

### Item Search

A catalog of _every item in the game_ - searchable, filterable, and with options like linking it in your local chatlog (as an `/echo` type message - you can right-click -> `Link` for sending messages or hit `Try on` for gear!) or looking it up on garland tools or teamcraft. If you also have the [_Market Board_](#market-board) plugin (see below) you can look up the item directly from the catalog!

If you're looking for the previous feature of saving outfit sets in the fitting room, don't worry. The fitting room itself is still here, but the outfits have been removed in favour of the more extensive [_Glamaholic_](#glamaholic) plugin.

<details>
<summary>Filters</summary>

In addition to searching (technically filtering by item name text) you can also filter items by:
- Category (the sort of things you can search in on marketboards, only more detailed and you can pick multiple)
- Equip level (player level needed to equip item, for gear)
- Item level
- Rarity
- Job/sex/race restrictions for gear
- What job can craft it (or if it's not craftable)
- What job can desynth it (or if it's not desynthable)
- What currency it can be bought with, or it it's not buyable
- Whether it's dyable or not
- Whether it's "unique" or not
- Whether it's tradeable or not
- What stats it affects

</details>

### Macro Chain

Macro Chain adds two commands: `/runmacro <macro#> {individual|shared}` and `/nextmacro`. The `/runmacro` command lets you start running a specific macro from the start, but it is NOT usable from WITHIN a macro. If you're wondering what the point of it is then, you might want to look at [_QoLBar_](#qolbar) and [_Simple Tweaks_](#simple-tweaks).

The `/nextmacro` command _only_ works from within a macro, and it immediately jumps to the first line of the _next_ macro. For example, if your macro #1 ends with `/nextmacro`, then executing that macro will also execute macro #2. This lets you make macros longer than 15 lines, technically speaking. For an alternative that's more powerful but also more complex, check out [_Macrology_](#macrology).

### Macrology

> :exclamation: **Requires [custom repo #4]**

This is basically an entire macro implementation, external to the game's macro system. Technically, this means that you can't use macro-only commands in Macrology macros, but it also means you _can_ use macro-forbidden commands in them. The major benefits are that Macrology macros have no length limit and run in parallel, so you can have more than one going at a time. On top of that, you can make a macro loop infinitely, although there's still no flow control, so you can't make it loop _conditionally_. You'll need to have a way to use the plugin's cancel-macro command (and the builtin `/macrocancel` won't work, since these are totally separate from the game's macros).

One other nice improvement is that Macrology allows fractional waits, which XIV macros don't support. You can manage the timing of your commands with some decent precision, and combining that with the lack of length limit means that you can make a whole procession out of a single macro!

### Market Board

Mentioned briefly in the [_Item Search_](#item-search) plugin above, this plugin provides an on-demand window to search the player markets. You can search by name and filter by all of the standard market categories, but you can't access your favourites or wish list - because it's not looking up the game markets directly from your character. The thing is, it _can't_ do that - there's no way to access that except through an in-game marketboard activator.

There's a service called _Universalis_ that tracks marketboard prices for items, across every single game world. It tracks what's currently available and sales that were made, and XIVLauncher (and Teamcraft, if you use that) both send (anonymous) updates whenever you look something up on the markets. You don't have to do anything to make it happen, just look at an item listing on the marketboards while using XIVLauncher with the in-game addon (Dalamud) enabled, or with Teamcraft running and packet capture enabled.

Unfortunately, since not everyone uses these tools, sometimes the data ends up out of date. If you want to force it to update for a specific item, you can go look at its prices yourself to send that data to Universalis. Try to convince your friends to use XIVLauncher if you can; the more people who do, the better the data will be!

### MOAction

Macro-style targeting of actions, without the macros - or the downsides they involve. If you've never heard of macro-targeting, it's when you make a macro to execute an action via the `/action` command, using various placeholders to create a priority list of targets. This would let you have a single button that attempts to use an action on your current target, and if that fails then use it on your target's target, for example. The problem is that macros don't queue like actions do, so you lose time on them.

MOAction lets you define a series of things to try when you use a specific action. The most basic use is to just try a handful of different targets on that same action, but you _can_ define an entry in that list to use a totally different action, if you want. MOAction will go down the list when you use the "initial" action and find the first entry that's valid, then use that.

Included in the targets list are both UI mouseover _and_ field mouseover, which means that as a healer, you can make your heal spells automatically target the player you're mousing over, and if there isn't one, then fall back to your target.

### No Kill

Very simple and absolutely an install-and-forget plugin. When you launch the game and try to connect to your data centre, the game terminates if that connection fails for any reason. That can be pretty annoying if the issue was only a temporary hiccup in your connection, so this plugin just stops it from doing that. If the game fails to connect to the server, it'll just stay open so you can retry, instead of making you launch it again - which is especially annoying with one-time passwords.

### No Tank You

A simple and hard-to-miss visual display of who's screwing up their job. NTY will show a warning if you or your party (configurable) is missing an important skill, like Sage's Kardion, Dancer's Dance Partner, or any tank's tank stance. Good for learning or helping others learn. You can even make it show warnings for the Well Fed buff to remind you to eat, although those only apply in areas that are specifically listed by the user.

### No Soliciting

An absolute _essential_, this plugin blocks RMT, FC ads, RP ads, phishing, and all sorts of related crap from both chat _and_ the party finder window. You can choose what categories of stuff to block and define your own filters too (for text matches and regex patterns both) in order to remove even _system_ messages. No FF, I _don't_ want you telling me every time I enter or leave a damn sanctuary.

Once installed, just run `/nosol` to open the configuration. It should be fairly self-explanatory.

### Orchestrion

Especially with Endwalker, sometimes you really want to know what music is being played. Orchestrion will not only show the current track title in your server info bar, it'll let you force a specific track to be played, show you a list of recently played tracks, and allow you to replace tracks with others.

### Ping Plugin

Much like the FPS plugin, this one's really simple. You can style the window, but all it does is what it sounds like: it reports your ping to the server. Convenient for estimaging how much lag you should expect to be having.

### Pixel Perfect

You probably know, if you've played for any real length of time, that the orange glowy areas around enemies are them charging up an attack, and that if you're in that area when they finish then you'll be hit. The animation doesn't matter, if they finished "casting" while you were in there, you're getting hit. What you may or may not know is that your "hitbox" for being inside that area is basically a single point. This plugin shows where that point is as a tiny overlay on your screen - if that point is even the _tiniest_ bit outside the attack area, you're safe.

Furthermore, it can also render a ring around your character at a configurable radius, which may be useful to tell when an enemy is inside the range of one of your primary attacks. Both the hitbox point and the ring are toggleable and colourable, and you can even force them to only appear in combat or in instances if you don't want them around normally.

### PrefPro

Not actually a commonly-needed one but very cool, and potentially also very comfortable. PrefPro lets you change your character name _only_ for the purposes of NPCs and dialogue - setting your first and last names - as well as choosing what combination to use when addressing you, and even what _gender_ to address you as.

<details>
<summary>Specifics</summary>

You set the first and last names for your characters (only for NPC speech) and then you have three situations you choose the form of address for. When NPCs or dialogue use your _full_ name, your _first_ name only, or your _last_ name only, you can force it to be replaced with first-then-last, first-only, last-only, or last-then-first. All independently.

Some cultures place the family name first and the individual name last, but the game doesn't have any option to indicate that your name follows that convention. PrefPro lets you force NPCs and dialogue to do that anyway, as well as to use a different name entirely for those replacements.

Finally, you can have gendered dialogue follow your character model's sex (playing a male gets male gendering, playing a female gets female gendering) or force it to use one or the other regardless. Unfortunately, due to the nature of language and the voice lines, it's outright not possible to get gender-neutral pronouns.

</details>

### PriceCheck

It might sound like you could just use the [_Market Board_](#market-board) plugin, but this one is a little different - and for things like quest rewards, more convenient. You can configure a minimum price threshold, a maximum history period, and a hotkey to trigger the lookup. When you hold that hotkey and hover over an item for a certain (also configurable) amount of time, the plugin looks up that item on Universalis and reports the average price - or, if the price is too low, tells you that you should just sell it to an NPC instead. You can choose whether it should tell you this in chat, in a popup window, or both.

### QoLBar

If you're like me, you never have enough hotbar space for all the things you'd like to put there. Especially if you also like to use custom macros to make slash commands accessible via easy buttons. This plugin will be your saving grace: it lets you define and add new hotbars, positioned anywhere you want, with buttons to run slash commands - and you can even make categories for submenus. Oh, and assign hotkeys too.

### Quest Map

If you've ever had to tab out of the game to look up questlines, or what quest you need to do to unlock some instance, or just where the quest starts, this plugin does all of that and more. You can search for quests by their name or rewards, including the duty/duties they unlock, and get an interactive map of the questlines involved - what's required for the one you want, and what it unlocks. Each of those quests can be clicked on in the map to see information about it, including a button to mark it on the map (which fails for instanced areas like the Waking Sands, unfortunately) and open it in your journal (if it's present, which means accepted or completed).

### Simple Tweaks

The title here is a _blatant_ lie, but it's a collection of minor-enough-to-not-need-their-own-plugin tweaks, so... close enough, I suppose? Featuring such QoL improvements as clickable chat links, disabling the title screen's idle movie, and a _wide_ assortment of UI and item-tooltip improvements, not to mention _custom chatbox command aliases_ (pretty convenient with MacroRecursion...!) this plugin does too much to describe, but I promise you'll find some useful things. Possibly my number one favourite, honestly!

### SoundSetter

A hotkeyable window (and plugin commands) to let you adjust different volume categories (including master volume) without needing the system config window. Not only can you now macro (and therefore hotkey!) volume controls, you can also hotkey the window itself from the plugin directly, which lets you control _all_ aspects of game volume... even in cutscenes, where you can't open the system config window.

### Teleporter

Personally, I find the ability to teleport via command more convenient than the menu, but this plugin doesn't stop there. You can show an "aethergate" window, which lets you add buttons for commonly-used teleports, and you can set a teleport cost threshold above which aetheryte tickets will _automatically_ be used, if you have any. It can skip the ticket popup on normal teleports. It can even take a _map zone name_ and teleport you to an aetheryte in that zone! And much like [ChatCoordinates](#chatcoordinates), it accepts partial names as well. `/tp idyl` and Idyllshire, here we come! Or is it Idylshire..? (It's the first, I checked while writing this.)

### Visibility

Two plugins in one, sort of. The old VoidList plugin (a better blacklist than the game provides) was rolled into Visibility a while back. That one lets you completely remove a player from your game, essentially - they won't even render on your screen. No chat, no emote messages, you won't even see them.

Visibility extends this to allow you to hide rendering of _all_ players, chocobos, pets, and/or minions, by default. You can override that to show party members, friends, FC members, and dead players while still hiding the rest, too. Ever gone to an area (*cough*Limsa*cough*) and found your smooth-as-butter framerate suddenly became a slideshow presentation? This can't completely eliminate _all_ lag from highly congested areas, but it can help with overstrained GPUs and also situations where you can't see the damn activator through the mass of people in the way.

Also, you can toggle the default show/hide functionality by command, so you can macro and hotkey the ability to hide players, which is nice when you only want it in certain areas (***cough*Limsa*cough***) but not others. Hiding players by default _won't_ hide their chat or emotes like VoidList-ing someone will, by the way.

### Waymark Preset Plugin

This one's for the raiders, really. You can configure it to save and load waymark presets from/to the _game's_ preset library to/from the _plugin's_, automatically, when leaving/entering instanced areas. For example, when I enter the Vault (HSW dungeon) my vanilla waymark presets are written by this plugin so that I have one for each section, marking enemy encounter areas and treasure chests. Then I can just use the normal, builtin function to apply those waymarks. If I went to another instance, I'd be able to have it automatically load presets for _those_ areas into my vanilla waymark preset list.

If you do a lot of instances (dungeons, trials, raids, etc) that you use waymarks in (or would like to but don't want to deal with placing them every time) then you might want to install this, look at the config (which has helpful tooltips) and maybe play around with it a little.

### XIVCombo (Expanded)

> :exclamation: **Requires [custom repo #4]** _(for the expanded version)_

> :exclamation: **Requires [custom repo #8]** _(for the very expanded version)_

You probably know about _skill chains_ in XIV - certain skills get _combos_ when used after others, which make them do more damage or add an extra effect. Generally, you want to follow the chain. For example, if you play Machinist, you want to use (heated) split shot, then follow it with (heated) slug shot, then finish the chain with (heated) clean shot. If you use plain Slug Shot _without_ first using (heated) split shot, you do 100 potency of damage. If you follow the chain, you do _260_ potency of damage instead, just with that skill - nevermind what (heated) split shot does first.

The issue with this is that you need another hotbar button (and probably keyboard button) for each of those three skills. That can fill your hotbars up pretty fast, and can be annoying or even difficult to hit the keybinds while still moving. Enter XIVCombo.

XIVCombo _condenses_ those skill by having you only place the _end_ skill of the chain on your hotbar, and dynamically replacing it on the fly. Continuing the above example, you would place (heated) clean shot on your hotbar, and the plugin would remember that while replacing it with (heated) split shot. When you use that one - the first attack in the chain - and the second attack is ready to combo, the button is replaced with the next one. Again so for the third one. Suddenly your three-move combo chain is all on a single button!

There are a fair number of these button-replacement chains that XIVCombo offers, and various forks may include even more. All of them are toggleable - you choose only the ones that you actually want, that fit your playstyle - and start out disabled by default, so as not to mess anything up. Install the mod and then look at the config; it's organised by job and each section has checkboxes to control the chain replacements and a little line by each with details.

> :bangbang: **There's an official version of this plugin**, and then _several_ different _unofficial_ versions, ranging from the "unofficially official" fork (_XIVCombo Expanded_) to through things that are probably about two steps removed from a bot, and only because they can't move and target things for you. If you feel like it, you can poke around on github and look for various repos and forks, which may also net you some other plugins. Just be careful, because you're literally running foreign code on your own computer and the author can make it do just about anything they want.

### YesAlready

> :exclamation: **Requires [custom repo #4]**

If you've gotten sick of having to tell the game that yes, you really did mean to click that, you're sure, you just want to do the thing, will it shut up and do what you told it to already, then this plugin might just save your sanity. Not only can you select categories of confirmation boxes to auto-confirm, you can even use plain-text _and_ regex matching for all of the popups. The plugin even recognises when there's a confirmation checkbox to be ticked as well as hitting the button, and takes care of that for you too! Finally, you can extract materia from things without the game bugging you for _every single item_ to be _extra_ sure.

Recently, support was even added for lists - you know, where you get presented with two or more options and click one of the lines? A surprising number of those are basically just yes-or-no boxes except with flavour text instead of simple "yes" and "no" options. Those are fully supported (so you can skip straight through the "do you want to retire to an inn room?" prompts) as well as longer lists.

There's even now support for skipping _dialogue_ based on the NPC in question, although you'll want to be careful with that one. But if you set it up right, it'll now take only one click to get into your inn room in any zone you want!



[webhook]: <https://github.com/adnanh/webhook/> "Define custom webhooks to invoke other programs, passing data directly through - available for windows and linux, can be compiled from source"
[custom repo #1]: <https://raw.githubusercontent.com/LeonBlade/DalamudPlugins/main/repo.json>
[custom repo #2]: <https://plugins.annaclemens.io/>
[custom repo #3]: <https://plugins.annaclemens.io/unofficial>
[custom repo #4]: <https://github.com/daemitus/MyDalamudPlugins/raw/master/pluginmaster.json>
[custom repo #5]: <https://raw.githubusercontent.com/Bluefissure/DalamudPlugins/Bluefissure/pluginmaster.json>
[custom repo #6]: <https://raw.githubusercontent.com/SaltyCog/DalamudPlugins/main/repo.json>
[custom repo #7]: <https://raw.githubusercontent.com/maributt/xivplugins/main/repo.json>
[custom repo #8]: <https://raw.githubusercontent.com/PrincessRTFM/MyDalamudPlugins/master/pluginmaster.json>
[custom repo #9]: <https://raw.githubusercontent.com/xivdev/Penumbra/master/repo.json>
[custom repo #10]: <https://repo.waitingway.com/>
