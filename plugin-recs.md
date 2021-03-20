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

### Globetrotter

A treasure hunter's _best_ friend - when you decipher a map or use the `/tmap` command with one in your inventory, Globetrotter will open your game map and place a flag where the treasure is located. Just like that. No more searching and squinting, no more wondering if the map matches that site or you're just seeing things, no more trying to recognise tiny fragments of maps... Globetrotter will tell you _exactly_ where to go.

### Good Memory

Have you ever been in an instance and an orchestrion roll comes up in the loot and you just _can't remember_ if you've already gotten that one? _Good Memory_ adds a line to the tooltip on things like orchestrion rolls and minions telling you whether you've already acquired it or not. No configuration, no checklists, no keeping notes, no gambling and hoping you're right - just look at the tooltip and it'll tell you straight. ~~And SE said they couldn't implement it...~~

### Item Search

A catalog of _every item in the game_ - searchable, filterable, and with options like linking it in your local chatlog (as an `/echo` type message - you can right-click -> `Link` for sending messages or hit `Try on` for gear!) or looking it up on garland tools or teamcraft. If you also have the [_Market Board_](#market-board) plugin (see below) you can look up the item directly from the catalog!

On top of that, it comes with a "fitting room" feature that lets you save outfits from the "try on" window, open that window with the `/fittingroom` command, and load your saved outfits into the window.

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

### Macro Recursion

The name is only slightly misleading - it doesn't let you call macros like subroutines or functions, it adds a `/runmacro` command that can be used from _within_ macros (or the chatlog if you want) to run a specific macro. Normally, XIV macros are limited to fifteen lines, including any `/macroicon`, `/macroerror`, etc. This plugin lets you make the last line a `/runmacro` command to immediately jump to another one - or, and this is where the recursion comes in, to call _itself_.

<details>
<summary>Examples</summary>
#### Infinite Bread
```
/micon "break fast" emote
/bread <wait.11>
/bread motion <wait.11>
/runmacro 25 shared 3
```
#### Infinite Riceball
```
/micon "eat rice ball" emote
/riceball <wait.11>
/riceball motion <wait.11>
/runmacro 26 shared 3
```
> :warning: **You will need to edit the last line** if you intend to copy these examples! In the macro window, select the macro you want to run from the command and look at the lower left corner. You'll see "Macro _[number]_" - that number is the macro ID. Look at the top of the window to see if the macro you want to run is in the _individual_ or _shared_ page. The command is `/runmacro [ID] [page] [optional line number]` - if you provide a line number, the macro will be started from that line, otherwise from the first.
</details>

### Market Board

Mentioned briefly in the [_Item Search_](#item-search) plugin above, this plugin provides an on-demand window to search the player markets. You can search by name and filter by all of the standard market categories, but you can't access your favourites or wish list - because it's not looking up the game markets directly from your character. The thing is, it _can't_ do that - there's no way to access that except through an in-game marketboard activator.

There's a service called _Universalis_ that tracks marketboard prices for items, across every single game world. It tracks what's currently available and sales that were made, and XIVLauncher (and Teamcraft, if you use that) both send (anonymous) updates whenever you look something up on the markets. You don't have to do anything to make it happen, just look at an item listing on the marketboards while using XIVLauncher with the in-game addon (Dalamud) enabled, or with Teamcraft running and packet capture enabled.

Unfortunately, since not everyone uses these tools, sometimes the data ends up out of date. If you want to force it to update for a specific item, you can go look at its prices yourself to send that data to Universalis. Try to convince your friends to use XIVLauncher if you can; the more people who do, the better the data will be!

### No Kill

> :exclamation: **Requires [custom repo #3]**

Very simple and absolutely an install-and-forget plugin. When you launch the game and try to connect to your data centre, the game terminates if that connection fails for any reason. That can be pretty annoying if the issue was only a temporary hiccup in your connection, so this plugin just stops it from doing that. If the game fails to connect to the server, it'll just stay open so you can retry, instead of making you launch it again - which is especially annoying with one-time passwords.

### No Soliciting

An absolute _essential_, this plugin blocks RMT, FC ads, RP ads, phishing, and all sorts of related crap from both chat _and_ the party finder window. You can choose what categories of stuff to block and define your own filters too (for text matches and regex patterns both) in order to remove even _system_ messages. No FF, I _don't_ want you telling me every time I enter or leave a damn sanctuary.

Once installed, just run `/nosol` to open the configuration. It should be fairly self-explanatory.

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

### Simple Tweaks

The title here is a _blatant_ lie, but it's a collection of minor-enough-to-not-need-their-own-plugin tweaks, so... close enough, I suppose? Featuring such QoL improvements as clickable chat links, disabling the title screen's idle movie, and a _wide_ assortment of UI and item-tooltip improvements, not to mention _custom chatbox command aliases_ (pretty convenient with MacroRecursion...!) this plugin does too much to describe, but I promise you'll find some useful things. Possibly my number one favourite, honestly!

### Slidecast

A tiny QoL improvement, but it can make a big impact. If you don't know, _slidecasting_ is a game mechaninc wherein you can safely move your character during the _last half-second_ of casting spells and attacks, without cancelling them. It may not sound like a lot, but it can be the difference between getting hit by an enemy and dodging while still successfully attacking. The thing is, you have to get it in the last half-second or you'll waste your cast. This plugin adds a little white line on the casting bar indicating when it's safe to move - once the cast progress reaches that line, you're good to slidecast. The visual display can be much easier to use than watching the number, at least for some people.

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

> :exclamation: **Requires [custom repo #2]** _(only for the expanded version)_

You probably know about _skill chains_ in XIV - certain skills get _combos_ when used after others, which make them do more damage or add an extra effect. Generally, you want to follow the chain. For example, if you play Machinist, you want to use (heated) split shot, then follow it with (heated) slug shot, then finish the chain with (heated) clean shot. If you use plain Slug Shot _without_ first using (heated) split shot, you do 100 potency of damage. If you follow the chain, you do _260_ potency of damage instead, just with that skill - nevermind what (heated) split shot does first.

The issue with this is that you need another hotbar button (and probably keyboard button) for each of those three skills. That can fill your hotbars up pretty fast, and can be annoying or even difficult to hit the keybinds while still moving. Enter XIVCombo.

XIVCombo _condenses_ those skill by having you only place the _end_ skill of the chain on your hotbar, and dynamically replacing it on the fly. Continuing the above example, you would place (heated) clean shot on your hotbar, and the plugin would remember that while replacing it with (heated) split shot. When you use that one - the first attack in the chain - and the second attack is ready to combo, the button is replaced with the next one. Again so for the third one. Suddenly your three-move combo chain is all on a single button!

There are a fair number of these button-replacement chains that XIVCombo offers, and various forks may include even more. All of them are toggleable - you choose only the ones that you actually want, that fit your playstyle - and start out disabled by default, so as not to mess anything up. Install the mod and then look at the config; it's organised by job and each section has checkboxes to control the chain replacements and a little line by each with details.

> :bangbang: **There's an official version of this plugin**, and then _several_ different _unofficial_ versions, ranging from the one I use to one that's about two steps removed from a bot - which I will _not_ be linking here.

### YesAlready

> :exclamation: **Requires [custom repo #2]**

If you've gotten sick of having to tell the game that yes, you really did mean to click that, you're sure, you just want to do the thing, will it shut up and do what you told it to already, then this plugin might just save your sanity. Not only can you select categories of confirmation boxes to auto-confirm, you can even use plain-text _and_ regex matching for all of the popups. The plugin even recognises when there's a confirmation checkbox to be ticked as well as hitting the button, and takes care of that for you too! Finally, you can extract materia from things without the game bugging you for _every single item_ to be _extra_ sure.



[Webhook]: <https://github.com/adnanh/webhook/> "Define custom webhooks to invoke other programs, passing data directly through - available for windows and linux, can be compiled from source"
[custom repo #1]: <https://raw.githubusercontent.com/LeonBlade/DalamudPlugins/main/repo.json>
[custom repo #2]: <https://github.com/daemitus/MyDalamudPlugins/raw/master/pluginmaster.json>
[custom repo #3]: <https://raw.githubusercontent.com/Bluefissure/DalamudPlugins/Bluefissure/pluginmaster.json>
