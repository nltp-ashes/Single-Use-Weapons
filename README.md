# Single Use Weapons [![License](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

[![Latest Stable Build](https://img.shields.io/github/v/release/nltp-ashes/Single-Use-Weapons?label=Latest%20Stable%20Build&color=brightgreen)](https://github.com/nltp-ashes/Single-Use-Weapons/releases/latest) [![Latest Test Build](https://img.shields.io/github/v/release/nltp-ashes/Single-Use-Weapons?include_prereleases&filter=*rc*&display_name=tag&label=Latest%20Test%20Build&color=yellow)]() [![Total Downloads](https://img.shields.io/github/downloads/nltp-ashes/Single-Use-Weapons/total.svg?label=Downloads%20(All%20Time))](https://github.com/nltp-ashes/Single-Use-Weapons/releases) [![Latest Release Downloads](https://img.shields.io/github/downloads/nltp-ashes/Single-Use-Weapons/latest/total.svg?label=Downloads%20(Latest%20Release))](https://github.com/nltp-ashes/Single-Use-Weapons/releases/latest)

---

Utility mod for disposable weapons, such as single shot rocket launchers.

---

### ABOUT

This addon does nothing on its own : it allows other addons to make their weapons single use, through a few config keys.

Single use weapons :
- Come loaded, and can't be unloaded or reloaded
- Once fired, play a discard animation (or get holstered), then disappear from the player's inventory
- Can optionally drop a spent model on the ground, which can't be picked up
- Only the last 10 spent models are kept in the world, older ones are removed

**Note :** Only weapons fired by the player are discarded. A spent weapon looted from an NPC gets discarded as soon as the player draws it.

---

### USAGE

To make a weapon single use :
1. In the weapon section, add `single_use = true`;
2. Set the weapon's `ammo_class` to a dedicated ammo section defining `fake_ammo = true`, which prevents the weapon from being unloaded or reloaded;
3. *(Optional)* In the weapon's HUD section, add a `anm_discard` animation, played after firing. Without it, the weapon is holstered instead;
4. *(Optional)* In the weapon section, add a `snd_discard` sound, played along with the discard animation;
5. *(Optional)* In the weapon section, add a `discard_object` section, inheriting from `physic_object`, with the `visual` to drop on the ground.

Example :
```ini
[wpn_my_launcher]:<...>
single_use          = true
ammo_class          = ammo_my_launcher
snd_discard         = weapons\my_launcher\discard
discard_object      = wpn_my_launcher_discarded

[wpn_my_launcher_hud]:hud_base
anm_discard         = my_launcher_discard_hands, my_launcher_discard

[ammo_my_launcher]:ammo_base
fake_ammo           = true

[wpn_my_launcher_discarded]:physic_object
visual              = dynamics\weapons\wpn_my_launcher\wpn_my_launcher_spent
```

**Important :** The ammo section is only meant to exist inside the weapon, don't add it to trade or loot lists.

---

### REQUIREMENTS

These addons are **absolutely required** in order for the addon to work :
1. [S.T.A.L.K.E.R. Anomaly 1.5.3](https://www.moddb.com/mods/stalker-anomaly/downloads/stalker-anomaly-153).
2. [S.T.A.L.K.E.R. Anomaly Modded Exes 12.09.2026 (or newer)](https://github.com/themrdemonized/xray-monolith)

---

### INSTALLATION

To **install** the addon :
1. Download and install the requirements;
2. Download this addon;
3. Using MO2, click the "Install a mod from an archive" button;
4. Follow the instructions.

To **update** the addon :
1. In MO2, disable and delete the previous version of the addon;
2. Make sure to update the requirements;
3. Make sure to check the changelog for extra steps;
4. Follow the installation instructions.

To **uninstall** the addon :
1. Close your game, disable and delete the addon from MO2.

---

### CHANGELOG

You can check out the changelog of the last update in the [CHANGELOG.md](CHANGELOG.md) file.

For past updates, please refer to the description of each release, in the [releases tab](https://github.com/nltp-ashes/Single-Use-Weapons/releases).

---

### FUTURE WORKS & KNOWN ISSUES

You can find a list of features planned as well as known issues [here](https://github.com/nltp-ashes/Single-Use-Weapons/issues).

If you believe you have found a bug in the addon, please open an issue [on the addon's GitHub page](https://github.com/nltp-ashes/Single-Use-Weapons/issues/new).

---

### SUPPORT & SUGGESTIONS

If you need help with anything, or if you have any suggestions, you can :
- ✅ Message me on [ModDB](https://www.moddb.com/members/nltp-ashes);
- ✅ Message me on Discord : @nltp_ashes (formerly NLTP_ASHES#0117);
- ✅ Message me on my [Discord](https://discord.gg/7Z8S2qg) server;

---

### SPECIAL THANKS & CREDITS

Special thanks to these people for their help in the making of this addon :

|   Name   |                                                                         Motive                                                                          |
|:--------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------:|
| **Kute** | For [Item Model Drop After Usage](https://www.moddb.com/mods/stalker-anomaly/addons/items-model-drop-after-usage), which inspired dropping spent models |

---

### LICENSE

Everything contained in Single Use Weapons and made by me, NLTP_ASHES, is licensed under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).

This means you're allowed to redistribute and/or adapt the work, as long as you respect the following criteria :
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
- **NonCommercial** — You may not use the material for commercial purposes (this includes donations).
- **ShareAlike** — If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
