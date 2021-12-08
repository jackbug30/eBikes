# Battery Selection

There are lots of battery choices, some of which were considered.

## Lead Acid

Lead Acid batteries are simple, in fact most car batteries are lead acid. They commonly come as sealed, maintenance free batteries, which offer many advantages. They are already in a hard plastic case, can be mounted in any orientation, and are easy to charge with a simple off the shelf charger.

On the negative, they aren't super power dense[^1]. It takes large lead acid batteries to hold the same energy as some of the other options. Also, if they are damaged, they will leak battery acid and may freeze in extreme cold (because they are full of liquid).

## Lithium

Lithium batteries are great because they pack much more energy into a smaller package[^1].

However, they are much more difficult to charge than lead acid: to do it properly, each cell needs to be balance charged. This means a big, slow, specialized charger. Also, they are quite dangerous. They do not always come in a hard plastic case like lead acid [here](https://www.towerhobbies.com/product/11.1v-3200mah-3s-30c-lipo-battery-ec3/EFLB32003S30.html) is an example. Additionally, lithium batteries explode or burst into flames when damaged or overheated[^2].

## Ni-Cd and Ni-MH

These chemistries offer some advantages over lead acid (primarily, they are more energy dense) and potentially less dangerous than lithium[^1].

However, they commonly come in small cells that would have to be wired together. Additionally, they may develop a 'memory' where they lose capacity over time if improperly used, although different sources indicate this is not always the case[^3].

## Decision: lead acid

For the prototype, lead acid batteries were selected. Although the capacity of lithium batteries is attractive, the threat of fire or explosion of a battery on a bicycle (which can easily crash or even simply fall over) is too high without better containment. It may be nice to upgrade in the future, but for a prototype, robust lead acid batteries were selected. Ni-Cd and NI-MH are also viable options, except that they would have to be purchased as individual cells and wired together. It was simply easier to purchase a few large lead acid batteries than many small cells.

## Voltage

I decided on 12v batteries. This is in part because my motor would run fine at 12v, and the wiring at that voltage is simple enough.

[^1]: L. Keith Araujo - Epec, "Battery Comparison of Energy Density - Cylindrical and Prismatic Cells", _Epectec.com_, 2021. [Online]. Available: https://www.epectec.com/batteries/cell-comparison.html. [Accessed: 08- Dec- 2021]
[^2]: J. Jhaveri, "[Battery Safety] Top 5 Reasons Why Lithium-Ion Batteries Catch Fire — ION Energy", _ION Energy_, 2021. [Online]. Available: https://www.ionenergy.co/resources/blogs/battery-safety/. [Accessed: 08- Dec- 2021]
[^3]: "The memory effect in batteries: what it is and how to prevent it | Panasonic eneloop", Panasonic-eneloop.eu, 2021. [Online]. Available: https://www.panasonic-eneloop.eu/en/news/memory-effect-batteries-what-it-and-how-prevent-it. [Accessed: 08- Dec- 2021]
