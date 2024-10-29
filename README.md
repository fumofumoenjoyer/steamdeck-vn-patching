# steamdeck-vn-patching



I don't think HOWTOs for absolute (Linux) newbies exist, yet.
Patches

  -For patches for which installation consists in copying a few files to the game directory, you can do that in desktop mode as usual.

  -For patches which ship as an exe, you can check if that can be opened as an archive, e.g. in 7-Zip. A lot of these are exes just self-extracting archives, so once you've gotten the payload data out, you can just proceed as above.

  -For patches that actually require running the exe, the easiest way is probably to install the Flatpak version of protontricks from Discover, that should have the option to run an arbitrary exe within the main game's "prefix" (= fake Windows installation), which is what you want.

  -If all else fails, patching the game on a Windows PC and overwriting the game directory on the Deck with the one from the PC usually works.

Non-Steam games

You can add non-Steam games to Steam as usual on the Deck, only you have to do it in desktop mode because of UI limitations in game mode. If you have the game in some ready-to-play format, e.g. a self-contained game directory, all you have to do is add the exe as a non-Steam game. You may have to fiddle with the extension filter drop-down to get it to show. Then check the game properties and make sure that the path to the exe and the game directory are set correctly. That done, force-enable Proton under compatibility.

If the game needs installation, you can add the installer as a non-Steam game as above, run that. Ideally install to a suitable destination in /home/deck/, not into the "prefix" (or do, and move it out after). Once the game is installed go into the properties and change the paths to point to your installation directory and installed game exe.

 

Often, this will just work. Other times, it will not, and then it gets complicated, especially if you don't know what you're doing. Don't hesitate to ask.

Proton

Proton is the name of Valve's version of WINE. Both are used to run Windows software on Linux. Valve keep old versions around, because new ones are not always strictly better, they can just as well break games that used to work fine. There are also third-party Proton versions, like Proton GE, which have cutting edge versions and/or components that Valve can't easily ship for legal reasons. I'd try, in order 7.0 [latest official stable] → Experimental → GE→ 5.0 → 4.11 → the rest from the top.

 The docs say "to run an executable for a Proton app, select Protontricks Launcher when opening a Windows executable (eg. EXE) in a file manager", though it's possible Flatpak interferes with that.

Alternatively, open a terminal (command prompt) in the game's directory. The easiest way is probably to Manage → Browse local files in Steam (desktop mode), then right-click and it should have a terminal option. Or you can just launch Konsole (the KDE terminal) and cd there. Anyway, when there, run run protontricks -c <COMMAND> <APPID>, where <COMMAND> is the patch exe and <APPID> is the game's Steam app ID. 



Assuming the patch exe is called "Patch.exe" and is in the same directory as the game, executing protontricks -c "Patch.exe" 1234567 in that directory should do it, the number being the game's Steam ID. It's in the URL of the Steam store page, for example, and if you just launch protontricks it will give you a list of installed Proton games and their IDs.

Caveat: protontricks only works after you've launched (or tried to) the game at least once, as that will create the Proton prefix for it.
