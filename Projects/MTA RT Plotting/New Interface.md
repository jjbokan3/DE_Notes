# Todo
- Utilize OpenStreetMap to allow for a search bar that displays the nearest station
- Create an interface where a portion of the screen is the map of the line and cars along it along with the ability to point and click to click a line/station
	- Map should only include a single or a few lines with cars
		- Once a line/station is clicked the map should pan into the line/station
	- Buttons to click the line should either then show the stations associated with it and/or pan into the location on the map
		- Figure out indiv line vs compelte route (N vs NQRW)
	- Include a details tab where you show:
		- Stations
		- Timetable
		- Overall health of the system
		- **Could be that depending on your click, the details tab will change**

# Updating graphic
- When selecting a line
	- Only show that line shape and the trains associated
	- Delete a line shape and trains associated when you unselect a line
- When selecting a station
	- Show the lines that connect to the station and the trains that will stop at the station
	- Only one station can be selected at a time
- When inputting an address, find nearby stations based on coordinates (show top 5-7)
	- These stations should likely be shown on the details tab


# Notes
- Z train not included in stops, stop times, and shapes



Train line Termini
- 5 train has two uptown termini and Nereid is not at all a common termini. 501 is one termini and 204 is Nereid terminus. Bowling Green (420) is not the terminus but Flatbush (247) is
- A train has three southern termini at Ozone (A65), Mott Av (H11) and Rockaway Park (H15)
- B train true termini is Bedford Pk (D03) but more trains go to 145th (D13)
- E train has two termini with Jamaica Center (G05) and Jamaica 179th (F01)
- 2 train true termini is Nereid Av (204)???
- M train terminus is Forest Hills (G08) but more trains run to Delancey (M18)
- Z train is same route as J