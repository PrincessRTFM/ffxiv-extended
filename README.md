# Setup

This guide is intended to cover the basics of setting up in-game plugins, and installing texture mods via Penumbra.

There are three main sections:
- [Setting up XIVLauncher](#xivlauncher)
- [Getting started with plugins](#plugins)
- [Importing mods with Penumbra](#penumbra)

At the bottom of this guide is a section on [troubleshooting] for common problems. If you encounter any problems not covered there, it also has links to support discord servers. If you come across a situation you think should be mentioned here, please let me know so I can see about adding it.

The [ConceptMatrix guide] has been moved to its own article, since it's both complex enough and also entirely unrelated to XIVLauncher, plugins, mods, and mod loading.


## XIVLauncher

In order to use plugins in FFXIV, you'll first need to be using [XIVLauncher], which is a much improved, faster-to-load game launcher that provides in-game plugins. By itself, the launcher is already more convenient than the official one, so even if you don't want to use any plugins at all, I highly recommend it. If you already have

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

To start with, you'll need to run the `/xlplugins` command. It's added by XIVLauncher, and should open a window directly in your game that looks roughly like this. Note that the list of plugins you see will be different - you can hide plugins you don't want _visible_ in your browser list, and also any installed plugins will be moved to the other tab. Furthermore, plugins that only have testing builds won't show up unless you enable them.

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

Prior to Penumbra, mods were installed via _TexTools_, which required that the game be shut down so it could replace files on disk. Penumbra, on the other hand, applies the edits to the game's _memory_, allowing it to load, activate, change, and disable mods on-the-fly. The catch is that Penumbra's still in development, so it's not yet available on the plugin browser. But don't worry, I'll walk you through installing it here.

Before you continue though, ask yourself: do you _want_ to install Penumbra? If you don't want to use _mods_ (which make purely visual changes) then you don't need Penumbra, and wouldn't use it anyway. If all you want are _plugins_ (which make mechanical/technical changes or add new features) then you can skip this section and just follow the above two.

Unfortunately, while Penumbra _itself_ doesn't require restarting the game to apply mods, _installing_ Penumbra does - you'll need to shut down when you install or update it, until it's officially released to the plugin browser.

To start, you'll need to download [Penumbra] as a zip file. On that page, make sure you download `Penumbra.zip` and _not_ one of the source code zipfiles! Open it up and get ready to extract it, but you'll need to put it in a specific place. For that, open up your file browser, click the address bar, and paste `%appdata%\XIVLauncher\devPlugins` into it, then hit enter to go there. You might want to pin this in your quick access section, because you'll be coming back here any time you need to update Penumbra.

This directory is initially empty, and that's fine - normally, it's not actually used. But like I said, Penumbra's still in development. Make a folder here, call it whatever you like - I personally used `Penumbra` for simplicity - and go into it. _This_ is where you need to extract that `Penumbra.zip` file from earlier - just drop all of the files from it right in here. And that's it - you just installed Penumbra. Hooray!

Go ahead and relaunch your game, log in, but don't connect with a character yet - see the little "manage mods" button in the lower right? That's from Penumbra. It'll go away once you log in to a character, but there's a command to open the same interface that button does: `/penumbra` - nice and simple. Either log in and use that command or hit the button now, and you should see something like this.

![Penumbra settings]

You'll probably want to leave these as they are, although you might want to change the mod directory. That's up to personal preference. Don't worry about what's _in_ it right now, that'll only really matter when you start importing _Penumbra_ mods rather than _TexTools_ ones.

For the purposes of this section, I'll assume you at least _know_ about TexTools and how to install mods with it. The important bit is that you have a `.ttmp` or `.ttmp2` file - a TexTools Mod Pack. That file contains the texture and model changes as well as details on what they apply to. If you've never messed with mods before, you can look at the [XIV Mod Archive] site to find something you like.

Once you have at least one modpack file, go back to FFXIV and look at Penumbra's window. You want the _Import Mods_ tab at the top. There's only one button here, _Import TexTools Modpacks_, and that's the one to click on. It'll open a standard open-file browser, like you'd see if you hit _open_ in notepad or something. Find the TTMP file you want to import - you can control-click or shift-click to import multiple at once if you want - and let Penumbra go.

At this point, there are two possibilities: either the mod imported successfully (and you'll see no messages under the button) or something went wrong and there'll be an error. If there's an error, take a look at the [troubleshooting] section.

Assuming the import was successful, go to the _Installed Mods_ tab. You should see the mod (or mods) that you just imported showing up in the list now - congratulations, they're installed! Click on a mod to see details on the right-side pane. Here, you can toggle it on and off, see whatever description it might have, view a list of what it changes (if provided - imported mods generally don't), the files it affects, any file _conflicts_ it has with other enabled mods, and even the configuration/settings for mods that let you choose elements. It sounds like a lot, but it's really not that bad, I promise!

<details>
<summary>Mod "metadata" - name, description, etc</summary>
At present, you can't _modify_ any of the metadata - you can't rename it, write your own description, tag what items it affects, things like that. That requires you edit the mod's `meta.json` file in the mod directory, so advanced users might want to do that sort of thing, but it's beyond the scope of this guide. If you're interested, JSON is a fairly easy-to-edit format, and you can find all sorts of tools online to help with it.

If you're curious about editing mod metadata to add descriptions, website links, change item lists, and the like, then you can look at my [Penumbra mod metadata] guide for more details. This guide is just for setting up mods.
</details>

<details>
<summary>How do Penumbra mods work?</summary>
Mods only affect what the game _loads_. That is to say, toggling or changing settings on a mod will only take effect _after_ the thing that mod changes is loaded. If you put on modded clothing and then turn the mod off, your in-world model won't update until you change gear away and back. Unfortunately, certain elements of the game UI are basically _always_ loaded from login, like the minimap; if you want to mod the UI, you can (and some things may be visible easily) but for that particular case, you might have to relaunch. Gear, minions, mounts, bodies, furnishings, all those kinds of things are affected whenever an instance of them is loaded by the game, so you don't need to relaunch for them.
</details>

<details>
<summary>Sharing mods</summary>
If you want to share a Penumbra mod, it's arguably easier than a TexTools one. Open the mod directory, find the specific folder of the mod you want to share, put it in a zipfile, and send it to someone. There's no looking through your modded items to select the ones you want to export - just zip, send, done. Importing is obviously the reverse - just put the mod folder into your base mod directory and hit _reload mods_ - or use `/penumbra reload` if you prefer. This _won't_ share any mod-specific settings you selected, mind - that's stored elsewhere.
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

This _usually_ happens with "advanced" modpack files that let you choose options when you import them. TexTools lets mod authors include screenshots of the options to help you decide what you want, but Penumbra doesn't understand modpack files with those extra screenshots.
</details>
<details>
<summary>The other way</summary>
If that doesn't work, then unfortunately your best bet is to import the mod into TexTools and then re-export it to a new, fresh `.ttmp2` file. This will usually require closing the game, although it's entirely possible to create a _second_ installation specifically for TexTools. Unfortunately, if the modpack file is an advanced one with configuration options, you _won't_ be able to change them live in Penumbra, because TT only imports the options you choose to apply at mod installation, which means the exported modpack file will only have those options in it.
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
