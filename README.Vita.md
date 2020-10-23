## Building the Vita port
### Requirements
* VitaSDK installed and in PATH;
* libFLAC (run `vdpm flac` to install it if it's not present by default);

The required fork of [libvita2d](https://github.com/frangarcj/vita2dlib/tree/fbo) and
[vita-shader-collection](https://github.com/frangarcj/vita-shader-collection) are now
present in this repository. You don't need to install them manually.

### Build instructions
Run `make -f Makefile.vita`. This should produce a VPK.

## Using the Vita port
### Installation
1. Install VPK.
2. Extract `data.zip` from the latest release to root of memory card (`ux0:`).
3. Copy any supported IWADs (see below) you have to `ux0:/data/chocolate/iwads/`.

### Launcher controls
* LTrigger/RTrigger: select tab
* Up/Down: select option
* Left/Right: adjust option
* Cross: activate option
* Start: save settings and launch the game you have selected in the `Game` tab (in single-player mode)
* Circle: save settings and exit launcher / cancel selection when in file select dialog

Controls for a particular game can be viewed and changed in the `Buttons` and `Input` tabs.

### Supported games / IWADs
To play a game from this list, copy the corresponding files to `ux0:/data/chocolate/iwads/`.

| Game                                   | File(s)        |
|----------------------------------------|----------------|
| Shareware Doom *                       | `doom1.wad`    |
| Doom / Ultimate Doom                   | `doom.wad`     |
| Doom II                                | `doom2.wad`    |
| Final Doom: TNT Evilution              | `tnt.wad`      |
| Final Doom: The Plutonia Experiment    | `plutonia.wad` |
| Chex Quest                             | `chex.wad`, [`chex.deh`](https://www.doomworld.com/idgames/?file=utils/exe_edit/patches/chexdeh.zip) |
| [FreeDoom](https://freedoom.github.io/): Phase 1                      | `freedoom.wad` |
| FreeDoom: Phase 2                      | `freedoom2.wad`|
| FreeDM                                 | `freedm.wad`   |
| Shareware Heretic *                    | `heretic1.wad` |
| Heretic / Shadow of the Serpent Riders | `heretic.wad`  |
| Hexen                                  | `hexen.wad`    |
| Strife                                 | `strife1.wad`, optionally `voices.wad`   |

\* included in `data.zip` for the latest Vita release

### Loading PWADs (and other custom game files)
Put all custom files for a given game into `ux0:/data/chocolate/pwads/<gamedir>`, where `<gamedir>` is `doom` for all Doom games, `heretic` for Heretic and Shareware Heretic, `hexen` for Hexen and `strife` for Strife, then use the `Custom` tab in the launcher to select any custom content you want.

### Recording demos
When `Record demo` is set to `On`, the demo is saved to `ux0:/data/chocolate/tmp/mydemo.lmp`.

### Notes
If the game closes without producing a crash dump or an error message, a file named `ux0:/data/chocolate/i_error.log` should be generated, which contains error messages.

The IP address that appears in the `Game address` field of the `Net` tab of the launcher when you run it is your Vita's LAN IP. You can use this if autojoin doesn't work properly.

To join a game by IP, select `Game address`, enter the address, then hit `Connect to address`.

Netgames will only work correctly if all players have selected the same game and set of custom files (stuff in the `Files` tab). PWAD order does matter. The game will complain upon connecting if you did something wrong.

The `Merge file` option is the launcher version of the `-merge` command line option. See the Chocolate Doom wiki for more details.

You can specify custom command line parameters in a [response file](https://doomwiki.org/wiki/Parameter#.40), then load it using the `Override response file` option. Don't forget to select the correct game.

By popular request some of the static render limits (`MAXVISPLANES`, `MAXVISSPRITES`, `MAXDRAWSEGS`) have been quadrupled in this fork to accomodate for SIGIL.

## Credits
- [these people](https://github.com/chocolate-doom/chocolate-doom/blob/master/AUTHORS) for Chocolate Doom itself;
- Vita SDK Team for the Vita SDK;
- rsn8887 and cpasjuste for the SDL2 port;
- rsn8887 for the SDL_net port, some graphics-related code and testing;
- frangarcj for Vita Shader Collection and the FBO fork of Vita2D;
- tiduscrying for the LiveArea assets;
- KINGGOLDrus for some launcher graphics;
- everyone on the #henkaku and #vitasdk IRC channels for help and/or testing.
