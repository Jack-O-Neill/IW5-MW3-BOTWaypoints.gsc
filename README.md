# IW5-MW3-BOTWaypoints.gsc
Credits:- INEEDBOTS for his BOTWARFARE
These are some of my botwarfare waypoints i made to help bots move better when hosting ported/custom maps.
There are 2 files inside each folder, a)The ```mp_mapname.gsc``` and b)A few lines of text you need to add to ```_bot_utility.gsc``` file.

STEP 1:-
Copy the ```mp_mapname.gsc``` and paste it in the following location:-
```plutonium\storage\iw5\maps\mp\bots\waypoints```

STEP 2:-
The ```_bot_utility.gsc``` can be located in the following location:-
```plutonium\storage\iw5\maps\mp\bots\_bot_utility.gsc```
Open ```_bot_utility.gsc``` using notepad++ etc.
Search for a few lines of text:-

```load_waypoints()
{
	level.waypointCount = 0;
	level.waypointUsage = [];
	level.waypointUsage["allies"] = [];
	level.waypointUsage["axis"] = [];

	if ( !isDefined( level.waypoints ) )
		level.waypoints = [];

	mapname = getDvar( "mapname" );

	wps = readWpsFromFile( mapname );

	if ( wps.size )
	{
		level.waypoints = wps;
		printLn( "Loaded " + wps.size + " waypoints from csv." );
	}
	else
	{
		switch ( mapname )
		{
		case "mp_complex":
			level.waypoints = maps\mp\bots\waypoints\mp_complex::mp_complex();
			break;
			default:
				maps\mp\bots\waypoints\_custom_map::main( mapname );
				break;
		}

		if ( level.waypoints.size )
			printLn( "Loaded " + level.waypoints.size + " waypoints from script." );
	}
  
  This is the part you need, it is where you enter the text for each "mp_mapname.gsc":-
  
  
		switch ( mapname )
		{
      case "mp_complex":
			level.waypoints = maps\mp\bots\waypoints\mp_complex::mp_complex();
			break;
      default:
				maps\mp\bots\waypoints\_custom_map::main( mapname );
				break;
		
 Adding another would look like this:-
 
      case "mp_complex":
			level.waypoints = maps\mp\bots\waypoints\mp_complex::mp_complex();
			break;
			case "mp_subbase":
			level.waypoints = maps\mp\bots\waypoints\mp_subbase::mp_subbase();
			break;
    
      etc,etc,etc
      
All gsc's were created using the botwarfare wp editor and passed all waypoint checks, if you encounter any problems feel free to contact me on Plutonium Forum or Discord
Jack O'Neill
