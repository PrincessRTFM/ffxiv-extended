# Penumbra Metadata

The first thing you need to know is where Penumbra's _storing_ this data. Once you have it installed (see [Plugins and Mods] for a setup guide) you can open the interface and click the _Open Mods Folder_ button in the plugin window. You might want to pin that folder to your quick access list if you intend to be back often.

Within the _root folder_ here, you'll see a file called `collection.json` as well as folders for any mods you've installed, whether they're active or not. Within each mod directory will be a `meta.json` file; the rest of the contents are the actual content of the mod.

As you've probably guessed, editing mod metadata means you'll need to understand JSON. If you don't, there are plenty of guides online about it, but it's _well_ beyond the scope of this article. Alternatively, you can use a visual JSON editor so you don't have to worry about syntax. There are lots of those online too.

For the moment, you'll probably want to ignore `collection.json` since there's really no reason to hand-edit that. At the end of this guide will be a section on the [modlist JSON] that will talk about that and what you can do with it, but unless you're a programmer you probably won't care.

## Mod Metadata

Assuming you've got at least one mod installed, pick whatever mod folder you want and open it up. If you haven't installed any mods yet, you'll need to do that first. See the [Plugins and Mods] guide for details and help.

Inside the mod folder, you'll see a `meta.json` file, as well as some other stuff. There'll probably be a folder, maybe a couple of them depending on the mod in question. You can safely ignore everything except that `meta.json` file. Go ahead and open that up.

> :exclamation: **If you see a solid block of text**: the file contents may be compressed/unformatted and lacking things like line breaks and indentation. You can find plenty of JSON formatters online; just paste the contents into one, then paste the formatted text back into the file instead of the original stuff.

Once you've gotten it formatted, you can easily see what fields are stored here. A number of them are probably empty; Penumbra is okay with some fields not having any data, but they must all exist.

<details>
<summary>Example metadata content</summary>
```json
{
	"Author": "Illyriana",
	"ChangedItems": [
		"Plush cushion"
	],
	"Description": "A higher-quality Plush Cushion minion",
	"FileSwaps": {},
	"FileVersion": 0,
	"Groups": {},
	"Name": "Minion - Better Plush Cushion",
	"Version": "1.0.0",
	"Website": null
}
```
</details>

> :exclamation: **The `Groups` field may be a massive entry**, in which case just _ignore it all_. That particular field is used to store mod configuration options, to allow changing settings live in the Penumbra modlist page. It'll be explained in the [Advanced Metadata] section below.

