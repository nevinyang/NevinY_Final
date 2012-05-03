# Application Flow Attributes #

## ID attribute values ##
### This design relies on four unique identifiers for representations: ###
**finals**
    Applied to a DIV tag. The data of a Finals series in this representation.
**game**
	Applied to a DIV tag. The data of a Finals game in this representation. 
**listfinals**
	Applied to a DIV tag. The list of NBA Finals series in this representation. This list may contain 0 or more Finals series.
**listgames**
	Applied to a DIV tag. The list of all Finals games in this representation. This list may contain 0 or more Finals games.

## Class attribute values ##
### Clients should be prepared to recognize the following class values: ###
**finals-new**
	Applied to a FORM tag. A link template to create a new NBA Finals series. INPUT[hidden].name="_method" element is used to dynamically treat the form as a PUT request when Finals year exists.  The element must be set to FORM.method="post" and should contain the descendant elements:
		INPUT[hidden].name="_method"
		INPUT[text].name="id"
		INPUT[text].name="team1_gamesWon"
		INPUT[text].name="team2_gamesWon"
		TEXTAREA.name="recap"
		INPUT[text].name="team1_id"
		INPUT[text].name="team1_name"
		TEXTAREA.name="team1_description"
		INPUT[text].name="team2_id"
		INPUT[text].name="team2_name"
		TEXTAREA.name="team2_description"
**game-new**
	Applied to a FORM tag. A link template to create a new game. The element must be set to FORM.method="post" and should contain the descendant elements:
		INPUT[hidden].name="finals"
		INPUT[hidden].name="team1_id"
		INPUT[hidden].name="team2_id"
		INPUT[text].name="gameid"
		INPUT[text].name="team1Score"
		INPUT[text].name="team2Score"
		TEXTAREA="recap"
**game-update**
	Applied to a FORM tag. A link template to update a game. The element must be set to FORM.method="post" and should contain the descendant elements: 
		INPUT[hidden].name="gameid"
		INPUT[hidden].name="finals"
		INPUT[hidden].name="team1_id"
		INPUT[hidden].name="team2_id"
		INPUT[text].name="team1Score"
		INPUT[text].name="team2Score"
		TEXTAREA="recap"
**games-search**
	Applied to a FORM tag. A link template used to search all games. The element must be set to FORM.method="get" and should contain the descendant element:
		INPUT[text].name="gameid"

## Name attribute values ##
### Name attributes identify a representation element that will be used to supply data to the server during a state transition. Clients should be prepared to supply values for the following state transition elements: ###
**_method**
	Applied to an INPUT[hidden] element. Used to dynamically change a form method to PUT.
**id**
	Applied to an INPUT[text] element. Uniquely identifies a finals.
**team1_gamesWon**
	Applied to an INPUT[text] element. The number of games won by the winning team, team 1.
**team2_gamesWon**
	Applied to an INPUT[text] element. The number of games won by the losing team, team 2.
**team1_id**
	Applied to an INPUT[text] or INPUT[hidden] element. Uniquely identifies team 1.  INPUT[hidden] is used to pass the element from a Finals item to a game item.
**team1_name**
	Applied to an INPUT[text] element. The name of team 1.
**team1_description**
	Applied to a TEXTAREA element. Brief description of team 2, such as players or key information.
**team2_id**
	Applied to an INPUT[text] or INPUT[hidden] element. Uniquely identifies team 2. INPUT[hidden] is used to pass the element from a Finals item to a game item.
**team2_name**
	Applied to an INPUT[text] element. The name of team 2.
**team2_description**
	Applied to a TEXTAREA element. Brief description of team 2, such as players or key information.
**finals**
	Applied to an INPUT[hidden] element. The element is used to link a games item to a finals item.
**recap**
	Applied to a TEXTAREA element. Provides a brief synopsis of the event (for either a game or a finals).
**gameid**
	Applied to an INPUT[text] element. Uniquely identifies a game.
**team1Score**
	Applied to an INPUT[text] element. The score of team 1 in a single game.
**team2Score**
	Applied to an INPUT[text] element. The score of team 2 in a single game.

## Rel attribute values ##
### This design identifies a number of possible simple state transitions (static links) that may appear within representations. These will appear as HTML anchor tags with the following rel attribute values: ###
**home**
	Applied to an A tag. A reference to the starting URI for the application.
**finals**
	Applied to an A tag. A reference to a Finals representation.
**finals-new**
	Applied to an A tag. A reference to the finals-new FORM.
**game-new**
	Applied to an A tag. A reference to the game-new FORM.
**game-update**
	Applied to an A tag. A reference to the game-update FORM.
**game**
	Applied to an A tag. A reference to a Finals game representation.
**games-search**
	Applied to an A tag. A reference to the games-search FORM.
**listfinals**
	Applied to an A tag. A reference to a list representation of all Finals in the database.
**listgames**
	Applied to an A tag. A reference to a list representation of all Finals games in the database.
	
# Data Types and Properties #
	
## Extended schema fields ##
### This design extends the SportsTeam (http://schema.org/SportsTeam) and SportsEvent (http://schema.org/SportsEvent) items to SportsTeam/Basketball, SportsEvent/BasketballGame and SportsEvent/NBAFinal for marking up content.  As these item types are extended, only properties not already listed on the parent item type will be described.  These extended types will contain the following additional itemprop values: ###

```
Thing > Event > SportsEvent/NBAFinal' (http://schema.org/SportsEvent)
```
**winningTeam**
	Basketball team that won this NBA Finals
**losingTeam**
	Basketball team that lost this NBA Finals
**winnerScore**
	Number of games the winning basketball team won.
**loserScore**
	Number of games the losing basketball team won.

```
Thing > Event > SportsEvent/BasketballGame (http://schema.org/SportsEvent)
```
**association**
	The sports association this team belongs to.
**gameNum**
	The number of the game in the Finals series.
**team1Score**
	The score for team 1.
**team2Score**
	The score for team 2.

```
Thing > Organization  > SportsTeam/Basketball [test](http://schema.org/SportsTeam)
```
**abbreviation**
	The abbreviation of team's official name.
