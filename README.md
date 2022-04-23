# MMM-ResRobot

A module for MagicMirror2 (https://github.com/MichMich/MagicMirror) which shows scheduled departures from public transport stop(s) in Sweden. The module
uses the ResRobot API for which you do need to obtain an API key, see below.

# Get API keys

1. You need to register for a free account at https://www.trafiklab.se.
2. Create a new project and choose "ResRobot v2.1" and "GTFS Sverige 2" as API.

# Find Station ID
1. Download static data by following instructions at https://www.trafiklab.se/api/trafiklab-apis/gtfs-sverige-2/static-data.
2. Unzip the downloaded file and open stops.txt
3. Search for your Station.

# Install

1. Clone repository into `../modules/` inside your MagicMirror folder.
2. Run `npm install` inside `../modules/MMM-ResRobot/` folder
3. Add the module to the MagicMirror config
```
	{
		module: "MMM-ResRobot",
		position: "left",
		header: "Departures",
		config: {
			routes: [
				{from: "", to: ""},	// ResRobot Station IDs of starting and destination station(s). At least one route must be defined.
				{from: "", to: ""},	// "from" is required but "to" is optional (set "to" to empty string to indicate all destinations)
			],
			skipMinutes: 0,			// Skip departures that happens within the next <value> minutes.
			timeWindow: 120,		// Time interval in minutes that will be returned from ResRobot, max 1439
			maximumEntries: 6,		// Number of departures to show on screen
	        getRelative: 0,         // Show relative rather than absolute time when less than <valute> minutes left to departure, 0 = stay absolute
			truncateAfter: 5,		// A value > 0 will truncate direction name at first space after <value> characters. 0 = no truncation
			truncateLineAfter: 5,	// A value > 0 will truncate line number <value> characters. 0 = no truncation
	        showTrack: true,        // If true, track number will be displayed
            coloredIcons: false,    // Setting this to true will color transportation type icons according to colors in colorTable
			apiKey: ""				// Your ResRobot v2.1 apiKey
        }
    },
```