The fields you'll probably be interested in are
- `ChangedItems` (an array of strings, each entry will be listed on a separate line in Penumbra)
- `Description` (a single string, will be listed in the _About_ tab on Penumbra)
- `Name` (single string, will be used as the text for the mod's entry in Penumbra's _Installed Mods_ list)
- `Website` (will be openable with a button on the mod's entry)

> :bangbang: **The mod name is _only_ take from the `Name` entry**, not from the mod's folder! However, Penumbra tracks your mod list (ordering, enabled/disabled status, and any relevant mod settings) by the folder name. If you rename the folder, you'll need to hit _Rediscover Mods_ and rearrange your ordering, set what's turned on and what's not, and reapply any configuration.

You can edit these fields to give yourself some more information in the modlist, which can be invaluable with a lot of mods or when you have multiple mods that affect the same thing. If you want to use line breaks in the description, use the four-character sequences `\r\n` wherever you want the line break to be. That's _one_ line break, so you need to write that _twice_ for a blank line, for example.

> :warning: **JSON has a very strict syntax**, so if you're hand-editing this file, it's probably a good idea to run it through a validator before reloading your mods. You can find them all over the internet, just make sure it's fully compliant with the strict spec. If Penumbra fails to parse a JSON file, it'll crash and you'll have to close your game, find and fix the file, then relaunch to get it working again. It may be worth finding and using a visual JSON editor tool online instead of hand-writing the fields, if you're not sure.

Once you've made your changes and saved the file, just go back to Penumbra and hit the _Rediscover Mods_ button. There's no need to relaunch the game like with TexTools. If you go to the _Installed Mods_ tab and look at your modlist, you'll see whatever changes you made are live. As long as you didn't rename the mod folder, it'll still be in the same position, and any configuration settings will be remembered.

## Advanced Metadata

Some mods allow you to select different options for them. For example, a minion mod might offer different colour schemes for its edits, or a gear mod might have optional pieces of the new model that you can choose from. All of those options - not which one you've chosen, but the definition of what options are _available_ - are stored in the `Group` field of the `meta.json` file.

> :bangbang: **In almost all cases, you won't need or want to edit this** - however, I have personally run into a situation where I needed to in order to fix a poorly-designed mod that was broken because it depended on specific behaviour from TexTools. In other cases, you may want to merge a set of basic/"static" mods that an author has released so that you have only one mod covering all of their alternatives.

I'm going to do my best to describe the structure, but english isn't always the best language for this sort of thing, so I'll also be providing a non-functional annotated "example" and then a full example taken from one of the actual mods I personally use.

<details>
<summary>Description of the structure (to the best of my abilities)</summary>
The `Groups` field is an object, where each entry consists of the group _identifier_ for the key, and the group _definition_ (another object) for the value. Each "group" is another setting that the user can modify. They're called "groups" because they _group_ different sets of file overrides together under the choices availble.

There are two types, dropdown selections and checkboxes. The structure is the same for each, differing only in the group's `SelectionType` field; the mod page renders them slightly differently, which I'll explain shortly.

The group _identifier_ is usually just the same as the group _title_, but the two values can be different. The group _title_ is what's shown to the user, the _identifier_ just needs to be unique. Within the group _definition_ are three fields: `GroupName`, `Options`, and `SelectionType`. The `GroupName` is self-explanatory, but how it renders differs based on the `SelectionType` so I'll cover that first.

For a dropdown box, where the user _must_ select one of the options (and _only_ one) to apply, the `SelectionType` should be the string value `"Single"` - as in, "choose a single option from this list" if that helps you remember. In these cases, the options are assumed to be mutually exclusive - it may be used for cases like selecting a colour scheme (as in the real example below) or selecting a model variant. The `GroupName` is rendered as a label to the right of the dropdown box, and each _option definition_ (explained shortly!) is rendered as a single entry labelled with the `OptionName` inside the selection list.

For a checkbox, where the user can choose either _on_ or _off_, the `SelectionType` should be the string value `"Multi"` - as in, "you can choose to enable multiple options from this group" instead. In these cases, the options within the group are usually assumed to be thematically linked, such as an outfit set allowing you to turn on specific _additional_ features, or to select which pieces of the outfit are actually overridden. The `GroupName` is rendered as a text label on the top of a small thin-bordered container box holding the checkboxes, where _each_ of the option definitions is another checkbox within that container.

The option _definitions_ are each objects within the `Options` array, which is a field of the _group_ definition. To recap, a group is a group _identifier_ as the key, then an object consisting of the `GroupName` (string) field, the `SelectionType` (string) field, and the `Options` (array) field. Each entry in the `Options` array is an object consisting of the _option definition_, which itself has the `OptionName` (string) field, the `OptionDesc` (string) field, and the `OptionFiles` (object) field.

For dropdown (`"SelectionType": "Single"`) _groups_, the option definition indicates which files from the mod directory will be applied to what in-game textures and models, when the user selects that particular option from the list. For checkbox (`"SelectionType": "Multi"`) groups, the option definition indicates which files will be applied to what game objects when the user _enbles_ that particular checkbox. If the user leaves that checkbox unticked, _no_ files will be overridden in the game; checkboxes are for optional overrides, dropdowns are for mandatory ones with variants to choose from.

For the `OptionFiles` object, each entry consists of the file path _in the mod folder_ (using backslashes, which must be backslash-escaped - see below) for the key, and an _array_ of the game objects to replace as the value. Yes, even if there's only one game object being replaced, it must still be an array. Of course, if you want to apply that override to multiple game objects for this option, you can just add more game object paths. Note that the _game object paths_ use _forward_ slashes (`/`) but the _mod folder paths_ use _backslashes_ (`\`) instead - which, in JSON strings, must be _backslash-escaped_. See the real-mod example below if you're confused.
</details>
<details>
<summary>Annotated "example" (NOT A REAL ENTRY)</summary>
```json
{
	"Groups": {
		"GROUP IDENTIFIER - usually the same as the GroupName sub-field": {
			"GroupName": "GROUP TITLE - specific display depends on the group type",
			"SelectionType": "USE 'Single' FOR A DROPDOWN, 'Multi' FOR CHECKBOXES",
			Options: [
				{
					"OptionName": "OPTION NAME - will be displayed to the user"
					"OptionDesc": "additional description, may not be rendered",
					"OptionFiles": {
						"FILE PATH IN MOD FOLDER": [
							"TEXTURE/MODEL PATHS TO REPLACE",
							"There may be more than one to apply the same override to multiple targets"
						]
					},
				}
			]
		}
	}
}
```
</details>
<details>
<summary>Example from an actual mod</summary>
```json
{
	"Groups": {
		"Fur Color": {
			"GroupName": "Fur Color",
			"Options": [
				{
					"OptionDesc": "",
					"OptionFiles": {
						"Fur Color\\Red\\chara\\monster\\m8212\\obj\\body\\b0001\\texture\\v01_m8212b0001_d.tex": [
							"chara/monster/m8212/obj/body/b0001/texture/v01_m8212b0001_d.tex"
						]
					},
					"OptionName": "Red"
				},
				{
					"OptionDesc": "",
					"OptionFiles": {
						"Fur Color\\Gray\\chara\\monster\\m8212\\obj\\body\\b0001\\texture\\v01_m8212b0001_d.tex": [
							"chara/monster/m8212/obj/body/b0001/texture/v01_m8212b0001_d.tex"
						]
					},
					"OptionName": "Gray"
				},
				{
					"OptionDesc": "",
					"OptionFiles": {
						"Fur Color\\Black\\chara\\monster\\m8212\\obj\\body\\b0001\\texture\\v01_m8212b0001_d.tex": [
							"chara/monster/m8212/obj/body/b0001/texture/v01_m8212b0001_d.tex"
						]
					},
					"OptionName": "Black"
				},
				{
					"OptionDesc": "",
					"OptionFiles": {
						"Fur Color\\Snow\\chara\\monster\\m8212\\obj\\body\\b0001\\texture\\v01_m8212b0001_d.tex": [
							"chara/monster/m8212/obj/body/b0001/texture/v01_m8212b0001_d.tex"
						]
					},
					"OptionName": "Snow"
				},
				{
					"OptionDesc": "",
					"OptionFiles": {
						"Fur Color\\Champagne\\chara\\monster\\m8212\\obj\\body\\b0001\\texture\\v01_m8212b0001_d.tex": [
							"chara/monster/m8212/obj/body/b0001/texture/v01_m8212b0001_d.tex"
						]
					},
					"OptionName": "Champagne"
				},
				{
					"OptionDesc": "",
					"OptionFiles": {
						"Fur Color\\Susy\\chara\\monster\\m8212\\obj\\body\\b0001\\texture\\v01_m8212b0001_d.tex": [
							"chara/monster/m8212/obj/body/b0001/texture/v01_m8212b0001_d.tex"
						]
					},
					"OptionName": "Susy"
				}
			],
			"SelectionType": "Single"
		}
	}
}
```
</details>

Any files in the mod folder that _aren't_ listed in at least one option definition of at least one group will simply be applied directly. The path to the game object being replaced is the same as the path within the mod folder - if the file is at `a/b/c.tex` within the mod folder, it'll replace the game object at `a/b/c.tex`. Which is only an example, there isn't actually something there, so don't do that and expect results.

If you have several separate mods that an author released as variants of the same thing, you can (with some care!) merge them into one Penumbra mod with a dropdown selector for the variant you want to use. Remember to syntax-check the `meta.json` file after editing it, _before_ you tell Penumbra to rediscover mods!

<details>
<summary>Self-conflicting mods and you: what is this shit and how do I fix it?</summary>
A key difference between Penumbra and TexTools is that TT will _overwrite_ existing mod content with any content it's given _later_ - this is how people can make mods that do purely 3D edits or colourswaps without copying the entire original mod. Penumbra doesn't do that. If two mods attempt to edit the same thing, the one loaded _first_ will win. By default, that's the one higher on the list; if it's easier for you to conceptualise the later mods as the winners, you can tell Penumbra to load in reverse order instead.

For mods that just make partial edit overrides to other mods, this is easy to resolve - Penumbra will highlight conflict _losers_ in red, and will list the mods that are overriding it (and the specific files being overridden) in the mod details. Just rearrange your list until you have the partial-edit mod overriding the original one. Unfortunately, some mods are poorly designed and _rely_ on that behaviour from TexTools - they may install all of their base content and then specify that various options should replace some of the files they just installed. Penumbra doesn't work like that though, so those mods don't work properly without being restructured.

> :warning: **This is a _very_ advanced process**, because you have to define (or _re_-define) option groups _and_ rearrange the structure of the mod's content files. While I'll try to explain how to do it, you should make sure you fully understand _first_ before making any changes, and you should _always_ back up the original mod folder too,

The first step is to find which of the "static" files are being replaced by option variants. You'll want to move them to a separate subfolder in the mod, although you should keep the folder structure they're in to help you remember what they replace. Any dropdown groups are simple enough - any options that don't replace those game objects, add entries to replace them with the newly-moved files. It might not be _easy_, but it's at least simple to understand... I hope. This is a very complicated and difficult process in general, I'm doing the best I can to explain it.

Checkbox options are a little more complicated, but not by much. Basically, you need to convert them into dropdowns instead. There will be two option definitions to choose from - you can name them whatever you want, but move the old option name up to the group name, because of how the labels are handled. Once you've done that, treat it like any other dropdown with the instructions above.

The end result _should_ be that "static" replacements (ones not affected by _any_ options) are never overridden by an option, and any "dynamic" replacements (ones that depend on the user's option selections) either apply the variant or the mod's "default" (previously-static) overrides.

I did mention it was really complicated and difficult, right?
</details>

## The Mod List

In Penumbra's _root_ mod directory - the one that has all of your mod _folders_ - you'll also find a `collection.json` file. This is Penumbra's mod list, storing not just the order but also the specific settings you've selected for mods that have configuration options. This is something you'll probably _never_ need to hand-edit, but if you're a programmer, you might want to write a tool to organise or clean up your mods.

If you ever want to rename a mod folder, you'll have two options. Either just do it and Penumbra will treat it like a brand-new mod, or open your `collection.json` file, find the existing folder name (control-f is your friend!), and replace it with the new name when you rename the folder.

<details>
<summary>If you want inspiration...</summary>
My own perl script is only about 200 lines long, but it can clean mod names, rename their folders to match the name so I can find the folder for a given mod easily, update Penumbra's modlist file to point the existing mod entry to the new folder name, and even group mods _in_ the mod list (changing their order) to put mods together by categories. I use things like `Gear`, `Minion`, `Mount`, and `Ui` as prefixes on the mod names to group them, and my sorter will move them all together in Penumbra's mod list. It's just a JSON array of mod definition objects listing the folder name, whether the mod is enabled, the mod priority (which will probably be deprecated/removed soon, just a heads up!), and the settings you've chosen if the mod has configuration. Run it through a JSON formatter and take a look, you can probably come up with something neat.
</details>



[Plugins and Mods]: </plugins-and-mods.md>
[advanced metadata]: <#advanced-metadata>
[modlist JSON]: <#the-mod-list>
