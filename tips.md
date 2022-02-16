# Things FFXIV Doesn't Tell You

There are a number of features, ranging from the merely useful to the outright invaluable, that aren't actually explained in the game, or if they are, it's done pretty poorly or it's hard to find. This guide is an ongoing attempt to explain those things.

## In no particular order...

Someday I might try to organise this. If I can ever figure out how.

### Chat Placeholders

Chatbox magic! There are a [fairly significant number](https://na.finalfantasyxiv.com/lodestone/playguide/db/text_command/placeholder/) of "placeholders" you can put into your chat messages that will be replaced. Perhaps the most useful two are `<pos>` and `<flag>` - and if you don't know about [map flags](#map-flags), keep reading.

The first (`<pos>`) is replaced with your current player location, as a _clickable_ link that will place a map flag at that spot. It's not a live-update or anything, it's just a link to the particular coordinates that you are currently at.

Likewise, `<flag>` will make a clickable flag-setting location link for wherever your map flag currently is. If you don't have one, it'll turn into a plain text string saying so instead, mind.

### Auto-translation

Since FFXIV is an international game, you might encounter players who don't speak the same language as you. There are four client languages available, but that doesn't help with player chat - except the devs thought of that! There's a whole library of phrases (including, I believe, _every single action name_) that you can use that will automatically translate into the client language of everyone who receives the message. You'll recognise them by the green curved arrow on the left and the red one on the right.

To use these, just hit tab in your chatbox or the macro editor. If you've got a partial phrase written out that's in the autotranslate library, it'll filter down to matching ones, to help you find what you want. Otherwise, you can look through the various categories. Anyone who sees the result will have it in whatever language they play the game in!

### Map Flags

One of the most useful features, IMO. Open up your big map - either by hitting the keybind (default `m`) or clicking on your minimap - and hold _control_, then right click somewhere. Tada! You get a red flag on the map at the location you clicked!

While in the map zone with your flag, it'll _always_ show on your minimap, like a special gathering node. If it's off the edge, it'll be smaller with an arrow pointing in its direction. If it's in a different zone, there's no indication of it, but you can use the [`<flag>` placeholder](#chat-placeholders) to see where you left it if you want - `/echo <flag>` is nice and easy.

You only have _one_ flag, and if you click on a location link in the chat, it'll be set to wherever the location was. If you move it, you replace the old one. If you just want it gone, right click on it without holding `control` and it'll go away.

As an aside, any time you manually place your flag, the `<flag>` placeholder is appended to your chatbox if it's not already in there somewhere. Annoying, but what can you do?

### Finding Aetherytes

On the big map, while holding `control` all aetheryte icons are moved to the foreground, over all other icons. Since [flags](#map-flags) are placed with _right_-click, you can _left_-click to teleport while holding `control` and you won't get a flag placed. It's a small thing, but it means you don't have to zoom waaay in when there's a bunch of stuff around the aetheryte!

### Easy Item Turn-in

In the quest item turn-in window - the one where you have boxes showing what items you need to give the NPC - you can just right click on the item box in that window to be given a list of _all_ applicable items in your inventory. Main inventory only, not armoury chest, so if it's gear then you might have to remove it first. Just click on the item you want to use for that turn-in and it'll be selected for you - no more searching through all of your inventory tabs!

### Ride Along Teleportation

If you've played for any appreciable length of time, you probably know that teleporting to an aetheryte costs gil. If you didn't, well, now you do. As an aside, you can register "favoured" destinations for 50% price (three by default, four if you register the companion app) and a single "free" destination for, as the name implies, free (if you use 2fa on your account), on top of the "home" one that you `/return` to.

But if you're in a party and you teleport, then all party members in the same map zone who have also unlocked the aetheryte you go to will be offered a _free_ ride-along teleport. There's no fee for anyone, not you and not them, and it doesn't expire. If they change zones, it's lost, but otherwise they can teleport there for free half an hour after you, if they were busy. And still want to go there half an hour later for some reason.

### Action Macros

Never use macros for combat actions, because

1. they can't make use of the action queueing system, and
2. any actions they run won't either, and
3. they soft-lock you into their particular course of action, although
4. only _one_ macro can run at a time, and unless you use `/macrolock` in it, others will interrupt it, while
5. if you _do_ use `/macrolock` in your macro, you can _only_ interrupt it with the "stop current macro" keybind (default unbound) or the `/macrocancel` command

There is precisely **one** exception to this: certain actions (most especially _Limit Break_) must be ground-targeted... _unless_ you use the `/action` command to invoke them **with a specified target**.

I'll save you the trouble of looking up the command and tell you how it works: `/action "Action Name Here" [target here]`, where the action name _must_ be in quotes if it has spaces, and the target is generally best done with a [placeholder](#chat-placeholders). As an example, this macro will attempt to use your Limit Break on your current target, and if it fails, it'll fall back to ground-target mode:

```
/micon "Limit Break" action
/merror off
/action "Limit Break" <t>
/action "Limit Break"
```

The first line gives it the _Limit Break_ icon so you can easily recognise it on your hotbar, the second turns off errors like "invalid target", and the third and fourth use the action.

This _can_ be used for other actions that default to ground-target mode, but remember the first, second, and fourth caveats above.

### Enemy Signs

There are fourteen "enemy signs" in the game: target to attack (1-5), target to bind (1-3), target to ignore (1-2), square, cross, circle, and triangle. Despite the name, they can be applied to players as well. Not a whole lot of players I've seen tend to use them, but they can be useful to indicate to your party what needs to be killed first, or what needs to be stunned/bound, or what shouldn't be touched. In larger instances, some players mark tanks/healers to better keep track of them. It's also fairly common to mark a player with the triangle if they know the current duty, so others know to follow their lead. If someone ever says to follow the dorito, that's what they mean.

As it happens, there are [placeholders](#chat-placeholders) for each of those signs. Combined with something like the `/target` command, you can easily make macros to automatically target whatever mob has a given sign. For example:

```
/micon attack1 enemysign
/merror off
/target <attack1>
```

First line makes the button look like the "target to attack #1" symbol, second silences errors in case there isn't anything with that mark, and the third targets whatever has it. Just adjust the `attack1` in the first and third lines to change the sign used.

