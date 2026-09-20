A guide on how to **download** and **install addons** in [World of Warcraft](https://worldofwarcraft.blizzard.com/) on Windows and macOS.

World of Warcraft calls them addons rather than mods, and they are one of the few cases in these guides where the game was built to accept them. Blizzard ships an addon API, an addon management screen at character select, and a published policy covering what addons may and may not do. There is no mod loader, no injector and nothing to patch. You drop a folder in the right place and the game loads it.

Our example is [Details! Damage Meter](https://www.curseforge.com/wow/addons/details), which at over 367 million downloads is one of the most installed addons in the game's history.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-addons-in-world-of-warcraft/)

## Table Of Contents
* [Requirements](#requirements)
* [How WoW Addons Work](#how-wow-addons-work)
    * [Flavors](#flavors)
    * [Where Addons Live](#where-addons-live)
* [Installing With The CurseForge App](#installing-with-the-curseforge-app)
* [Installing With WowUp](#installing-with-wowup)
* [Installing With The Wago App](#installing-with-the-wago-app)
* [Installing Manually](#installing-manually)
* [The TMC App](#the-tmc-app)
* [Enabling Addons In-Game](#enabling-addons-in-game)
* [Settings And Saved Data](#settings-and-saved-data)
* [Keeping Addons Working After A Patch](#keeping-addons-working-after-a-patch)
* [Uninstalling](#uninstalling)
* [Troubleshooting](#troubleshooting)
* [Conclusion](#conclusion)
* [See Also](#see-also)

## Requirements
* A PC running **Windows 10** or later, or a **Mac**. Both are fully supported, and everything in this guide works on either.
* **World of Warcraft** installed through the Battle.net launcher.
* Very little disk space. Addons are Lua and XML text files plus the occasional texture, so even a large collection is small.
* A file extractor if you install manually. Windows and macOS both handle `.zip` natively.

Addons are officially sanctioned. Blizzard publishes a UI Add-On Development Policy setting out the rules, and there is no ban risk in using addons that follow it. What is not allowed is automation that plays the game for you, and no addon from CurseForge or Wago is going to be doing that.

## How WoW Addons Work
An addon is a folder of Lua scripts, XML layout files and a `.toc` manifest. WoW scans a specific folder at launch, reads each `.toc`, and loads what it finds.

There is no framework to install underneath. Nothing to hook the game, nothing to inject, nothing that runs outside of WoW's own scripting sandbox.

### Flavors
This is the part that catches people, because WoW is not one game any more.

Retail and each Classic line run separate clients, with separate addon folders and separate addon builds. A CurseForge addon page lists which **flavors** it supports, and Details! currently covers:

| Flavor | What it is |
| ------ | ---------- |
| Retail | The current expansion, on the 12.x client |
| Classic | Classic Era |
| Classic TBC | The Burning Crusade Classic |
| MoP Classic | Mists of Pandaria Classic |
| Titan Reforged Classic | The newer Classic line |

Downloading the wrong flavor gives you an addon that either does not appear at all or appears greyed out as out of date. Addon managers pick the right one for you based on which install you point them at, which is one of the better reasons to use one.

### Where Addons Live
Each flavor has its own folder inside your WoW install. On Windows, Retail is here:

```
C:\Program Files (x86)\World of Warcraft\_retail_\Interface\AddOns
```

On macOS:

```
/Applications/World of Warcraft/_retail_/Interface/AddOns
```

The other flavors use the same layout with a different folder name, such as `_classic_era_` or `_classic_`. There is also `_ptr_` if you have the public test realm installed.

Every addon is one folder directly inside `AddOns`, named the same as the addon. Details! installs as a folder called `Details`.

**NOTE** - If the `AddOns` folder does not exist yet, create it. It is only made once something needs it.

## Installing With The CurseForge App
The most common option, and the one CurseForge addon pages assume.

1. Download the [CurseForge app](https://www.curseforge.com/download/app). There is a lightweight standalone build and an Overwolf build with in-game features; either works, and the standalone one is the lighter choice. Windows, macOS and Linux builds are all available.
2. Open it and let it detect your WoW installations. It finds each flavor separately.
3. Open the **World of Warcraft** section and pick the flavor you want to add addons to.
4. Search for **Details! Damage Meter** and click **Install**.
5. The app downloads the correct build for that flavor and drops it in the right `AddOns` folder.

The app also handles updates, which is the real reason to use it. WoW addons break with every content patch and being able to update thirty of them at once matters more here than in most games.

## Installing With WowUp
[WowUp](https://wowup.io/) is a free, open source, community-built addon manager with Windows, macOS and Linux builds. It can pull from multiple addon sites rather than just one, which is useful because not every addon is on CurseForge.

1. Download WowUp from [wowup.io](https://wowup.io/).
2. On first launch it scans for WoW installs and lists each flavor it finds.
3. Open **Get Addons**, search for **Details! Damage Meter** and install it.
4. Use **My Addons** to see what you have and update it.

WowUp can also adopt addons you installed by hand, matching them up to their source so that they start getting updates. If you have a folder full of manually installed addons from years ago, pointing WowUp at it is a quick way to bring the whole lot back under management.

## Installing With The Wago App
[Wago Addons](https://addons.wago.io/) is the other major addon host, and the same people run [wago.io](https://wago.io/) for WeakAuras and other import strings. The [Wago App](https://addons.wago.io/app) manages addons from their catalogue.

1. Download the app from [addons.wago.io/app](https://addons.wago.io/app).
2. Let it find your WoW installations.
3. Browse or search, and install.

The Wago App's real advantage is the rest of the Wago ecosystem. If you are already importing WeakAuras strings or UI packs from there, having one app that handles the addons alongside them is convenient.

**TIP** - Do not run two addon managers against the same install if you can avoid it. They will both try to own the same folders and you will get duplicate or half-updated addons. Pick one.

## Installing Manually
Worth knowing, and genuinely easy in WoW.

1. Go to the [Details! Damage Meter page](https://www.curseforge.com/wow/addons/details) on CurseForge.
2. Under **Files**, pick the file matching your flavor. For the current expansion that is the Retail build.
3. Download the `.zip`.
4. Extract it.
5. Copy the extracted folder, `Details`, into your `Interface\AddOns` folder.
6. Restart WoW if it is running.

The result should be:

```
World of Warcraft\_retail_\Interface\AddOns\Details\
```

with the addon's `.toc` file and its Lua files inside.

**WARNING** - The addon folder goes directly in `AddOns`, and the folder name has to match what the addon expects. A nested `AddOns\Details-v1.2.3\Details\` will not load, and neither will loose Lua files sitting in `AddOns` on their own. Some addons also ship several folders in one zip, for example a main addon plus a library, and all of them go into `AddOns` side by side.

## The TMC App
The last option is our own, with the caveat that WoW is already the best-served game in this guide series when it comes to managers. [The TMC App](https://moddingcommunity.com/tmc-app) does one-click installs, **sandboxes** (named mod profiles per game with their own deployment method), a server browser with live latency graphs, and RCON.

**World of Warcraft is not in its supported games list.** Between the CurseForge app, WowUp and the Wago App, addon management is a solved problem here, so this one sits lower on our list than games with no decent tooling at all. We would rather say that than pad the list.

**The app is also in very early development.** Its README calls it partially tested and that is a fair description. If you use it for other games and would like WoW support, saying so is the fastest way to move it up the queue.

It is **open source** under GPL-3.0 at [github.com/modcommunity/tmc-app](https://github.com/modcommunity/tmc-app). Bugs, feature requests and "please support this game" all belong in [the issue tracker](https://github.com/modcommunity/tmc-app/issues), pull requests are welcome, and adding a game turns out to be four JSON files rather than any code, so contributing WoW support is well within reach.

Installing it:

* **Linux**: one line, no root and no package manager.

```bash
curl -fsSL https://raw.githubusercontent.com/modcommunity/tmc-app/main/scripts/install.sh | sh
```

* **Windows**: the `setup.exe` or `setup.msi` from the [releases page](https://github.com/modcommunity/tmc-app/releases). There is a portable build too, though it does not register the launcher entry or the `tmc://` link handler.
* **macOS**: the `.dmg` from the same releases page.

## Enabling Addons In-Game
Installing is not quite the whole job.

1. Start WoW and go to the character select screen.
2. Click **AddOns** in the bottom left.
3. Make sure your addons are ticked.
4. Enter the world.

New addons are usually enabled by default, but it is the first thing to check when something you just installed is not showing up.

The addon list is per character by default, with an **All** dropdown to apply your selection everywhere. That is useful when you want a damage meter on your raiding character and not on your bank alt.

Once in-game, `/reload` reloads the interface without logging out, which picks up changes to addon files. Some addons also register their own slash command, and Details! uses `/details`.

## Settings And Saved Data
Addon settings are not stored with the addon. They live in the `WTF` folder alongside the rest of your interface configuration:

```
World of Warcraft\_retail_\WTF\Account\<ACCOUNT>\SavedVariables
```

with per-character data under the realm and character folders below that.

This has two useful consequences. Updating or reinstalling an addon does not lose your configuration, since the config is in a different place entirely. And backing up your `WTF` folder backs up your whole UI setup, which is well worth doing before a big patch.

## Keeping Addons Working After A Patch
Every WoW content patch bumps the interface version, and every addon whose `.toc` still names the old one gets flagged as out of date and disabled.

When that happens:

1. **Update your addons first.** Most authors push a compatible build within hours of a patch, and an addon manager gets you there in one click.
2. **If an addon has not been updated**, you can tick **Load out of date AddOns** on the character select AddOns screen. Often it works fine, since the interface version is only a declaration. Sometimes it errors constantly, in which case disable it and wait.
3. **Major expansion patches break more.** Expect a few days of addons catching up rather than a few hours.

**TIP** - If your UI comes up broken after a patch, the quickest diagnosis is to disable everything, confirm the default UI is fine, and re-enable in batches.

## Uninstalling
Through a manager, uninstall it from the addon list and the folder is removed.

By hand, delete the addon's folder from `Interface\AddOns`.

Either way, the addon's saved variables stay behind in `WTF`. That is deliberate, so that reinstalling brings your settings back. If you want a genuinely clean slate, delete the matching `.lua` file from the `SavedVariables` folder as well.

## Troubleshooting
**The addon does not appear in the AddOns list.** The folder structure is wrong. Check for a nested folder, so `AddOns\Details\Details.toc` rather than `AddOns\Details-12.1\Details\Details.toc`.

**It is listed but greyed out.** It is disabled, or flagged out of date. Tick it, and tick **Load out of date AddOns** if you need to.

**Installed to the wrong flavor.** Very common. Make sure your manager is pointed at `_retail_` and not at a Classic install, or the other way round.

**Lua errors everywhere after a patch.** Update your addons. If one refuses to behave, disable it and check its CurseForge page for a compatible build.

**The addon loads but its window is gone.** Many addons have a lock or hide toggle, and some remember a position off-screen. Check the addon's own options first; `/details` for Details!. As a last resort, delete its saved variables file to reset it.

**Two managers keep fighting.** They are both managing the same folder. Pick one and uninstall the other.

**Blizzard's own UI settings reset.** Check whether you deleted or moved anything from `WTF`. That folder holds Blizzard's settings as well as addon data.

## Conclusion
WoW addons are the easiest install in this whole set of guides. There is no loader, the game has a management screen built in, and a manager like the CurseForge app or WowUp reduces the whole thing to searching and clicking install.

The two things that actually cause problems are flavors and patches. Make sure you are installing for the right client, and expect to spend a few minutes updating addons after every content patch.

For the games that are less well served than this one, the [TMC App](https://github.com/modcommunity/tmc-app) is ours. It is open source, early in development, and feedback on it is appreciated.

## See Also
* [World of Warcraft addons on CurseForge](https://www.curseforge.com/wow/addons)
* [Wago Addons](https://addons.wago.io/)
* [WowUp](https://wowup.io/)
* [Details! Damage Meter source on GitHub](https://github.com/Tercioo/Details-Damage-Meter)
* [Official World of Warcraft Discord](https://discord.com/invite/wow)
* [TMC App](https://github.com/modcommunity/tmc-app)

We keep this guide as current as we can, but WoW patches and addon managers both move. If an instruction here no longer matches what you are seeing, please report it or open a [pull request](https://github.com/modcommunity/how-to-install-mods-in-world-of-warcraft/pulls) on this guide's GitHub repository.

Join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or want help with anything modding related!
