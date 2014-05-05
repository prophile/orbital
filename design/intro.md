Orbital
=======

Orbital is an [Escape Velocity][ev]-style to be made for One Game A Month, May
2014.  It is single-player, 2D, and ships without steak knives.

The basic mechanics broadly follow the tropes of a science fiction open-world
RPG: you have a *ship*, which can be flown around in -- and *jumped* between --
*star systems*. There are *stellar objects* including *planets*, *moons* and
*space stations* in *systems*, some of which can be *landed* on. There are also
*AI ships*, some which may or may not be *hostile*. In space, the player can
*fight* other ships. On stellar objects, the player has the option of *buying
new ships* at the *shipyard*, *trading* resources known as *junks*, or buying
*outfits* at the *outfitter* to upgrade their ship with new *weapons*, new
capabilities, or increased performance. There may also be *missions*, available
at the *mission computer*.

Star Systems
------------

A star system contains zero or more *stellar objects*, and has zero or more
two-way *links* to other star systems. It has a 2D galactic cartesian
coordinate, with units in light-years, a name (human-readable), and an
*identifier*.

Stellar Object
--------------

A stellar object is located within one star system, and has any combination of
the following services available:

* Outfitter
* Shipyard
* Trading Post
* Mission Computer
* Landing Site

If no landing site is available, craft will not be permitted to land.

A stellar object has a 2D stellar cartesian coordinate, with units in *space
metres*; a name (human-readable), a sprite, and an *identifier*.

Ship
----

A ship is the name for any craft that can fly. It has a number of *outfits*,
some of which some as standard, it has some level of *energy*, and is of some
*ship class*. It can optionally have a *name*.

TODO: flight behaviour

Ship Class
----------

Ships come in various different classes. A class has a *name*, a *sprite* and
possibly an *engine sprite*, and a list of *standard outfits*.

Individuals
-----------

TODO: write me

Entities and Behaviours
-----------------------

TODO: write me

Outfits
-------

TODO: write me

Weapons
-------

TODO: write me

AI
--

TODO: write me

Trading
-------

TODO: write me

Missions
--------

TODO: write me

Attributes
----------

TODO: write me

Space Metres
------------

Space is pretty big. Human engineering is capable of making only pretty small
ships. This could lead to some extremely dull gameplay.

As a compromise, Orbital uses a unit of *space metres*. These roughly correspond
to *one metre* for ships, *ten metres* for small stellar objects (like asteroids
or space stations) and *100km* for large stellar objects like moons or planets.

Identifiers
-----------

Identifiers are the internal handles for objects. While previous EV games used a
16-bit numeric resource ID, Orbital uses short, lowercase, hyphen-separated
strings. That is to say, strings matching `[a-z0-9-]`.

[ev]: http://www.ambrosiasw.com/games/ev/ "Escape Velocity, Ambrosia Software"

