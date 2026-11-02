# Deadlock-but-x10andItem-Server
Host a Deadlock Combo (x10 + Item2) server on your own PC and play with friends over Steam
(no port forwarding). x10: every skill upgrade is 10x stronger, 3 s respawn, hero rules, CC
protection. Item2: the Broker is back (free deals, Legendaries, rerolls) and 11 custom items
(five Legendary ones, six sold in the normal shop).

You need: Windows 10/11, Deadlock (Steam), .NET Runtime 10 (x64), and Deadworks (setup
downloads the latest release from GitHub; if that fails, download deadworks-vX.X.X.zip yourself
from https://github.com/Deadworks-net/deadworks/releases and put it in this folder).

Install (once): unzip anywhere, close Deadlock, double-click setup_server.bat. It finds Deadlock,
installs Deadworks, the two Combo plugins, the mod file (unless Deadlock Mod Manager already has
it) and two lines in gameinfo.gi so friends can join over Steam. Plugins of the single mods are
moved to plugins_disabled. Remove old x10 / Item2 mod files (pak90, pak93, pak94, pak95) from addons.

Start: double-click start_combo_server.bat, wait for the map to load. You: F7 in game, type
connect localhost:27016. Friends: type status in the SERVER window, copy the steamid, they type
connect [A:1:...] (the steamid changes every start). Everyone should install the same Combo mod
version (pak96_dir.vpk) to see the Broker's window and the new items' icons and texts.

HOW A FRIEND (PLAYER) JOINS
Only once:
1. Install the Combo mod (one file): with Deadlock Mod Manager, or put pak96_dir.vpk (inside Deadlock_Combo.zip) in
   Deadlock\game\citadel\addons  (usually C:\Program Files (x86)\Steam\steamapps\common\Deadlock\game\citadel\addons;
   make the addons folder if it isn't there). Remove old x10 / Item2 mod files (pak90, pak93, pak94, pak95): Combo has them
   already and the values would stack. It must be the same version the host uses (ask the host).
2. Start Deadlock from Steam as usual. You don't need Deadworks or .NET and no ports to open: that's only for the host.
3. Settings -> enable "Dev command console".
Every time:
1. The host starts the server first and waits until it has loaded the map.
2. Get the host's current steamid, e.g. [A:1:1234567890:12345] (with the square brackets). It stays valid until the host
   closes the server; a restarted server has a new one.
3. In the main menu or your Hideout press F7 (console).
4. Type   connect [A:1:1234567890:12345]   (the host's steamid; paste it) and press Enter.
5. Wait for the map, then pick a team and a hero as usual (switch team later: changeteam 0 in the console).
6. Leave the server: F7, then  disconnect
Can't join? The steamid may have changed (ask again, and check the server window is still open); check both brackets and no extra
spaces (paste it instead of typing); if you join but see no Broker window, icons or texts of the new items, you don't have the
same Combo mod version as the host (you can still play: use the chat commands); after a Deadlock update wait until the host
has updated the kit.

The Broker: free deals at 10:00, 20:00 ... and Legendaries at 15:00, 30:00 ... for 2.5 min. Stand
at a shop, press R. Rerolls: 5,000 souls (deal) / 10,000 (Legendary), doubling each time.

Settings: Deadlock\game\bin\win64\configs\ComboX10Rules\ComboX10Rules.jsonc and
ComboItem2Broker\ComboItem2Broker.jsonc, then type dw_reloadconfig in the server window. The test
commands (/broker, /giveitem ...) are off; set "AllowBrokerCommand": true to use them.

The log (combo_item2.log) is quiet by default so the server stays fast; set "VerboseLog": true in
ComboItem2Broker.jsonc only when you debug. Pausing the game (P) is meant to pause the Broker's timers,
the items' timers and the CC protection (the plugin reads the game's pause flag; see "pause flag" in the log).

After a game update: run setup_server.bat again and update the Combo mod. Deadworks may need a
moment to support a new game version.
