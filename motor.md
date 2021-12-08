# Motor Sizing

The motor is the primary component, so the rest of the system should be built around it. As such, it's not a bad idea to start with it.

## Motor Types

There are a couple types of motors, two of which were considered:
1. Brushed motors. Simple, but they require literal brushes inside to transfer power which could wear out. Also, they aren't as efficient as brushless motors.
2. Brushless motors. More complex, and more efficient. Another nice feature is that they are widely available in different sizes for RC cars, and can be waterproof (quite useful for a bike that can ride in the rain). For that reason, I decided up front to use a brushless motor.

## Bike Physics

For this example, the aim was for a bike that can be driven as if it was an electric motor cycle, ie with a powerful enough motor to accelerate from a stop and maintain a reasonable speed. Others may be looking for more performance, or perhaps less (just a simple assist to help get up hills). Either way, the process must start by figuring out how much energy we must exert to move me and the bike.

### Motor Wattage

To find how much energy it takes to move, assume the bike and rider are one. If we put some energy into that object (whether by pedaling or using a motor), that energy has to go somewhere and will move us. We just need to find out how much energy.

For this example build, assume the rider can accelerate from a stop to 20mph to ride at a reasonable speed on the road. The bike and rider weigh about 185 pounds. Because the current concern is with energy, find the energy at 0mph and 20mph. Using the formula `E=.5mv^2` (energy [in joules] = .5 * mass [kilograms] * velocity [meters per second] squared), we find the energy in a nomoving bicycle to be 0 J, and a 20mph (8.9m/s), 185 lb (83.9kg) bike to have about 3353 joules. Finding the difference between the two, we know that to make a bike move at 20mph, we must add 3353 joules to it.

Finally, the acceleration. In the example, the desired acceleration is from 0 to 20mph in 10 seconds. There's a neat unit called the Watt, which represents how fast energy is flowing. It takes 3353 joules to accelerate the bike (from the previous step). If that energy was added very slowly (a low wattage), it would still be added, just taking a long time. On the other hand, adding the energy very fast would result in faster acceleration. The formula for wattage is quite simple: `Wattage = Joules / Seconds`. Plugging in the example numbers, we get `335W = 3353J/10S`.

Just a note, this is a quite simplified way to work out the math, as it completely ignores friction and air resistance. But, it's a good starting point.

Finally, electric motors are not completely efficient, so more energy will have to be used than expected. Brushless motors are about 80% efficient[^1], so the motor will need to be 125% more powerful than expected. As such, assuming these numbers, the actual motor wattage will need to be `335W*1.2=402W`. Now, this is a theoretical minimum number, so it will be treated as an absolute minimum. Increasing wattage will increase acceleration, which is desirable.

### Motor Specs

Now we have the necessary motor wattage, it would be tempting to grab any cheap 400 watt motor and attach it. The problem with this, however, is that motors essentially provide two things: speed (how fast it spins) and torque (how strong the turning is). The formula for motor wattage basically depends on just these two factors. So, even though a motor is 400 watts, it may spin super slow. It'll be powerful, but too slow to be actually spin our tire fast enough. So, we must account for these two.

Like mentioned earlier, I decided on a brushless RC car motor. These are commonly sold based on two numbers, wattage and kV rating. Complicating matters, they usually don't explicitly give a torque rating, so more math is in order.

The kV rating basically tells how fast the motor will spin based on how much voltage is applied. More volts = more faster. In fact, 1 volt will spin the motor at the kV rating, 2 volts will spin it at twice, etc. So, to find how fast the motor will spin, we just need to use this formula: `Speed = kV rating * voltage`.

To find the torque of the motor, we can use the formula `Torque (lb*ft) = wattage * 7 / rpm`.

I started shopping around for motors, and found [this] one from Amazon. It's 1800 watts (way more than the theoretical 400 we found earlier), and has a kV rating of 2250rpm/volt.  I will be running the motor at 12v (discussed more in the battery section), so I can expect `12v * 2250rpm/v = 27,000 rpm` max speed. At that speed, `1800 * 7 / 27000 = .46 lb*ft` of torque. So, this motor spins quite fast but doesn't have a lot of turning force. If it was attached directly to the hub of the bike, the bike wouldn't move because the torque is way too low. In a world without friction, it would probably start to move, but absurdly fast (about 2088 mph acutally). Of course, we would never really get that fast. So, because we have plenty of wattage, we just need to convert some of that speed to torque. We can use a magical thing called gears to do that!

#### Gear Ratios

Gears do exactly what we need to do, with a reasonable formula: the ratio of teeth (or circumfrence) is the same as the speed ratio, and the reciprocal of the torque ratio. What that means is if gear 1 is twice as big as gear 2, gear 2 will spin twice as fast as gear 1, yet have double the torque. Perfect! Trading speed for torque.

In our case, we have perfect gears: a tiny motor shaft, and a huge bike tire. Of course, I'll put some sort of wheel on the motor shaft so I get a little more friction. Jumping ahead a little, but my original plan was to directly drive the wheel with the motor just rubbing the sidewall. This lead to problems down the road, but for the sake of the math, I'll continue. Anyway, the circumfrance of my bike tire is just 26 inches (diameter) times pi, or 81.68 inches. The circumfrance of a small wheel I found was only 1.3 inches. That's means that the the speed will be reduced by a factor of 62, while the torque will be multiplied by a factor of 62. So now, our original speed of 2088mph is now only 33mph. Much better and more reasonable!

Also, the torque is quite a bit more. Now, it's 28.52 pound feet, much more reasonable.

So, all that being said, I chose the motor I did for the following reasons:
1. The theoreticl maximum speed (33mph) is higher than originally wanted.
2. The wattage (1800) is much more than the bare theoretical minimum.
3. It's a waterproof motor.
4. It's brushless.


[^1]: "Brushless Motor Efficiency and Constants -", _Radiocontrolinfo.com_, 2021. [Online]. Available: https://www.radiocontrolinfo.com/brushless-motor-efficiency/. [Accessed: 08- Dec- 2021]
