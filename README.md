# commander-cli
# testing part 2

Our beginning commander utility tool for tracking all MTG Commander things.

Our little practise project to boost our python skills. Starting with a simple command line interface and then expand to more complex things.

TESTING
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

## Console outputs

* Summary output after every actions
* Have a detailed output upon request

### Summary output

* Players and health of each
* Maybe min remaining commander damage? ie min of (21 - most dmg from another commander)
	> This may be easier by adding in damage dealt and damage taken in the data??
* maybe number of summons?
* Should it look like a table or just a list view?

```
Player1: 40 HP
Player2: 60 HP
```

## Data Structures

### Overall damage tracking (1st step)

Use json/dictionary format for this as it is very flexible and makes it easy to track multiple things with the same blob of data.

```JSON5
{
	"player1": {
		"health": 100,
		"summons": 1,
		"total_damage: [
			{
				"to": "player2",
				"damage": 10
			},
			{
				"to": "player3",
				"damage": 5
			}
		],
		"commander_damage": [
			{
				"to": "player2",
				"damage": 3
			}
		]
	},
	"player2": {}
}
```

### Damage event tracking

Can keep track of all damage events with a `pandas` `dataframe`.

* Not sure if health/healing will be its own table or if it can be in here as a -ve damage value, or as its own column?? Need to think about self healing (ie no other player) as well as life stealing.
	* healing can be its own column and target can be the same player
	* can possible add in event type to say whether it is healing/stealing/spell/creature etc

| Caster | Target | Damage | Healing | Commander | Example of |
| ---- | --- | ------ | --------- | ---- | --- |
| p1 | p2 | 40 | 0 | false | normal damage |
| p1 | p2 | 40 | 0 | true | commander damage |
| p1 | p1 | 0 | 10 | false | self healing |
| p1 | p2 | 0 | 10 | false | healing other player |
| p1 | p2 | 10 | 0 | false | life stealing (dmg) |
| p2 | p1 | 0 | 10 | false | life stealing (heal) |

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

some delta

different delta
