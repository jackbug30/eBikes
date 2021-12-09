# Battery Selection

[Home](index) | [Motor size](motor) | Batteries | [Motor mounting](motor-mount) | [Final assembly](final-assembly)

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

Additionally, 12V batteries were selected. It is a very common for lead acid batteries in this size to be 6 or 12 volts. 12V were selected because it results in twice as much speed and torque as opposed to 6v batteries (from the motor section). Also, the specific motor selected is rated for 22 volts max, so two 12v batteries in series, resulting in 24V, is too much. In theory three 6v batteries could be tied in series for 18V, however 12V batteries are simply more common so 12v was selected.

## Capacity

The final characteristic of a battery is the capacity, telling how much power it can supply for how long. A common number given by a battery manufacturer is Ah (amp hours), or how long (in hours) the battery can supply one amp. The relationship is linear, so said battery could also supply 2 amps at half the time, 4 amps and one quarter the rated time, etc. In other words, `Ah rating = amps drawn * hours drawn`.

Ah can be easily converted to Wh (watt hours) by simply multiplying by the battery voltage, in this case 12v, so that we can use watts instead of amps, which simplifies the next step; `Wh rating = watts drawn * hours drawn`

The average expected power consumption of a bike at 20mph is about 180 watts (this accounts for air resistance, which was ignored earlier)[^4]. This number is assuming no hills, so the true number is likely much higher. However, it gives a reasonable datapoint to work from. It would be great, for the prototype, to be able to ride for a full hour without having to recharge. So, using the run time formula, `180 watts drawn * 1 hour drawn = 180Wh`. Now, converting that to Ah (`180Wh / 12v`), a total Ah rating of 15Ah is necessary.

Finding a single 12v, 15Ah battery was difficult, but it was easy to find smaller batteries, specifically [these](https://www.amazon.com/dp/B00K8V30D0?psc=1&ref=ppx_yo2_dt_b_product_details). Each is rated for 7.2Ah, but if they are attached in parallel, the total rating is 14.4Ah, quite close to the desired 15Ah. For this reason, two of these batteries were purchased.

[^1]: L. Keith Araujo - Epec, "Battery Comparison of Energy Density - Cylindrical and Prismatic Cells", _Epectec.com_, 2021. [Online]. Available: https://www.epectec.com/batteries/cell-comparison.html. [Accessed: 08- Dec- 2021]
[^2]: J. Jhaveri, "[Battery Safety] Top 5 Reasons Why Lithium-Ion Batteries Catch Fire — ION Energy", _ION Energy_, 2021. [Online]. Available: https://www.ionenergy.co/resources/blogs/battery-safety/. [Accessed: 08- Dec- 2021]
[^3]: "The memory effect in batteries: what it is and how to prevent it | Panasonic eneloop", Panasonic-eneloop.eu, 2021. [Online]. Available: https://www.panasonic-eneloop.eu/en/news/memory-effect-batteries-what-it-and-how-prevent-it. [Accessed: 08- Dec- 2021]
[^4]: S. Gribble, "An interactive model-based calculator of cycling power vs. speed", _Gribble.org_, 2021. [Online]. Available: https://www.gribble.org/cycling/power_v_speed.html. [Accessed: 08- Dec- 2021]
