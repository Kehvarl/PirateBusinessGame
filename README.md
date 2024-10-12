# Pirate Business Game

## Concept
* Genre: Business Sim
* Rule: Start Small
* Setting: Pirates
* Theme: Stolen Identity

To fulfill these points, lets take them out of order.

First up, the setting of Pirates gives us a lot of guidance.  We'll almost certainly be using a ship or ships and stealing from other ships.

Next we'll look at the Start Small rule.  That's pretty self contained, and since we're working with ships it implies we'll begin with a small ship and progress to larger ships or fleets of ships.

The theme of Stolen Identity may give us a story hook for how the player starts out.  Either they've had their identity stolen and that has somehow lead them to piracy, or they've stolen the identity of a famous pirate.  Or perhaps we can use that for part of the game, they're in the process of stealing the identity of a famous pirate or pirates. Several options here and each gives the game a different flavor.

The final point is the genre of Business Simulation.  That tends to imply buying and selling, seeking customers, and trying to make money.  The Tycoon seties of games had you build various things to gain customers, money, and upgrades.  There's a potential there for a Pirate Tycoon type game were you invest in ships and crews, try to select routes that are rich in plunder but light on other pirates or various warships that might end your time at sea rather unpleasantly.  There's also potential for a clicker sort of game.   Click on ships to loot them, upgrade your ship to  unlock auto-clicks (crew and canon), and richer targets.

Both approaches would require some art assets, the Tycoon game would definitely be more involved.

## Gameplay
  Let's take the "Clicker" or "Idle" game approach.  We'll make this a "Business Sim" by allowing the player to invest in upgrades and other opportunities which generate some sort of revenue.

  The player will start with a small Ship in Port, they'll have almost no money so they can't buy many upgrades.

  While in Port the player can take several actions
  1) Purchase Upgrades
    a) Ships (More Cargo, More Crew, More Cannon, Special Rules)
    b) Crew (Increase Speed, Better Looting, Better Combat, Longer Range, Automate)
    c) Weapons (More Damage, More Loot, Longer Range)
  2) Investment Opportunities
    a) Dockyards
    b) Smugglers Dens
    c) Drinking Extablishments
    d) Other Pirate's Expeditions
    e) Insurance Schemes
  3) Sell Loot
  4) Head to Sea

  While out at Sea, the player's ship will gain actions, these actions can be used to
  1) Explore (Find Islands, Find Ships, Avoid Trouble)
    a) If Island is suitable, can set it as Home
  2) Attack
  3) Flee
  4) Return Home
  5) Trading Port

## Necessary Assets
  * Pirate Portrait
  * Some ships
  * frame
  * water
  * combat scenes
  * treasure scenes
  * island scenes
  * port scenes

## Implementation

### Phase 1
  Let's ignore all art and assets, and just consider the simulation itself.  What is our minimal setup for that?

  What variables do we track:
  * Current Game State
    * At Port
      * Trading
        * Sell
        * Buy
      * Depart
        * Unknown Waters
        * List of Known Destinations or Trade Routes
    * At Sea
      * Exploring
      * In Combat
  * Areas
    * Name
    * Type
      * Sea
      * Port
      * Special
    * Factions
    * Attackable
    * Combat Level Range
    * Treasure Level Range
    * Special Features
  * Ships
    * Name
    * Type
      * Merchant
      * Treasure Ship
      * Warship
    * Factions
    * Frequency
    * Attackable
    * Combat Level Range
    * Treasure Level Range
    * Special Features

  Example Areas
  * Main Port
    * Type: Port
    * Factions: {}
    * Attackable: False
    * Combat: 0
    * Treasure: 0
    * Special Features: []

  Any Port will offer trading
  Some Ports will have factions with favorable or unfavorable status.  This can impact availability of goods and alter pricing.

  Example Ships
  * Player
    * Type: Warship
    * Factions: {}
    * Attackable: True
    * Combat: 1
    * Treasure: 0
    * Speacial Features: [:player]
    * Current Cargo: {Prisoners: 0, <good>: 0}

  * Ship
    * Name: MoneyPit
    * Type: TreasureShip
    * Factions: {SomeOne:1}
    * Attackable: True
    * Combat: 1
    * Treasure: 1
    * Speacial Features: []

  * Ship
    * Name: Cargo
      * Type: Merchant
      * Factions: {SomeTwo: 5}
      * Attackable: False
      * Combat: 0
      * Treasure: 0
      * Special Features: []

  Trading Options
  * Upgrade Ship
    * Speed
    * Combat Level
    * Cargo Capacity
    * Crew
      * Add Navigator
      * Add Canoneer
      * Add Quartermaster
      * Add Lookout
  * Sell Cargo
    * Sell Goods
    * Ransom Prisoners
    * Sell Parts
  * Buy Cargo
    * Buy Goods
    * Buy Parts
  * Sell Ship
  * Buy Ship
