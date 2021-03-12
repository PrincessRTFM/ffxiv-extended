# ConceptMatrix In a Nutshell

ConceptMatrix, also called CMTool or CMT for short, is a program designed to write to FFXIV's memory while it's running in order to make purely visual, your-client-only changes. Its most common use is taking screenshots.

## Getting Started

First things first, you'll need to download [CMTool]. Make sure you get the `CMTool.zip` file, not one of the source code ones! This zipfile has a handful of files and some folders in it, which you need to keep together. Make a folder for it wherever you like - I personally used `Documents\My Games\FFXIV\ConceptMatrix` to keep things nicely organised. Extract the contents of the zipfile to wherever you chose to install it, then you'll probably want to whitelist that whole folder in your antivirus. CMT is designed to modify the memory of a separate running program, which is a _major_ red flag in most antivirus apps - and for good reason - but in this case, it's a false positive.

Once you have CMT set up and whitelisted, run the `ConceptMatrix.exe` file. It'll automatically check for updates on its own, so you can just make a shortcut to it for easy access. Give it a minute to start up, and you'll see something like this - assuming you have the game running. If not, launch it.

![CMT actor data]

Note that I've switched to the dark theme, but light is the default. I'll tell you how to change in a moment. First, this may be a bit overwhelming, so let's break it down a little...

![CMT actor breakdown]

Ignore everything I blurred out for now. We'll come back to most of that later. First things first, unless you ~~are a filthy godless heathen~~ actually want to keep light mode, hit the little hammer-and-wrench button on the menu bar, underneath that row of buttons and stuff at the very top. You'll probably want to toggle to _Zodiark Theme_, in the upper left. Feel free to ignore the rest of that page, it's mostly user-preference stuff. Now, back to the _Actor Data_ page.

First off, picking an actor to target is fairly easy. That's the dropdown in the upper left corner - it defaults to your character, which is probably the one you'll mostly be sticking with. If you move around in the game, you can hit the arrow-cirle button right next to it to reload the list of actors, in order to target an NPC if you want. Note that some actors may be "present" in the game but not visible. Don't blame CMT, that's on SquareEnix - they made the actors be _there_ in game data even when they're not showing up.

In order to change details about your chosen actor, _check the box_ next to the aspect you want to change, then change it. While it's possible to just type raw values into the box, you'd need to know the numeric ID of the value you want to use; it's far easier to just hit the "view" button next to it, wait a second or two if necessary while CMT loads the options, and then click the one you want. Of course, some things only take raw values, like height and bust size - for those, you probably know the allowed range (those two are both 0-100, for instance) but if you don't, you can always try just messing around. Or look online for details on that field, or ask someone for help, or go to the [CMTool support discord server]... you've got options.

If you've been trying that as you read, you'll probably notice that your target doesn't look any different. You need to hit the _Actor Refresh_ button at the top to make the game refresh their appearance data and apply your changes. You'll see your target briefly vanish and immediately fade back in with whatever changes you made. If you're feeling adventurous, you can hit _Randomize Appearance_ to roll the dice and see what you get!

Now that you've made some changes, maybe you want to tweak another actor. Perhaps you've got a friend that you'd like to take some screenshots with! Before you select them in the dropdown, you'll probably want to hit the _Unfreeze All_ button first. That just unchecks all of the "freeze value" checkboxes, which means that when you select your next target actor, the fields will update to match them. If you don't unfreeze the values first, then those fields will be applied to the new target. Good for copying specific aspects of a look onto a lot of actors, but if you're not trying to do that, then you'll want to make sure those boxes are all unchecked.

While you're looking up there, the _Load Appearance_ and _Save Appearance_ buttons let you save all of an actor's appearance data - the stuff you're looking at on the left here and a few bits from the right - in CMT, so you can basically clone their look onto another actor at any time. You can use that for things like making a party scene with NPCs not normally in that area, for example. The _Load State_ and _Save State_ buttons are for a quick backup of the current values; they are _not_ persistent and there's only one backup slot, so it's only for when you're trying things out and want to be able to return to some specific set of changes if you don't like your new idea.

I'm going to skip over the _Actor Properties_ page here since most of those controls are either self-explanatory or far beyond the scope of this guide. Feel free to poke around in it though - maybe being able to fine-tune various colours on your target actor will come in handy for fancy screenshots!

![CMT equipment]

The equipment page is pretty much what it sounds like - you can view lists of _all_ equipment in the game and make your target wear whatever you want. Be aware that this _will_ let you "wear" items that your target can't _actually_ wear, like race-specific gear. It won't render properly. Nothing should break, but the game won't know what to do. It'll also allow you to dye undyable items, which is only useful with mods - undyable items don't actually have the data to change their look based on dyes. Understandably so, I should think.

You can use this to prototype outfits and preview makeover results before spending money - gil or the real stuff - on whatever you'd need to get there. Of course, you can also just set an outfit you know you like for screenshots even if you don't own the actual pieces.

One more tip: you can fully hide your main/off hand items here by zeroing the scales for them. Even if you're in battle stance, they won't be visible.

I'm skipping ahead to the _World_ page now, but I'll come back to the _Posing Matrix_ one later. Not the old one, you want to use the new one.

![CMT world]

You have _complete_ control over your camera here. You'll need to check the box to freeze the values before changing them, but it can be very useful for screenshots when you need to get that _perfect_ angle. The most useful fields here are zoom/FoV, rotation, and the locations. Once you're in gpose mode, you can also mess with the filters to apply whatever you want all at once!

For the weather boxes, _force_ weather applies instantly, but only works outside of gpose. The normal weather box takes a few moments to transition but works inside gpose too. You can control the game time with the top number, but it's definitely not 1:1, so you'll probably need to use the slider to get the approximate area of the day and then the +/- buttons to get exactly where you want. That time next to them is the in-game time and updates as the game plays as well as with your changes.

Now, for posing...

![CMT posing matrix]

_(This guide is still being written, and further content isn't yet done. Sorry for the delay!)_
<!-- please don't be mad, I'm literally doing this all on my own time and I've already written the main guide today, PLUS half of this one .-. I'll try and get the rest up soon! -->



[CMTool]: <https://github.com/imchillin/CMTool/releases/latest> "Latest CMTool release"
[CMTool support discord server]: <https://discord.com/invite/crystallinemeans>
[CMT actor data]: <img/cmt-actor-data.png> "For privacy, I've blurred out my name and FC, as well as the location that's listed in the titlebar"
[CMT actor breakdown]: <img/cmt-actor-breakdown.png>
[CMT equipment]: <img/cmt-equipment.png>
[CMT world]: <img/cmt-world.png>
[CMT posing matrix]: <img/cmt-posing-matrix.png>
