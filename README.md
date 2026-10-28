# NBA 2K14 (PS4) - Ultrawide 3440x1440 Runtime Patch

Renders the game at 3440x1440 (21:9) instead of 1920x1080, for the
[NBA2K14-PS4-Runtime](https://gitlab.com/sexcurrybeats/NBA2K14-PS4-Runtime)
shadPS4-based launcher.

This is **experimental**. The game was built for a fixed 16:9 aspect ratio.
The 3D camera/court render correctly fills the wider frame, but the
HUD/menus were not designed for 21:9 and may not adapt - test before relying
on it. If you hit layout issues in menus or the HUD, that's a known
limitation of this patch, not a bug report I can fix without further
reverse-engineering of the executable.

## Credits

The patch points (byte-search masks) are taken directly from the `Native
1440p` mod by **PeacemanNOT**, part of the NBA2K14-PS4-Runtime project. This
mod only changes the *replacement value* for width from 2560 to 3440,
keeping the same search patterns and height value. All credit for locating
the original resolution-setting code goes to PeacemanNOT.

## Requirements

- NBA 2K14 PS4, title ID `CUSA00007` or `CUSA00104`, version 01.00
- [NBA2K14-PS4-Runtime](https://gitlab.com/sexcurrybeats/NBA2K14-PS4-Runtime) v1.2 or later
- Your own legally-dumped game files. No game files, PKGs, or proprietary
  PlayStation modules are distributed here - only the patch.

## Install

1. Copy the `Ultrawide 3440x1440` folder (containing both files from this
   repo) into your `<game-directory>-mods` folder, e.g.:
   ```
   games/
     CUSA00007/
     CUSA00007-mods/
       Ultrawide 3440x1440/
         Ultrawide 3440x1440.xml
         settings.json
   ```
2. In the launcher's **Mods & Assets** dialog, enable the mod (or add
   `Ultrawide 3440x1440` to `load order.txt` manually).
3. Do not run this alongside the stock `Native 1440p` mod - both patch the
   same addresses, so only one can be active at a time.

## What it changes

- Patches the game's hardcoded 1920x1080 render target to 3440x1440
  (width changed from the `Native 1440p` mod's 2560 to 3440; height stays
  at 1440).
- `settings.json` raises `General.extra_dmem_in_mbytes` to 768 to cover the
  larger framebuffer (scaled up from the 1440p mod's 512).

## License

GPL-2.0-or-later, consistent with the NBA2K14-PS4-Runtime project this is
built on. See `LICENSE`.
