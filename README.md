# commander-cli

Our beginning commander utility tool for tracking all MTG Commander things.

Our little practise project to boost our python skills. Starting with a simple command line interface and then expand to more complex things.

## CLI features

Two options: 

1) Run the CLI that keeps the process going waiting for more instructions, or
2) Cache the information somewhere and new commands affect that cache - think this will be nicer

__The common ideas will be:__

* Everytime you run a command or initialised there should be a nice summary display to show you all of the key kpis
* Run a command that will setup a new game for you with n players, their health totals, number of times commanders summoned, and damage dealth by other players commanders.
* Command that says player x summoned their commander
	* put up their commander summoning tally
	* Can add a feature to say how much extra mana is requried, ie 4 Summons (+8 mana)
* Damage to player x
	* can have this simpler command to not have to track players as much
* Command that player x damaged player y
	* should reduce the health of player y
	* optional flag to say it was by a commander
	* Can then also include summary stats like total damage dealth, who each player attacked the most etc
* Command to add health to player x
	* will be needed to cover all health movements
* Health stealing??
	* this can also just be damage and then healing as 2 separate commands

## Development

Intructions for how to get the code installed to run/develop on your computer.

Also housekeeping rules we want to stick to to keep the code tidy.

### Git

Will be using `git flow` methodology to keep things nice and tidy.

## Future Plans

### Near future

* Simple command line interface
* Things to track:
  * Commander life per player
  * Summonder damage to each player by each player
  * Number of commander summons

### Far future

* User interface of some kind
* Use something like 'Click' to do all the CLI nexting
