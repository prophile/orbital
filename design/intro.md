Orbital
=======

Orbital is an [Escape Velocity][ev]-style to be made for One Game
A Month, May 2014.  It is single-player, 2D, and ships without steak
knives.

The basic mechanics broadly follow the tropes of a science fiction
open-world RPG: you have a *ship*, which can be flown around in --
and *jumped* between -- *star systems*. There are *stellar objects*
including *planets*, *moons* and *space stations* in *systems*,
some of which can be *landed* on. There are also *AI ships*, some
which may or may not be *hostile*. In space, the player can *fight*
other ships. On stellar objects, the player has the option of *buying
new ships* at the *shipyard*, *trading* resources known as *junks*,
or buying *outfits* at the *outfitter* to upgrade their ship with
new *weapons*, new capabilities, or increased performance. There
may also be *missions*, available at the *mission computer*.

Star Systems
------------

A star system contains zero or more *stellar objects*, and has zero
or more two-way *links* to other star systems. It has a 2D galactic
cartesian coordinate, with units in light-years, a name (human-readable),
and an *identifier*.

Stellar Object
--------------

A stellar object is located within one star system, and has any
combination of the following services available:

* Outfitter
* Shipyard
* Trading Post
* Mission Computer
* Landing Site

If no landing site is available, craft will not be permitted to
land.

A stellar object has a 2D stellar cartesian coordinate, with units
in *space metres*; a name (human-readable), a sprite, and an
*identifier*.

Landing on a stellar object refuels energy to full.

Ship
----

A ship is the name for any craft that can fly. It has a number of
*outfits*, some of which some as standard, it has some level of
*energy*, and is of some *ship class*. It can optionally have a
*name*.

Granted by outfits, ships have the following attributes:

* Turn Rate (this must be >0)
* Acceleration (this must be >0)
* Top Speed (this must be >0)
* Total Armour (this must be >0)
* Energy Capacity (this must be >0)
* Energy Regeneration Rate (this must be >0)
* Carrying Capacity (this must be >0)
* Jump Time (this must be >0)

Unlike in the original Escape Velocity, carrying capacity covers
both space used by outfits and space used by cargo.

The controls are basic: bank left, bank right, and thrust.

Ship Class
----------

Ships come in various different classes. A class has a *name*, a
*sprite* and possibly an *engine sprite*, and a list of *standard
outfits*.

Individuals
-----------

Individuals represent one person. That person probably pilots a
ship. Individuals have a *name*, a *current ship*, a *balance*,
and any number of *attributes*.

Entities and Behaviours
-----------------------

Entities are the generic type of anything which flies around in
space. They may be attached to a *ship* or a *stellar object*, or
neither, but not both. They have any number of *behaviours* attached,
as well as a *current position*, a *previous position*, and a
*heading*.

Behaviour are what make entities *do things*. The standard behaviours
are:

* Visible (makes it render a sprite)
* Targettable (makes it clickable as a target)
* Collidable (lets things collide with it)
* Engine (handles engine driving)
* Jump (handles jumping behaviour)
* Land (lets ships land on it, attached to a stellar object)
* PlayerControl (lets the player pump in engine commands)
* AIControl (lets the AI pump in engine commands)
* HomingControl (a simple homing mechanism targetting an entity)
* ForwardControl (a control mechanism with constant thrust, good
  for unguided projectiles)
* Asplode (makes it explode when hitting armoured entities)
* Armoured (gives the entity some amount of armour, which means
  things can asplode when they hit it and decrease that amount)
* Energetic (gives it energy, up to some maximum and increasing at
  some rate)

Outfits
-------

An outfit is associated with a *name* (which may be empty for hidden
outfits), an *identifier*, a *cost*, the amount they change any
*ship attributes*, an optional *action* to be run every tick, and
an optional *action* to be run on command (such as launching a
weapon).

Weapons
-------

TODO: write me

AI
--

Ship AI is a basic target-and-shoot affair, and follows a simple
state machine:

* GOTO (targetting a landable entity), leading to FIGHT if attacked
  or another GOTO or LEAVE once the target is reached;
* LEAVE (targetting an angle), which goes to a distance away from
  the system centre then jumps out at that angle, leading to FIGHT
  if attacked;
* FIGHT (targetting an entity), which goes to LEAVE once the target
  is no longer present.

Trading
-------

There are a number of *junks* available. Each has a base price.
Stellar objects that offer a *junk* will have some multiplier for
the price. They can be bought and sold. Each *junk* has a *base
price*, a *name* and an *identifier*.

Missions
--------

TODO: write me

Attributes
----------

An *attribute* is the equivalent of an *outfit* for an *individual*.
Missions are one type of attribute. Attributes have a *name* (which
may be null), an *identifier*,

Space Metres
------------

Space is pretty big. Human engineering is capable of making only
pretty small ships. This could lead to some extremely dull gameplay.

As a compromise, Orbital uses a unit of *space metres*. These roughly
correspond to *one metre* for ships, *ten metres* for small stellar
objects (like asteroids or space stations) and *100km* for large
stellar objects like moons or planets.

A space metre corresponds roughly to one pixel of space on-screen.

Time
----

Time in space is internally measured in *ticks*, which are equal
to one-thirtieth of a second, both in-universe and in practice.

Identifiers
-----------

Identifiers are the internal handles for objects. While previous
EV games used a 16-bit numeric resource ID, Orbital uses short,
lowercase, hyphen-separated strings. That is to say, strings matching
`[a-z0-9-]`.

[ev]: http://www.ambrosiasw.com/games/ev/ "Escape Velocity, Ambrosia Software"
