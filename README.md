DayZChernarus Mission System
=============
Original code by <a href="https://github.com/theszerdi">TheSzerdi</a>, Falcyn and TAW_Tonic.

<h3>This has only been tested on Chernarus (1.7.7.1).</h3>  

 * Before installing you must first customize the fillboxes SQF's inside the Missions/Misc folder and the NPC's load-outs in the addunitserver SQF's. 
 
 * If you leave the script as is, you MUST update your BE filters with the attached files as it contains weapons that BE will kick for.


<h3>Installation</h3>

<b>server.pbo</b>

Copy the Missions folder to the root of the server PBO.

Open <b>server_functions.sqf</b>

<b>Find:</b>

	fn_bases = compile preprocessFileLineNumbers "\z\addons\dayz_server\compile\fn_bases.sqf";
	
<b>Insert after:</b>
	
	fnc_hTime = compile preprocessFile "\z\addons\dayz_server\Missions\misc\fnc_hTime.sqf"; //Random integer selector for mission wait time
	
<b>Find:</b>
	
	dayz_recordLogin = {
	private["_key"];
	_key = format["CHILD:103:%1:%2:%3:",_this select 0,_this select 1,_this select 2];
	_key call server_hiveWrite;
	};
	
<b>Insert after:</b>
	
	//----------InitMissions--------//
	MissionGo = 0;
	MissionGoMinor = 0;
	if (isServer) then { 
	    SMarray = ["SM1","SM2","SM3","SM4","SM5","SM6"];
	    [] execVM "\z\addons\dayz_server\missions\major\SMfinder.sqf"; //Starts major mission system
	    SMarray2 = ["SM1","SM2","SM3","SM4","SM5","SM6"];
	    [] execVM "\z\addons\dayz_server\missions\minor\SMfinder.sqf"; //Starts minor mission system
	};
	//---------EndInitMissions------//


 
<b>mission.pbo:</b>

Copy the included debug folder into the root of the mission.pbo.
	
The AI require faction settings. If you have SARGE AI or DZAI you're good to go. Otherwise add faction.sqf to the root of the mission.pbo and add this line to the end of your init.sqf:

    [] execVM "faction.sqf";

	
<h3>The Crates</h3>

Inside the MISC folder, there are 4 differing fillboxes scripts. They are set up like so:

* fillboxes.sqf - Large weapons crate.

* fillboxesS.sqf - Small weapons crate.

* fillboxesH.sqf - High value weapons crate.

* fillboxesM.sqf - Medical crate.

	
<h3>The Missions</h3>

The missions are split into two types, major and minor, and run as follows.


<h4>Major</h4>

<b>Bandit Weapon Cache.</b>  
Bandits have discovered a weapons cache! Kill them and secure the weapons for yourself!

<b>Medical C130 Crash.</b>  
A C-130 carrying medical supplies has crashed and bandits are securing the site! Take them on and secure it's cargo for yourself

<b>Bandit Medical Camp.</b>  
Bandits have set up a medical re-supply camp! Secure it for yourself!

<b>Bandit Heli Down!</b>  
A bandit supply helicopter has crash landed! Secure it and it's cargo for yourself!

<b>Medical Ural Attack.</b>  
Bandits have destroyed a Ural carrying medical supplies and secured it's cargo!

<b>Medical Supply Crate.</b>  
A medical supply crate has been secured by bandits! Kill them all to get the supplies!


<h4>Minor</h4>

<b>Bandit Hunting Party.</b>  
A bandit hunting party has been spotted! Kill them all and get their supplies!

<b>Medical Outpost.</b>  
A group of bandits have taken over a Medical Outpost!

<b>Bandit Stash House.</b>  
A group of bandits have set up a stash house!

<b>Bandit Helicopter Crash.</b>  
A bandit helicopter has crashed! Kill any survivors and secure the loot!

<b>Bandit Hummer Crash.</b>  
A bandit Humvee has crashed! Kill any survivors and secure the loot!

<b>Bandit Weapons Truck.</b>  
A bandit weapons truck has crashed! Kill any survivors and secure the loot!


		
	


	

