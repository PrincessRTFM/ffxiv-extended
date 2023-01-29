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

### Aether Compass

Despite the name, this plugin detects more than just aether currents, like finding hunt mobs (B/A/S-rank) and nodes on the Island Sanctuary. You can configure what exactly it looks for, and how you want it to inform you, with options including an on-screen pointer that shows you the direction of the detected thing, a vanilla-game "toast" notification like you'd get for entering a new part of the map, and even a chat message with a clickable link to place your flag there.

If you're doing aether currents or the Hunt, this plugin can be invaluable for finding the things you need.

### Auto Visor

> :exclamation: **Requires [custom repo #11]**

Purely for style, this plugin lets you define conditions (normal, mounted, flying, swimming, diving, using fashion accessory, in duty, in combat, weapon drawn...) for individual jobs, on individual characters, to automatically control your headgear visibility, weapon visibility, and even the "adjust visor" toggle. Maybe you want your headgear to be invisible until you're in combat or in a duty, and once you draw your weapons, you want it visible and _also_ the visor to be adjusted for whatever effect that gives. Maybe you want to only show your weapon when you're in a duty. Maybe you only want your headgear visible when mounted, and visor adjusted when flying.

You can set all these sorts of things _and more_, and you can do it per-job per-character for nigh-total control.

### BigPlayerDebuffs

This one's super simple, but can be a nice little bit of QoL: it scales up your own debuffs applied to your target in their status effect UI element. You can configure how much it scales by, but it's a convenient way to see at a single glance which debuffs are _yours_ (and may need to be refreshed soon) and which ones are from other players.

### Burning Down The House

> :exclamation: **Requires [custom repo #1]**

BDTH is a tool that allows you to position furnishings (indoor _and_ outdoor, but be careful not to be obvious about it!) _anywhere_ as long as you can place it down. You can float things in midair, half-bury stuff in the ground, overlap items, whatever you like. This is the plugin version of it, rather than the external program version. Once installed, just use `/bdth` to open the interface. It's fairly self-explanatory, but if you want to use the coordinate controls, switch to _rotation_ mode in the furnishing editor and select the item.

### Character Panel Refined

This cuts out useless cruft in the character panel window, and adds in some useful stats like critical/direct hit percentages, damage estimates, and DoH/DoL stats without consumables, to make comparing gear and checking base stats a lot easier.

### Chat Bubbles

This is a bit niche, but if you have trouble tracking who's talking or you just like the slight immersion of having player speech show up in bubbles over the speaker's head, this is for you. Once installed, you can configure it to choose which chat channels get bubbles, as well as the _text_ colour of the speech in those bubbles - no background colour control, so light text is basically unreadable - as well as how long the bubble stays. You can even make additional messages from the same person show up in the _same_ bubble, expanding it to fit, instead of adding another one.

### ChatAlerts

If you've ever missed important chat messages because you just didn't notice them, this might help. You can configure text to look for, optionally using regular expressions, and specify the channels to check against. You can even make it match against the message _sender_ instead of _content_, to always get pinged for specific people. And you can set up audio alerts to grab your attention, and even highlight the part of the message that matched - although that may not play well with others, since XIVChat seems to crash when that happens.

### ChatCoordinates

This one is mostly useful if you end up with world coordinates _outside_ the game that you want to place a flag at _inside_ the game. For instance, if you use wikis or the like to locate specific things, you can take the coordinates and use the `/coord` command to place your map marker there without having to find the actual site on your map and control-click there yourself.

<details>
<summary>Usage</summary>

The `/coord` command is very lax. It tries _really_ well to extract coordinates from what you write, and can even take a partial map-zone name as well if you're not marking your current area. Basically, looks for the first number (which can include a decimal point) and treats that as the _x_ coordinate, then looks for the second (again, can have a decimal) and uses that as the _y_ coordinate, and then _if_ there's a colon (`:`) after that, everything _past_ the colon is a partial map-zone name to look for and put the flag in. So, for example, you can paste in `/coord x30, y=12.2:dhona` and get a map flag at `(30.0, 12.2)` in Mor Dhona. Or you could say `/coord 10.4 19.5` to put your marker at `(10.4, 19.5)` in whatever map zone you're currently in.

</details>

### Chill Frames

Let's be real here, FFXIV can turn your computer into a space heater sometimes, _especially_ on higher graphics settings. And that can put some not-insignificant wear on your GPU. It's great that the game lets you limit the framerate when AFK or when the game's not in focus, but what the heck do you need 200 FPS for when you're just gathering? That's where this plugin comes in: you can set an "alternate" framerate limit, separate from the default one, and specify when exactly this alternate limit does _not_ apply.

If that sounds confusing, think of it like this: you can say that the _game's_ FPS limit is the "alternate" and this plugin's is the "main" and the plugin lets you specify when to use the _game's_ limit instead of the plugin. For example, you could set the game to not limit FPS, and have this plugin limit at 60, and then tell the plugin to only use that limit of 60 when _not_ in combat, in a duty, in a cutscene, or crafting, for example.

The end result is that when you can actually _use_ the extra framerate, you have it (automatically!) but when it's just a waste, you can save your GPU (and air conditioner) a little work.

### Coin Pouch

For reasons known only to Square Enix, basically all currencies other than gil have specific caps in this game. Which, unfortunately, means that if you don't remember to spend them when you get near that cap, you lose out on any more that you earn. For example, if you don't spend your Allagan Tomestones of Poetics, then doing duties and roulettes can't give you any more.

This plugin provides a warning in your chat when you cross a configured threshold of various currencies (for example, if you set it to 5000, then when you go from _below_ 5k to _at least_ 5k) to warn you that you're nearing the cap and need to spend them soon.

### Customize+

> :exclamation: **Requires [custom repo #16]**

The game itself only lets you customise your character's look so far. The scaling sliders are limited, and also only really available for height and bust (and maybe musculature?) which may make people used to more extensive systems a little disappointed. Well, this plugin's effects are entirely local (although check out _[Mare Synchronos]_ later!) but they expose scaling controls in all three dimensions for basically _every_ scalable bone in the character body.

Persistently. Per-character. Including NPCs.

### Daily Duty

There are a lot of timed things in this game. Limits that reset daily, events you can do weekly - the Hunt, both cactpots, roulettes, tribal quests, custom deliveries, the fashion report... the list goes on. It can be a lot to try and keep track of. Daily Duty simplifies it by letting you specify the ones you actually _care_ about and how you want it to help you: you can get reminders on login, on zone change (but only every five minutes, to avoid spam), in a little todo window... even a little window with timers, including progress bars to next reset and textual countdowns.

The module for Wondrous Tails will even send you alerts when you can mark off a sticker or are capped on Second Chance points, and the module for roulettes will highlight roulette names _in the duty finder_ in red for unfinished and green for completed for the day.

### Distance

Most people don't think about it much, but in this game, distances matter. All attacks have ranges, and most mobs (including bosses) have face-pull distances too, where once you cross them the mob attacks you. This plugin provides a number of ways to display the distance from you to something in the world - your target, focus target, arbitrary entities - and it does so by attaching a little bit of text to their nameplate, or the target/focus UI widget on your HUD.

And for bosses for which the face-pull range is known, it can even display _in-world_ an arc between you and the boss indicating the safe distance, so you can approach during pre-pulls without pulling early.

### Double Weaver

> :exclamation: **Requires [custom repo #5]**

Weaving refers to the practice using an ability, which is off-GCD, between the use of weaponskills or spells, which are on-GCD. _Double_ weaving is doing this twice per GCD, and is not only possible but almost essential for some high-end duties... but it's only possible with good ping. High latency causes "drifting", where your next GCD is delayed in order to perform the second ability weave. The point of this plugin is to gently nudge the game's internals in very particular ways in order to effectively _simulate_ having low ping specifically for double weaving.

### Easy Eyes

Some of the VFX in FFXIV can be overly bright, which is irritating at best, and an actual safety concern at worst, like for photosensitive players. If you've ever looked at particular VFX and wished you could just turn _that particular one_ off, then this plugin is for you. It lets you record a list of recent VFXs and then spawn them manually to check if they're an irritant, and you can add notes to VFXs that you disable since they're done by internal path. For example, Holy - the blinding-yet-standard White Mage spell - is `vfx/action/mg_holly/eff/mgc_holy1c0t.avfx`. You can even export and import lists of blocked VFXs and notes, for sharing with others.

### EnemyListDebuffs

If you play a job that's supposed to put DoT effects on enemies, it can be a pain in the ass to make sure you've got them on _all_ enemies, since you have to cycle through the entire list and check each one. This plugin just shows _your_ DoT effects next to the enemy's name in the enemy list, to see at a quick glance which ones have it and which ones don't. It even includes the time remaining!

### FPS Plugin

Nice and simple, this just shows you what your immediate and average FPS is. It can even show your minimum FPS within the same tracking period for your average, if you want. You can style it (font size, background opacity, text colour...) and place it wherever you want on your screen. You can even use chat commands (`/pfps` with either `show`, `hide`, or `toggle`) to control its visibility, so you can macro them and assign them to a hotbar with a key control.

### Gatherbuddy

A gatherer's best friend indeed, this one will let you search timed MIN/BTN nodes (including filtering to one or the other _and_ by expansion pack!), find out what bait, location, time, weather, and skill you want for fish, set in-game alarms (managed by the plugin) for timed nodes going up, and even provide a weather forecast for the next half-dozen weather changes in the game - for _every_ zone.

On top of that, the `/gather` command takes a partial item name, finds the best match, and tells you about it - along with, optionally, applying the relevant gearset, starting a teleport to the nearest aetheryte, and opening your map, complete with a pinned location. There's also `/gathermin` and `/gatherbtn` for items that can be gathered by either, to force only looking at one type of node.

And finally, if you've got GP to burn, there's `/gathergroup` for things like "find whatever node is currently up that'll give me white scrips", including again the ability to limit it to only MIN or BTN nodes.

### Gearset Helper

It's all about numbers, especially in the endgame, and this plugin is your best friend for dealing with those numbers. In the character window and examine window both, you can see effective stats (including gear, materia, and even food), the list of all materia melded to equipped gear (including how many slots are left), and the calculated _effects_ of the stats on the relevant mechanics like actual critical hit chance and damage.

### Glamaholic

No, sorry, you can't save more than twenty glamour plates in the game. That's on SE, plugins can't help. What plugins _can_ do, and what this particular plugin _does_, is save your glamour plates (and let you create them more easily) so that you can effectively backup, create, edit, and then restore/load plates into the _actual_ glamour plate set.

This plugin lets you create a glamour plate with a much nicer editor, including even a feature to look for gear that shares the same model (in case you have something you want but that's hard to get). You can name and even tag your plugin-saved plates to search through them later, because there's _no_ limit - and you can even create a plate directly from an examine window, to copy someone's look, if you want.

You can instantly try on the entire plate at once in the fitting room, just like the [_Item Search_](#item-search) plugin used to do, but you can also "apply" the plate when you have the in-game plate editor open, which will replace it with the items from the plugin's list. Finally, you can _share_ plates too, by copying a chunk of JSON describing the items in it, which someone else can then import to make a Glamaholic plate that's a copy of yours.

### Glamourer

> :exclamation: **Requires [custom repo #13]**

Similar-ish to Glamaholic, but filling a quite different niche, Glamourer lets you basically save character appearance - customisations (race, gender, hairstyle, colours, etc) and gear both - and apply them to yourself or your target later, at any time. You can even make _fixed_ designs, where characters with specific names, optionally on specific jobs, will always use a particular Glamourer design. And don't worry, you can configure designs to _only_ apply customisations or gear, rather than doing both.

On its own, this is entirely local, although that can make for excellent screenshot assistance. But check out _[Mare Synchronos]_ for a way to let other players see changes made to yourself!

### Globetrotter

A treasure hunter's _best_ friend - when you decipher a map or use the `/tmap` command with one in your inventory, Globetrotter will open your game map and place a flag where the treasure is located. Just like that. No more searching and squinting, no more wondering if the map matches that site or you're just seeing things, no more trying to recognise tiny fragments of maps... Globetrotter will tell you _exactly_ where to go.

### Good Friend

FFXIV natively sends you login/logout notifications for Free Company members, but not for your friends list in general. And no, it's not possible to make that happen - you would need to poll the server to get the status of _everyone_ on your friends list in order to do that, and that would be so detectable and possibly bannable. How this plugin does it is with an external API, which is sent a message when you log in or out, and then passes that on to the players in your friends list in order to notify them. This means that the plugin will only ever notify you of friends logging in and out _if they also use the plugin_, of course.

### Heels Plugin

> :exclamation: **Requires [custom repo #1]**

Especially once you get into modding, your character may not look _quite_ right when wearing high heels but not being any taller. In some cases, your feet may even clip into the ground. This plugin lets you specify how much your character's height should be offset for particular footwear items, to resolve these issues.

### Inventory Search Bar

Sometimes you know an item is in a particular inventory, but not _where_. Even the vanilla `/itemsearch` command only tells you which "box" of the inventory it's in. ISB gives you the ability to search within a _single_ inventory for an item name, highlighting all matching items to easily find the thing you _know_ is in there somewhere but can't find. It supports your own inventory, your saddlebags, your armoury, and your retainers.

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

### Mare Synchronos

> :exclamation: **Requires [custom repo #15]**

The plugin of every modder's dreams: pair with a friend (via plugin-specific means with a personal ID code) and then you and that friend will see each other's characters as you see yourselves. Mare only works with _[Penumbra]_ so you'll need that as well, but you should be using that for mods already anyway. It also features compatibility for _[Glamourer]_, _[Customise+]_, and the _[Heels Plugin]_ to share customisations made to your character through those plugins, but the core of it is that any Penumbra mods that apply to _your character_ will send the minimum necessary files to paired Mare users in order to recreate your _precise_ look for other people. No more sharing of whole entire mods, messing with collections and settings, and worrying about sharing private or paid mods - just register on Mare's discord, swap your pairing codes, and that's it. You're good to go.

### Market Board

Mentioned briefly in the [_Item Search_](#item-search) plugin above, this plugin provides an on-demand window to search the player markets. You can search by name and filter by all of the standard market categories, but you can't access your favourites or wish list - because it's not looking up the game markets directly from your character. The thing is, it _can't_ do that - there's no way to access that except through an in-game marketboard activator.

There's a service called _Universalis_ that tracks marketboard prices for items, across every single game world. It tracks what's currently available and sales that were made, and XIVLauncher (and Teamcraft, if you use that) both send (anonymous) updates whenever you look something up on the markets. You don't have to do anything to make it happen, just look at an item listing on the marketboards while using XIVLauncher with the in-game addon (Dalamud) enabled, or with Teamcraft running and packet capture enabled.

Unfortunately, since not everyone uses these tools, sometimes the data ends up out of date. If you want to force it to update for a specific item, you can go look at its prices yourself to send that data to Universalis. Try to convince your friends to use XIVLauncher if you can; the more people who do, the better the data will be!

### Mastercraft

> :exclamation: **Requires [custom repo #3]**

It's not a crafting bot, but it _is_ the most convenient crafting assistant short of using one. It actually works a lot like Teamcraft if you've used that, and the two pair fantastically well - Mastercraft imports crafting macros just like Teamcraft can export, to create a crafting rotation in the plugin. You also specify the minimum stats that the rotation needs, and when you go to craft something, you choose the recipe, rotation, and quantity, and hit the queue button. Yeah, you can queue multiple crafts - Mastercraft will even change your class to the necessary crafter!

You can pause the queue, automatically skip touch actions when quality is capped, and if you specify food or potions on the rotation, Mastercraft will use them for you if necessary.

### Material UI Plugin

> :exclamation: **Requires [custom repo #10]**

The game's own UI isn't bad, not by any stretch, but some users may prefer to use [Material UI](https://github.com/skotlex/ffxiv-material-ui) for a different (dark theme) look. Instead of downloading a pile of mod packages, importing them into Penumbra, and arranging priorities to resolve conflicts on the various optional settings, you can just use this plugin which lets you pick options and automatically create a Penumbra mod complete with mod option groups, no extra messing about required!

### Mini-Mappingway

The game's minimap will show party members as little dots, but what about friends and FC members? Mini-Mappingway solves that by rendering its own dots over your minimap. Unfortunately, it's also over other UI elements, but that's a technical limitation, and not a big deal. You can set priorities for colouring - if someone's a friend _and_ an FC member, which colour should be used, the friend one or the FC one? You can choose to show or hide dots for friends, FC members, and even _all players_ if you want, which can be nice for easily checking if anyone's doing a FATE that you're passing by.

### No Kill

Very simple and absolutely an install-and-forget plugin. When you launch the game and try to connect to your data centre, the game terminates if that connection fails for any reason. That can be pretty annoying if the issue was only a temporary hiccup in your connection, so this plugin just stops it from doing that. If the game fails to connect to the server, it'll just stay open so you can retry, instead of making you launch it again - which is especially annoying with one-time passwords.

### No Tank You

A simple and hard-to-miss visual display of who's screwing up their job. NTY will show a warning if you or your party (configurable) is missing an important skill, like Sage's Kardion, Dancer's Dance Partner, or any tank's tank stance. Good for learning or helping others learn. You can even make it show warnings for the Well Fed buff to remind you to eat, although those only apply in areas that are specifically listed by the user.

### No Soliciting

An absolute _essential_, this plugin blocks RMT, FC ads, RP ads, phishing, and all sorts of related crap from both chat _and_ the party finder window. You can choose what categories of stuff to block and define your own filters too (for text matches and regex patterns both) in order to remove even _system_ messages. No FF, I _don't_ want you telling me every time I enter or leave a damn sanctuary.

Once installed, just run `/nosol` to open the configuration. It should be fairly self-explanatory.

### Orange Guidance Tomestone

Are you a Dark Souls fan? Do you love the system for leaving messages on the floor in DS? Do you think more games should do that? OGT is here for you! It's a recreation of that exact system, using an external service, with a pile of custom templates and phrases you can choose from. If you miss `try finger but hole` from DS, you can now look forward to `lover ahead therefore try two-handing` in FFXIV.

Please note that all housing districts and same-size interiors share a single zone ID with others of the same type (all of Mist, for instance) so you may see messages from people in your house even if nobody else can access it. To solve this, you can use `/ogt ban` inside your house (or other zone) to never show messages in zones with that ID.

### Orchestrion

Especially with Endwalker, sometimes you really want to know what music is being played. Orchestrion will not only show the current track title in your server info bar, it'll let you force a specific track to be played, show you a list of recently played tracks, and allow you to replace tracks with others.

### Penny Pincher

Do you have a love/hate relationship with selling items on the marketboards? Is marketboard PvP something you can't get away from, even though you hate constantly adjusting prices? Penny Pincher will copy to your clipboard the lowest price of an item when you search up existing prices in your retainer, but you can make it reduce the copied price in a few ways to make undercutting simple. For example, you can always undercut by one gil, or five gil, or fourteen gil. And all you have to do is tell the plugin how to undercut, then open the item price list from your retainer, close it, and paste the new price.

### Penumbra

> :exclamation: **Requires [custom repo #9]**

Previously, to use mods - graphical changes - in FFXIV, you had to close the game, open TexTools, and import the mod. And if you had things in the wrong order, you had to start _from scratch_ because there was no priority system, it was just "last applied mod wins". And of course, these mods applied globally, not just on yourself (or others). Penumbra fixes all of this by being a _runtime_ mod loader - when the game goes to load a model or texture, Penumbra intercepts that and checks if you have a mod enabled _and_ applying to the target character. There are a lot of ways to control who the mods apply to, and you can adjust settings, priorities, and even what mods you have active, all in real-time with the game still running - and it'll let you redraw characters too, to see your changes live.

Plus, _[Mare Synchronos]_ work with Penumbra to let paired players see your character the way _you_ see your character.

### Ping Plugin

Much like the FPS plugin, this one's really simple. You can style the window, but all it does is what it sounds like: it reports your ping to the server. Convenient for estimaging how much lag you should expect to be having.

### Pixel Perfect

You probably know, if you've played for any real length of time, that the orange glowy areas around enemies are them charging up an attack, and that if you're in that area when they finish then you'll be hit. The animation doesn't matter, if they finished "casting" while you were in there, you're getting hit. What you may or may not know is that your "hitbox" for being inside that area is basically a single point. This plugin lets you make little widgets (called "doodles") to show where exactly your hitbox is, and more. You can make dots, rings, and lines, all fixed relative to your position. For instance, you can have a dot under you for your hitbox - if that's even a _little_ outside the AoE marker, you're safe. You can have a line that always points north, like a little mini-compass. You could even have a line with your current facing if you want, which can be useful out of combat.

### Positional Assistant

This one is actually by me, and its whole purpose is to help melee jobs land their positionals. It's designed to be highly configurable and support chat commands, so you can make macros on your hotbar to adjust it. The way it works is that your current (non-player) target gets up to eight lines drawn around them, colours individually configurable, to mark off the borders between front, flanks, and rear, or the four corners. If you're trying to land a flank hit, you just need to be between the right two lines. No more looking at the hitbox and hoping you're far enough over!

### PrefPro

Not actually a commonly-needed one but very cool, and potentially also very comfortable. PrefPro lets you change your character name _only_ for the purposes of NPCs and dialogue - setting your first and last names - as well as choosing what combination to use when addressing you, and even what _gender_ to address you as.

<details>
<summary>Specifics</summary>

You set the first and last names for your characters (only for NPC speech) and then you have three situations you choose the form of address for. When NPCs or dialogue use your _full_ name, your _first_ name only, or your _last_ name only, you can force it to be replaced with first-then-last, first-only, last-only, or last-then-first. All independently.

Some cultures place the family name first and the individual name last, but the game doesn't have any option to indicate that your name follows that convention. PrefPro lets you force NPCs and dialogue to do that anyway, as well as to use a different name entirely for those replacements.

Finally, you can have gendered dialogue follow your character model's sex (playing a male gets male gendering, playing a female gets female gendering) or force it to use one or the other regardless. Unfortunately, due to the nature of language and the voice lines, it's outright not possible to get gender-neutral pronouns.

</details>

### Price Insight

It might sound like you could just use the [_Market Board_](#market-board) plugin, but this one is a little different - and for things like quest rewards and crafting, much more convenient. When you mouse over an item, it retrieves pricing data (cached for an hour and a half, to not hammer the Universalis server), and displays pricing data _on_ the item's tooltip directly.

Please note that due to technical reasons, you need to redisplay the tooltip in order to see newly acquired pricing data.

### QoLBar

If you're like me, you never have enough hotbar space for all the things you'd like to put there. Especially if you also like to use custom macros to make slash commands accessible via easy buttons. This plugin will be your saving grace: it lets you define and add new hotbars, positioned anywhere you want, with buttons to run slash commands - and you can even make categories for submenus. Oh, and assign hotkeys too.

### Quest Map

If you've ever had to tab out of the game to look up questlines, or what quest you need to do to unlock some instance, or just where the quest starts, this plugin does all of that and more. You can search for quests by their name or rewards, including the duty/duties they unlock, and get an interactive map of the questlines involved - what's required for the one you want, and what it unlocks. Each of those quests can be clicked on in the map to see information about it, including a button to mark it on the map (which fails for instanced areas like the Waking Sands, unfortunately) and open it in your journal (if it's present, which means accepted or completed).

### ReAction

> :exclamation: **Requires [custom repo #12]**

Aside from a pile of useful options like insta-casting ground target actions when your cursor's in range and allowing camera-relative dash actions, you can specify actions (including just "all harmful actions" and "all beneficial actions") and then put together a queue of targeting priorities for them. For example, maybe you want _all_ attacks to prioritise targeting your "UI target" (mouseover on the enemy list), then your actual target, then your focus, then your target's target, then your _field_ mouseover target, then the last enemy you targeted, then the last enemy that attacked you... the possibilities are endless.

Oh, and it can automatically cancel your spell casts when your target dies, too.

### Ready Check Helper

Ready checks are useful in several cases, but they're not always the most convenient to actually use. This plugin will render a little green check or red X on players in the party list when they respond to the check. It's a small thing, but it's so convenient.

### RepairMe

Never again will you forget to repair your gear or extract your materia, as long as you look at the widgets from this plugin. You can get a little progress-bar style display for your most-damaged-gear's condition and your highest-spiritbonded-gear's spiritbond level, as well text percentages, and even alerts at thresholds.

### RezPls

If you play a healer, you _need_ this plugin. It will highlight, both in world _and_ in the party/alliance lists, players who need to be cleansed of negative effects, players who are _being_ raised so you don't waste your own, and even players who need to be raised in the world. And if you don't always play a healer, that's fine - you can restrict displays to jobs that can actually cleanse and raise.

### Show Gear

Another simple QoL tweak, but the fitting room and item dye windows default to only showing the specific piece of gear in question, rather than showing your existing gear _with_ that specific item. This plugin just inverts that. Now, when you go to try on a piece of gear, you'll see it combined with your current gear by default.

Please note that there are some technical oddities to the item dying window, so you may want to disable this plugin overriding that.

### Simple Tweaks

The title here is a _blatant_ lie, but it's a collection of minor-enough-to-not-need-their-own-plugin tweaks, so... close enough, I suppose? Featuring such QoL improvements as clickable chat links, disabling the title screen's idle movie, and a _wide_ assortment of UI and item-tooltip improvements, not to mention _custom chatbox command aliases_ (pretty convenient with MacroRecursion...!) this plugin does too much to describe, but I promise you'll find some useful things. Possibly my number one favourite, honestly!

### Snooper

When you're at a crowded place, especially an RP venue, it can be hard to keep track of the messages from a particular player. This plugin lets you open a window that _only_ shows messages from your target, including emotes and all the normal chat channels.

### Sound Filter

Some people, especially those with misophonia, may experience discomfort with particular sounds in this game. With this plugin, you can record a list of SFX to get the internal paths the game uses to identify them, and then block them from being played. You'll never again have to hear twelve different people crafting at once, or some of the gross noises from morbol-type mobs, or that endless blaring garlean alarm from some of the duties...

### SoundSetter

A hotkeyable window (and plugin commands) to let you adjust different volume categories (including master volume) without needing the system config window. Not only can you now macro (and therefore hotkey!) volume controls, you can also hotkey the window itself from the plugin directly, which lets you control _all_ aspects of game volume... even in cutscenes, where you can't open the system config window.

### StackSellPrice

Another one by me, and a really tiny, really simple QoL thing: on item tooltips, at the bottom, where the NPC shop-selling price is listed, this plugin just changes that so that it also shows the total price for the entire stack you're hovering over, based on the number of items in it, as well as the per-item price. It even respects NQ/HQ price differences.

### Teleporter

Personally, I find the ability to teleport via command more convenient than the menu, but this plugin doesn't stop there. You can show an "aethergate" window, which lets you add buttons for commonly-used teleports, and you can set a teleport cost threshold above which aetheryte tickets will _automatically_ be used, if you have any. It can skip the ticket popup on normal teleports. It can even take a _map zone name_ and teleport you to an aetheryte in that zone! And much like [_ChatCoordinates_](#chatcoordinates), it accepts partial names as well. `/tp idyl` and Idyllshire, here we come! Or is it Idylshire..? (It's the first, I checked while writing this.)

### TinyCommands

> :exclamation: **Requires [custom repo #8]**

Third one of mine, TC is mostly designed to extend macros with new commands, but there's nothing stopping you from using them directly. It adds a whole _pile_ of new commands, ranging from one to clear your map flag, to a way to combine `/<emote> motion` with `/em <text>` in one line, through ways to find nearby entities by name, and more. It's possibly the single most extensive utility command plugin that exists, because I can't find any others that let you do half of this.

### Visibility

Two plugins in one, sort of. The old VoidList plugin (a better blacklist than the game provides) was rolled into Visibility a while back. That one lets you completely remove a player from your game, essentially - they won't even render on your screen. No chat, no emote messages, you won't even see them.

Visibility extends this to allow you to hide rendering of _all_ players, chocobos, pets, and/or minions, by default. You can override that to show party members, friends, FC members, and dead players while still hiding the rest, too. Ever gone to an area (*cough*Limsa*cough*) and found your smooth-as-butter framerate suddenly became a slideshow presentation? This can't completely eliminate _all_ lag from highly congested areas, but it can help with overstrained GPUs and also situations where you can't see the damn activator through the mass of people in the way.

Also, you can toggle the default show/hide functionality by command, so you can macro and hotkey the ability to hide players, which is nice when you only want it in certain areas (***cough*Limsa*cough***) but not others. Hiding players by default _won't_ hide their chat or emotes like VoidList-ing someone will, by the way.

### Waymark Preset Plugin

This one's for the raiders, really. You can configure it to save and load waymark presets from/to the _game's_ preset library to/from the _plugin's_, automatically, when leaving/entering instanced areas. For example, when I enter the Vault (HSW dungeon) my vanilla waymark presets are written by this plugin so that I have one for each section, marking enemy encounter areas and treasure chests. Then I can just use the normal, builtin function to apply those waymarks. If I went to another instance, I'd be able to have it automatically load presets for _those_ areas into my vanilla waymark preset list.

If you do a lot of instances (dungeons, trials, raids, etc) that you use waymarks in (or would like to but don't want to deal with placing them every time) then you might want to install this, look at the config (which has helpful tooltips) and maybe play around with it a little.

### Where Am I Again?

Rather than opening your map to figure out where you are (world region, map zone, and even local area), this plugin will just put that info directly into your server info bar, complete with instanced area number where applicable. Tiny, but convenient.

### WoLua

> :exclamation: **Requires [custom repo #8]**

As if [_TinyCommands_](#tinycommands) wasn't enough with its conditional-execution commands, now you can write _fully custom_ chat command in Lua, and even share them with others. These commands have access to a significant amount of game information through APIs exposed to the scripts, on top of the full logical decision making capabilities of the Lua scripting language.

Since this plugin offers so much power to scripts, it can be rather complicated, but [documentation is available](https://github.com/PrincessRTFM/WoLua/tree/master/docs) online, as well as the ability to share created scripts with other users.

### Wotsit

Wotsit gives you a hotkey to open a Spotlight-style quick search from which you can look for commands, crafting recipes, gatherables, emotes, even a calculator - and more! And plugins can even register their own items with Wotsit, so that if you also have, for example, the [_Orchestrion_](#orchestrion) plugin, you can search for song titles and play them directly.

### XIVCombo (Expanded)

> :exclamation: **Requires [custom repo #4]** _(for the expanded version)_

> :exclamation: **Requires [custom repo #8]** _(for my own very expanded version)_

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
[Mare Synchronos]: <#mare-synchronos>
[Penumbra]: <#penumbra>
[Glamourer]: <#glamourer>
[Customise+]: <#customize>
[Heels Plugin]: <#heels-plugin>
[custom repo #1]: <https://raw.githubusercontent.com/LeonBlade/DalamudPlugins/main/repo.json>
[custom repo #2]: <https://plugins.annaclemens.io/>
[custom repo #3]: <https://plugins.annaclemens.io/unofficial>
[custom repo #4]: <https://raw.githubusercontent.com/daemitus/MyDalamudPlugins/master/pluginmaster.json>
[custom repo #5]: <https://raw.githubusercontent.com/Bluefissure/DalamudPlugins/Bluefissure/pluginmaster.json>
[custom repo #6]: <https://raw.githubusercontent.com/SaltyCog/DalamudPlugins/main/repo.json>
[custom repo #7]: <https://raw.githubusercontent.com/maributt/xivplugins/main/repo.json>
[custom repo #8]: <https://raw.githubusercontent.com/PrincessRTFM/MyDalamudPlugins/master/pluginmaster.json>
[custom repo #9]: <https://raw.githubusercontent.com/xivdev/Penumbra/master/repo.json>
[custom repo #10]: <https://raw.githubusercontent.com/Sevii77/ffxiv_materialui_accent/master/repo.json>
[custom repo #11]: <https://raw.githubusercontent.com/Ottermandias/AutoVisor/master/repo.json>
[custom repo #12]: <https://raw.githubusercontent.com/UnknownX7/DalamudPluginRepo/master/pluginmaster.json>
[custom repo #13]: <https://raw.githubusercontent.com/Ottermandias/Glamourer/main/repo.json>
[custom repo #14]: <https://raw.githubusercontent.com/Eternita-S/MyDalamudPlugins/main/pluginmaster.json>
[custom repo #15]: <https://raw.githubusercontent.com/Penumbra-Sync/repo/main/plogonmaster.json>
[custom repo #16]: <https://raw.githubusercontent.com/XIV-Tools/DalamudPlugins/main/repo.json>
[custom repo #17]: <https://raw.githubusercontent.com/NightmareXIV/MyDalamudPlugins/main/pluginmaster.json>
