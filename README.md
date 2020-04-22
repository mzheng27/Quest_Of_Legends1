# Quest_Of_Legends1
Quest version 1 designed in Java. Object Oriented. Players may play in teams to fight monsters, buy inventories, tour the map, and level up. 


>> To compile and execute enter:

javac play.java
java play

>> About the Game & User Input:

1. The user can quit buy entering P/p when not during a fight; or the game ends if one of the players has a hero that reaches level 11. 

2. Abbreviation for Tool objects (Potion, Armor, Weapon, Spell) is the first 3 letters. Abbreviation
for Fighter objects (Hero, Monster) is the first 4 letters. If the item's abbreviation is not unique, the user should types in the full name. 

3. While not Fighting:  To move up (W/w), move left (A/a), move down(S/s), move right(D/d), quit game (Q/q), show info (I/i), 
<NEW>: uses a market cell (M/m), switch player (C/c), drink Potion (P/p), change weapon (T/t), (MAP/map) for
displaying the board. 

4. If playing in teams. the current player is marked with a "#" on the map. 

>>  Usability of each class:

Tool: a class for tools that the players can buy from the Quest's market, implements the GameTool<Hero> interface which is a generic interface that describes how GameTool for 
the class T (Hero in this case) should behave
subclasses: 
	<1>Armor: represents tools in the Quest Market which are specified to be Armory (has damage reduction effect).
	<2>Weapon: for tools in the Quest market which are specified to be Weaponry (has damage effect). 
	<3>Spell (abstract): for tools in the Quest market which are specified to be Spells (has damage effect & backdrops monster's skills).
	Subclasses (Override the useTool method of the Spell class) 
		- FireSpell: represents fire spell, decreases defense of monster by 10%
		- IceSpell: represents ice spells, decreases damage of monster by 10%
		- LightSpell: lightening spells; decreases dodge of monster by 10%
	<4>Potions: represents tools in the Quest market which are specified to be Potions (can have various effects).

Fighter (abstract): implements the Fight interface and provides methods alive(), getStat(), getStat(boolean x), resetHp(int x). 
subclasses (overrides the getStat method in Fighter, provides a attack method which describes how this subclass of Fighter attacks. 
	<1> Hero: represents the heroes in the Quest.
	field:
	- LLBag: implements the Bag interface. Represents the behaviors of a hero's bag with a 	linked list.
	subclasses of Hero (override levelUp)
	- Paladin:represents the Paladins in Quest
	- Sorcerer: represents the Sorcerers in Quest
	- Warrior: represents the Warriors in Quest
	<2> Monster: represents the monsters in the Quest.

QuestMap:  a class that represents the Quest's map/board and its many usage. 
	field - cells: a 2-D list of Objects that implements the QuestCell interface.
	- Market:  a class that represents the Quest's tiles that are the Quest's market where the 	players may buy some tools for their heroes. Market implements the interface QuestCell. 
		- a Market object's field is composed of Store objects
			Store: a class that represents the Quest's Store which has tools that the hero 			can buy. 
		-  CommonZone: class that represents the Quest's tiles that are the common zones 		where the heroes may fight some monsters. 
		-  NonAccessible: representing the Non Accessible cells on the Quest Board, of type 		3; implements the QuestCell interface.

TeamPlayer - represents a team of Players who plays the Quest. Provides methods to switch to another player, and to get a string representation of all players and their heroes. In this version, the number of Players is between 1 and 3.  
	a TeamPlayer object's field if composed of Player objects:
	- Player: a class that represent the Player of game. 
		a field of Player object is TeamHero
		- TeamHero: represents a team of hero controlled by one player such that the 			number of heroes ranges from 1 to 3.

QuestList<T extends Hero>: a generic interface for the Lists of Heros in Quest. Ensures the Objects which implements it provides a create method and a getHeros method.
classes that implements QuestList:
	<1>PaladinList - a class that represents all Paladins (a type of Hero) in the Quest
	<2> SorcererList - a class that represents all Sorcerers (a type of Hero) in the Quest 
	<3> WarriorList - a class that represents all Warriors (a type of Hero) in the Quest 

MonsterList:  a class that represents all the monsters in Quest in a 2-D array such that the first index is a monster's level. 

QuestGame: a class that embodies the rules and playings of the Quest.
