# Setup

This guide is intended to cover the basics of setting up in-game plugins, and installing texture mods via Penumbra.

There are three main sections:
- [Setting up XIVLauncher](#xivlauncher)
- [Getting started with plugins](#plugins)
- [Importing mods with Penumbra](#penumbra)

At the bottom of this guide is a section on [troubleshooting] for common problems. If you encounter any problems not covered there, it also has links to support discord servers. If you come across a situation you think should be mentioned here, please let me know so I can see about adding it.

The [ConceptMatrix guide] has been moved to its own article, since it's both complex enough and also entirely unrelated to XIVLauncher, plugins, mods, and mod loading.


## XIVLauncher

In order to use plugins in FFXIV, you'll first need to be using [XIVLauncher], which is a much improved, faster-to-load game launcher that provides in-game plugins. By itself, the launcher is already more convenient than the official one, so even if you don't want to use any plugins at all, I highly recommend it. If you already have it, skip ahead to the [plugin setup section](#plugins) instead.

On the download page (linked above) you will need to download and run the `Setup.exe` file to install the launcher. Follow the instructions and go through the installation as normal. Once installed, you may want to replace your normal launcher shortcut for convenient; remember that plugins will _only_ function if the game is run through XIVLauncher!

When you first start the launcher, you should see something similar to the following image. Your splash screen will be different, as will your news items, the `Use One-Time Passwords` checkbox will be disabled, and there will be no username or password prefilled, as you've never logged in before.

![XIVLauncher opening screen]

Before you log in, click the gear button in the lower right. You should now see something like this, though your game path may be different. If it's not present, don't worry - just click the `...` button and locate the directory you installed the game to.

![XIVLauncher game tab]

If you want steam to see that you're playing FFXIV and give you the overlay, check the box to enable steam integration. You _do not_ need to have bought the game _through_ steam for this. Leave the additional launch arguments box empty, but you might want to run the integrity check. A small window will pop up with a little spinning progress circle as it validates your install to make sure everything will work. This might take a little while, and there's no cancel function, so be ready to wait a bit if you do. Once that's done, or if you skipped it, go to the _Game Settings_ tab at the top, where you'll see something like this:

![XIVLauncher game settings tab]

You'll want to make sure you're using `DirectX 11`, especially if you plan on using mods - they tend not to work properly on DX9. Skip over to the _In-Game_ tab now, and make sure you have the top checkbox ticked, and the bottom one _not_ ticked. The injection delay is something you probably won't have to worry about, so leave it at `0ms` for now. You should be looking at this:

![XIVLauncher addon tab]

If you want, you can go to the _Patching_ tab and set a download speed limit; if you don't, it'll download game patches as fast as it can. Everything's done for setup now, so hit the checkmark button in the lower right to save your settings and go back to the login screen.

If you bought the game through steam instead of from SE, you'll need to turn on use of the steam service account. Put in your username and password, tick the box for one-time passwords if you use the two-factor app, and hit log in to start the game! If you turned on one-time passwords, you'll see this little popup appear. Just type in your security key and hit enter or click ok to continue.

![XIVLauncher 2fa popup]

You should now be in the game, at the starting menu. Once the splash screens pass, anyway. In order to verify that everything's working, log in with any character and look at your chatlog. You should see a line saying `Dalamud v<numbers> loaded` just under any login news announcements. If you _don't_ see that, check the [troubleshooting] section at the bottom.


## Plugins

Now we get to the fun stuff: plugins to affect your game. You can find a more in-depth guide to my personal recommendations and configurations on the [recommended plugins] article, but for this particular guide, I'm going to focus on basics like how to view and install plugins.

To start with, you'll need to run the `/xlplugins` command, or use the button on the main menu screen, at the upper left. Both of these are added by XIVLauncher, and should open a window directly in your game that looks roughly like this. Note that the list of plugins you see will be different - you can hide plugins you don't want _visible_ in your browser list. Furthermore, plugins that only have testing builds won't show up unless you enable them.

![Plugin browser]

If you don't see anything showing up, check the [troubleshooting] section. Otherwise, before anything else, let's work on your user experience with the in-game addon itself. Hit the settings button on the bottom of the plugin browser window and you'll see another window come up:

![Dalamud settings]

Protip: you can drag these windows around and hit the little arrow button next to the close one to collapse them down!

Here you can configure a few things about Dalamud, the in-game addon and plugin framework supplied by XIVLauncher. You can check the options on the other two tabs too, but don't worry about the experimental tab for now. In my [recommended plugins] article, I'll give you a number of custom/unofficial plugin repo links you can put in there to get more plugins that I personally like to use.

<details>
<summary>My personal recommended settings</summary>

- Flash FFXIV window on duty pop: **ON**

	If you're tabbed out and waiting for the duty finder to match you with a party, the taskbar item for your game window will flash when it's ready.

- Display loaded plugins in welcome message: **OFF**

	Especially if you're going to have a lot of plugins like I do, the list is not only unnecessary but also too long.

- Auto-update plugins: **ON**

	This means you won't have to remember to open the menu and hit update, and there's only _very_ occasionally a broken update. Very much worth it, if you ask me.
</details>

Go ahead and hit the save and close button and get back to the plugin browser, now. Go ahead and scroll through it, click on anything that catches your eye - you can read a description written by the author, click the little world-icon button (if it's there) to go to the website/page for that plugin (usually the source code repo), and just hit the install button on it if you decide you want it. To remove a plugin, the install button becomes "disable" instead, and disabled plugins are deleted by the launcher on load.

Now, this guide is only about the basics, but it's also about installing _Penumbra_, which is a runtime mod loader. That is to say, Penumbra loads texture/model mods into the running game and applies them live, without needing to shut down and restart FFXIV. If you were looking for Penumbra in the mod browser though, you'll probably have noticed it's not there. Don't worry, that's where part three of this guide comes in:


## Penumbra

> :exclamation: **This section is outdated!** Some details may no longer be accurate, although the general information is overall still correct.

Prior to Penumbra, mods were installed via _TexTools_, which required that the game be shut down so it could replace files on disk. Penumbra, on the other hand, applies the edits to the game's _memory_, allowing it to load, activate, change, and disable mods on-the-fly. The catch is that Penumbra's still in development, so it's not yet available on the plugin browser. But don't worry, I'll walk you through installing it here.

Before you continue though, ask yourself: do you _want_ to install Penumbra? If you don't want to use _mods_ (which make purely visual changes) then you don't need Penumbra, and wouldn't use it anyway. If all you want are _plugins_ (which make mechanical/technical changes or add new features) then you can skip this section and just follow the above two.

Penumbra is currently in development and isn't available on the "official" plugin repo yet, but it recently added its own custom third party repository. This is pretty easy to set up, so don't worry. Step one is to open the plugin installer with `/xlplugins`, so get that open. Then click the "settings" button at the bottom, and this time go to the "experimental" tab. Don't worry, this isn't actually experimental. Under the custom repos section, you'll need to paste `https://raw.githubusercontent.com/xivdev/Penumbra/master/repo.json` into the box and click the plus button to add it. Make sure the checkbox under the "enable" column is ticked, then hit the "save and close" button at the bottom.

Back in the plugin installer, search for the "Penumbra" mod, click on it, and hit the install button. That's all - you now have it installed! Open up the interface with `/penumbra` and you'll be greeted with something like this.

![Penumbra settings]

You'll probably want to leave these as they are, although you might want to change the mod directory. That's up to personal preference. Don't worry about what's _in_ it right now, that'll only really matter when you start importing _Penumbra_ mods rather than _TexTools_ ones.

For the purposes of this section, I'll assume you at least _know_ about TexTools and how to install mods with it. The important bit is that you have a `.ttmp` or `.ttmp2` file - a TexTools Mod Pack. That file contains the texture and model changes as well as details on what they apply to. If you've never messed with mods before, you can look at the [XIV Mod Archive] site to find something you like.

Once you have at least one modpack file, go back to FFXIV and look at Penumbra's window. You want the _Import Mods_ tab at the top. There's only one button here, _Import TexTools Modpacks_, and that's the one to click on. It'll open a standard open-file browser, like you'd see if you hit _open_ in notepad or something. Find the TTMP file you want to import - you can control-click or shift-click to import multiple at once if you want - and let Penumbra go.

At this point, there are two possibilities: either the mod imported successfully (and you'll see no messages under the button) or something went wrong and there'll be an error. If there's an error, take a look at the [troubleshooting] section.

Assuming the import was successful, go to the _Installed Mods_ tab. You should see the mod (or mods) that you just imported showing up in the list now - congratulations, they're installed! Click on a mod to see details on the right-side pane. Here, you can toggle it on and off, see whatever description it might have, view a list of what it changes (if provided - imported mods generally don't), the files it affects, any file _conflicts_ it has with other enabled mods, and even the configuration/settings for mods that let you choose elements. It sounds like a lot, but it's really not that bad, I promise!

<details>
<summary>How do Penumbra mods work?</summary>

Mods only affect what the game _loads_. That is to say, toggling or changing settings on a mod will only take effect _after_ the thing that mod changes is loaded. If you put on modded clothing and then turn the mod off, your in-world model won't update until you change gear away and back. Unfortunately, certain elements of the game UI are basically _always_ loaded from login, like the minimap; if you want to mod the UI, you can (and some things may be visible easily) but for that particular case, you might have to relaunch. Gear, minions, mounts, bodies, furnishings, all those kinds of things are affected whenever an instance of them is loaded by the game, so you don't need to relaunch for them.

If you've changed things in Penumbra, you can try the `/penumbra redraw` command, which _may_ help. Unfortunately, UI things are not redrawn, so if you install a UI mod, you still have to restart.

</details>

<details>
<summary>Sharing mods</summary>

If you want to share a Penumbra mod, it's arguably easier than a TexTools one. Open the mod directory, find the specific folder of the mod you want to share, put it in a zipfile, and send it to someone. There's no looking through your modded items to select the ones you want to export - just zip, send, done. Importing is obviously the reverse - just put the mod folder into your base mod directory and hit _reload mods_ - or use `/penumbra reload` if you prefer. This _won't_ share any mod-specific settings you selected, mind - that's stored elsewhere.

</details>

<details>
<summary>What are mod collections?</summary>

Mod collections are just a list of enabled mods (which you must already have installed) and their settings, if any. Your installed mods list is always the same, but collections remember the enabled/disabled state for each of them and any settings the mod offers, forming a preset of sorts for what's active and how it looks.

There are three "types" of collections: default, forced, and character. By default, without configuring things yourself, there's only one _actual_ collection, and it's assigned as the default one. It's also named "Default" at start, which can be confusing.

The way that collections work is that Penumbra looks at up to two collections when loading something. When Penumbra draws an actor with a specific collection - a player or NPC that has a "character" collection for them - anything that's loaded (models, textures, etc) is looked for first in that character collection. If there's nothing overriding the normal content in there, Penumbra then looks in the "forced" collection. If there's nothing there either, the vanilla content is used.

When Penumbra loads anything that _doesn't_ have a character collection (including things like UI elements), it looks first in the "default" collection (NOT the one _named_ default, the one _marked_ as default!) and then falls back to the forced one.

What this means is that UI mods should be put in either your default or forced collection, anything you want applied to a specific character should be put into a collection that is then assigned as their character collection, anything you want applied _only_ to characters _without_ a specific collection should go in default, and anything that should be applied _universally_ (unless specifically overridden) should be in forced.

If it helps, think of it as loading all mods in the forced collection, then loading (and overriding) everything from either the applicable character collection if one exists, or else the default one.

</details>


# Troubleshooting

Sometimes, things don't work quite right. Don't worry, this section will cover the basics of troubleshooting. If things still don't work after this, you can always try the [XIVLauncher support discord server].

## I don't see the message about Dalamud loading when I log in!

Step one is to whitelist XIVLauncher in your antivirus. If that doesn't work, something else may be interfering.

<details>
<summary>Whitelisting XIVLauncher in your antivirus</summary>

You'll need to whitelist the following three folders:
- `%localappdata%\XIVLauncher`
- `%localappdata%\goatsoft`
- `%appdata%\XIVLauncher`

To get the exact paths, open up your file browser window, click the address bar, and paste those in. Press enter to go to them, then click the address bar again and copy the new path. Once you've whitelisted those paths, you may need to reinstall the launcher or restart your computer, depending on your antivirus. If things still aren't working, you can join the [XIVLauncher support discord server] and ask for help in the `#xivlauncher_issues` channel.

</details>

<details>
<summary>Known and probable interferences, from the support discord</summary>

- RivaTuner/RTSS
- OBS
- MSI Afterburner (contains RTSS)
- MacType
- Reshade, GShade, and similar apps
- Discord (sometimes; depends on how fast it hooks for its overlay - if it hooks _after_ Dalamud then everything works)

If you use any of these, you may have to block them from affecting FFXIV, or delay them so that Dalamud has time to hook the game first.

</details>

## I have the Dalamud message, but no plugin windows are showing up!

This is almost certainly because something else is hooking the game's DirectX render before Dalamud can. Some things play well together and have no issue, some things work fine as long as they hook the game _after_ Dalamud, and some things just don't work at all. Check the list above for known and probable interferences.

## Penumbra failed to load my modpack file!

This is _usually_ due to a "dirty" modpack file. There are two ways to clean them.

<details>
<summary>The good way</summary>

TTMP files are basically zip files with only two files inside them: `TTMPD.mpd` and `TTMPL.mpl`. If you open up the modpack file with something like 7zip or winrar and see any _other_ files (some authors include screenshots in their modpack) you should delete them and try importing again.

This _usually_ happens with "advanced" modpack files that let you choose options when you import them. TexTools lets mod authors include screenshots of the options to help you decide what you want, but Penumbra may have trouble understand modpack files with those extra screenshots.

</details>

<details>
<summary>The other way</summary>

If that doesn't work, then unfortunately your best bet is to import the mod into TexTools and then re-export it to a new, fresh `.ttmp2` file. This will usually require closing the game, although it's entirely possible to create a _second_ installation specifically for TexTools. Unfortunately, if the modpack file is an advanced one with configuration options, you _won't_ be able to change them live in Penumbra, because TT only imports the options you choose to apply at mod installation, which means the exported modpack file will only have those options in it.

If you have the patience and you're willing to dig around in the guts of the Penumbra mod, you can try exporting every combination of options that you're interested in and manually creating the options in the Penumbra mod, but that's pretty advanced, and I'm not going to go into details about it here.

</details>



[Troubleshooting]: <#troubleshooting>
[XIVLauncher]: <https://github.com/goatcorp/FFXIVQuickLauncher/releases/latest> "Latest XIVLauncher release"
[Penumbra]: <https://github.com/xivdev/Penumbra/releases/latest> "Latest Penumbra release"
[XIV Mod Archive]: <https://www.xivmodarchive.com/>
[XIVLauncher support discord server]: <https://discord.gg/3NMcUV5>
[ConceptMatrix guide]: <cmtool.md>
[recommended plugins]: <plugin-recs.md>
[Penumbra mod metadata]: <penumbra-metadata.md>
[XIVLauncher opening screen]: <img/launcher-front.png>
[XIVLauncher game tab]: <img/launcher-settings.png>
[XIVLauncher game settings tab]: <img/launcher-game-settings.png>
[XIVLauncher addon tab]: <img/launcher-in-game-addon.png>
[XIVLauncher 2fa popup]: <img/launcher-2fa.png>
[Plugin browser]: <img/plugin-browser.png>
[Dalamud settings]: <img/dalamud-settings.png>
[Penumbra settings]: <img/penumbra-settings.png>

