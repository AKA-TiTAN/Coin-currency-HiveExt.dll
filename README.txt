http://epochmod.com/forum/index.php?/topic/15309-custom-hiveextdll-release/

https://www.youtube.com/watch?v=-T8xWj02MkM


Coin Currency Modded hiveExt.dll for DayZ Epoch 1.0.5 by TiTAN
========================================================

Installation instructions
=========================

Pre-requirements: a PBO manager and basic knowledge of ArmA script editing

Please Test before you commit to a live Server!

Alternatively If you are running a standard Overpoch server (you will still need @DayzOverpoch and the Key File if you have'nt already got it)
You can Just Replace your server's @DayZ_Epoch_server file, and replace your DayZ_Epoch_Server11.Chernarus file in your MPMissions folder.
This includes Axe Cops Multi Char support.

and run the following querys

ALTER TABLE `Character_DATA` ADD COLUMN `Wealth` INT UNSIGNED NOT NULL DEFAULT 0 AFTER `Infected`;
ALTER TABLE `Character_DATA` ADD COLUMN `Bank` INT UNSIGNED NOT NULL DEFAULT 1000 AFTER `Wealth`; 
ALTER TABLE `Character_DATA` ADD COLUMN `Slot` TINYINT UNSIGNED NOT NULL DEFAULT 1 AFTER `PlayerUID`;

modify your player cleanup Query from deleting all 'dead' players with something like

DELETE n1 FROM Character_DATA n1, Character_DATA n2 WHERE n1.CharacterID < n2.CharacterID AND n1.PlayerUID = n2.PlayerUID 

then the last player entry will remain dead or alive, and palyer will not loose their "bank balance" or Humanity!

Thats it and you are Done!




Alternatively you can modify you own files below.

You might want to compare/edit the .sqf files rather than replace, if you already have made modifications to them.


  1) run the SQL query to add the Required columns to the "Character_DATA" table in your Epoch database:
ALTER TABLE `Character_DATA` ADD COLUMN `Wealth` INT UNSIGNED NOT NULL DEFAULT 0 AFTER `Infected`;
ALTER TABLE `Character_DATA` ADD COLUMN `Bank` INT UNSIGNED NOT NULL DEFAULT 1000 AFTER `Wealth`;

 2) unpack your dayz_server.pbo

 3) copy the file HiveExt.dll to the @DayZ_Epoch_Server folder (overwrite the Epoch file)


 4) Replace the file compile\server_playerSetup.sqf, in your dayz_server.pbo with File supplied.


 5) Replace the file compile\server_playerSync.sqf, in your dayz_server.pbo with File supplied.

<<<<<<< HEAD

 6)     If its a standard dayz_server pbo (ie: if not and modifying to Zupa's 999 version) then you will need to add the files in Server Folder to the Relevent folders.
 

 7)	repack your dayz_server.pbo

  
 8)     If modifying Zupa's 999 version In Your Mission folder, Replace the relevent files in the missions folder .

=======

 6) repack your dayz_server.pbo


you will need to edit your scripts for use.

If you are using your own scripts, you will need to edit your scripts!!!! 

to call eg:-

PVDZE_plr_Save = [_activatingPlayer,(magazines _activatingPlayer),true,true] ;
publicVariableServer "PVDZE_plr_Save";



"wealth" and "bank" variables will need to be used, (unless you change there decleration in the server_playerSetup.sqf and server_playerSync.sqf  to what ever variables you use to store your player money and bank declerations in your scripts).
=======
i have added a gold folder in my github file, it is quick and dirty edit of Zupa's V1.0 from his github. i am sure he will clean it up if he wishes to use the .dlls

loads of Credit goes to him for those.



if you use this file and find it useful, please consider a donation to fund my future works..

https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=akatitan%40sky%2ecom&lc=GB&item_name=TiTAN&currency_code=GBP&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted

the files in the gold folder are a quick and dirty code replacement for Zupa's gold scripts v1.0 Credit goes to him for them.


the files in the gold folder are a replacement for Zupa's gold scripts Credit goes to him (and i believe Maca for them).

=======
