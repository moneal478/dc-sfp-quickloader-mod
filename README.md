# Data Center SFP Quick Load

Data Center SFP Quick Load is an unofficial MelonLoader mod for the Steam game
**Data Center**. It moves compatible SFP/QSFP modules from the box in your hand
into compatible empty ports on the switch you are looking at.

## Preview status

The current public build is **v0.1.4-preview.1** (assembly version `0.1.4`). Core
quick loading has been validated with standard SFP, 25G, and 40G/QSFP modules
on purchased switches, routers, and firewalls.

Three preview limitations remain:

- The normal bottom-bar `Quick Load SFPs` key hint does not appear. The
  configured key still works, and result messages/logging are available.
- Performance while holding a module box still needs broader in-game
  confirmation.
- Customer and DMZ switch panels built into the map are not targeted correctly
  by v0.1.4. Upgrade to v0.1.5-preview.1 for that repair.

## Features

- Loads every compatible module it can from the held box with one key press.
- Supports aiming at a switch body or one of its individual ports.
- Leaves occupied ports unchanged.
- Leaves incompatible or excess modules in the box.
- Keeps the game's normal `E` interaction available by using `F` by default.
- Lets you change the activation key in a small text configuration file.

## Requirements and tested environment

- The Steam version of **Data Center** (app `4170200`).
- MelonLoader configured for the game's .NET 6 IL2CPP runtime.
- A keyboard; controller and mouse bindings are not currently supported.

The preview was tested with Data Center build `24198836`, Unity
`6000.4.12f1`, MelonLoader `0.7.3 Open-Beta`, .NET `6.0.36`, and Proton `11.0`.
Other environments may work but have not been verified yet. Game updates can
require an updated mod release.

This mod is not affiliated with Waseku, Data Center, Steam, or MelonLoader.

## Install

1. Fully quit Data Center.
2. Install MelonLoader for Data Center if it is not already installed, launch
   the game once, and quit again.
3. Download
   [`DataCenterSfpQuickLoad-v0.1.4-preview.1.zip`](releases/v0.1.4-preview.1/DataCenterSfpQuickLoad-v0.1.4-preview.1.zip).
4. In Steam, open **Data Center > Manage > Browse local files**.
5. If the opened Data Center installation folder does not contain a `Mods`
   folder, create a new folder there and name it exactly `Mods` with a capital
   `M`. It must be directly inside the Data Center installation folder, beside
   `Data Center.exe` and the `MelonLoader` folder—not inside `MelonLoader`.
   If the `MelonLoader` folder is also missing, install MelonLoader and launch
   the game once before continuing.
6. Extract these two files from the ZIP directly into `Mods`:

   ```text
   DataCenterSfpQuickLoad.dll
   DataCenterSfpQuickLoad.deps.json
   ```

7. Start Data Center. `MelonLoader/Latest.log` should contain both the mod name
   and `Data Center SFP Quick Load loaded.`

The ZIP checksum is published beside it in
[`SHA256SUMS`](releases/v0.1.4-preview.1/SHA256SUMS), and hashes for the two
extracted files are in
[`CONTENTS_SHA256SUMS`](releases/v0.1.4-preview.1/CONTENTS_SHA256SUMS).

## Use

1. Pick up a non-empty box of 1G, 10G, 25G, or 40G modules.
2. Stand near the destination device and center your view on the switch body or
   one of its SFP/QSFP ports.
3. Press `F` once, or the key configured in
   `UserData/DataCenterSfpQuickLoad.cfg`.

The mod fills compatible empty ports across the focused parent device, not only
the single aimed-at port. It loads as many modules as the device can accept.
There is no confirmation prompt, selective-port mode, or undo command.

### Compatibility behavior

- 1G, 10G, and 25G modules use the game's standard class-0 SFP ports.
- 40G/QSFP modules use class-1 QSFP ports.
- Occupied ports are skipped.
- Incompatible and excess modules remain in the held box.

These rules mirror the game's current in-game compatibility behavior.

## Configuration

The first launch creates this file relative to the Data Center installation:

```text
UserData/DataCenterSfpQuickLoad.cfg
```

Its default content is:

```text
ActivationKey=F
```

Set `ActivationKey` to a Unity Input System keyboard key name such as `G`, `V`,
`Space`, `Digit1`, or `LeftShift`, then restart the game. Invalid values fall
back to `F` and produce a warning in `MelonLoader/Latest.log`. Key conflicts are
not detected automatically.

## Upgrade

1. Fully quit Data Center.
2. Replace both mod files in `Mods` with the files from the new package.
3. Remove stale renamed or duplicate copies of the DLL.
4. Restart the game and verify the version in `MelonLoader/Latest.log`.

Your configuration file remains in `UserData` during an upgrade.

## Uninstall

Fully quit the game and remove these files from `Mods`:

```text
DataCenterSfpQuickLoad.dll
DataCenterSfpQuickLoad.deps.json
```

Optionally remove `UserData/DataCenterSfpQuickLoad.cfg` to delete the saved key
setting, then restart the game.

## Troubleshooting

### The mod does not load

- Confirm both files are directly inside `Data Center/Mods`.
- If `Mods` is missing, fully quit the game and create it directly inside the
  Data Center installation folder. Name it exactly `Mods`; do not create it
  inside `MelonLoader` or leave the files inside the downloaded ZIP.
- Confirm MelonLoader itself starts and uses its .NET 6 runtime.
- Remove duplicate or renamed copies of the mod.
- Search `Data Center/MelonLoader/Latest.log` for `Data Center SFP Quick Load`.

### Pressing the key does nothing

- Confirm you are holding a non-empty SFP/QSFP module box.
- Aim near the center of a switch body or one of its ports and stand within
  roughly six metres.
- Confirm the configured key and restart after changing it.
- Remember that the bottom-bar key hint is absent in this preview.
- Built-in customer and DMZ panels require v0.1.5-preview.1 or newer.

### No compatible open ports are found

The target may be full or may expose the wrong port class for the held modules.
The mod writes a `Quick-load diagnostics` line to `MelonLoader/Latest.log` with
the detected module types, ports, and compatibility counts.

When reporting a problem, include that diagnostic line, the mod version, the
Data Center build, and the MelonLoader version. Do not post the entire log until
you have checked it for unrelated personal information.

## Changelog and support

See [CHANGELOG.md](CHANGELOG.md) for release notes. Use the repository's GitHub
Issues page for reproducible problems and include the diagnostic details listed
above.
