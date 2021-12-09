# Motor Sizing

[Home](index) | Motor size | [Batteries](batteries) | [Motor mounting](motor-mount) | [Final assembly](final-assembly)

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

Now that the wattage is in hand, it would be tempting to grab any cheap 400 watt motor and attach it. The problem with this, however, is that motors essentially provide two things: speed (how fast it spins) and torque (how strong the turning is). The formula for motor wattage basically depends on just these two factors. So, even though a motor is 400 watts, it may spin too slow. It'll be powerful, but too slow to be actually spin the tire fast enough. So, these factors must be accounted for.

Like mentioned earlier, the prototype will use a brushless RC car motor. These are commonly sold based on two numbers, wattage and kV rating. Complicating matters, the torque rating is usually not explicity given, so it must be calculated.

The kV rating indicates how fast the motor will spin based on how much voltage is applied. More volts = more speed. In fact, 1 volt will spin the motor at the kV rating, 2 volts will spin it at twice, etc. So, to find how fast the motor will spin, simply use this formula: `Speed = kV rating * voltage`.

To find torque from wattage and RPM, this formula may be used: formula `Torque (lb*ft) = wattage * 7 / rpm`.

Knowing this, the search for a motor started. [This](https://www.amazon.com/gp/product/B07BGZWFMP/ref=ppx_yo_dt_b_asin_title_o06_s00?ie=UTF8&psc=1) motor was located on Amazon.com. It's 1800 watts (way more than the theoretical 402 calculated earlier), and has a kV rating of 2250rpm/volt.  It will be run at 12v (discussed more in the battery section), so `12v * 2250rpm/v = 27,000 rpm` max speed is expected.. At that speed, `1800 * 7 / 27000 = .46 lb*ft` of torque. So, this motor spins quite fast but doesn't have a lot of turning force. If it was attached directly to the hub of the bike, the bike wouldn't move because the torque is way too low. In a world without friction, it would probably start to move, but absurdly fast (about 2088 mph acutally). Of course, it would never really get that fast. So, this motor has plenty of wattage, but some of that speed must be converted to torque.

#### Gear Ratios

Gears do exactly that: trade speed and torque, with a reasonable formula: the ratio of teeth (or circumfrence) is the same as the speed ratio, and the reciprocal of the torque ratio. What that means is if gear 1 is twice as big as gear 2, gear 2 will spin twice as fast as gear 1, yet have half the torque. Perfect! Trading speed for torque.

In this case, the gear ratios are perfect: a tiny motor shaft, and a huge bike tire. Jumping ahead, the original prototype plan was to directly drive the bike tire with the motor shaft. This lead to problems (discussed in the motor mounting section), but for the sake of completeness, this example will be worked out. Anyway, the circumfrance of the bike tire is just 26 inches (diameter) times pi, or 81.68 inches. The circumfrance of a small wheel (intended to be installed on the motor shaft) was only 1.3 inches. That's means that the the speed will be reduced by a factor of 62, while the torque will be multiplied by a factor of 62. So now, the original top speed of 2088mph is now only 33mph. Much better and more reasonable!

Also, the torque is quite a bit more. Now, it's 28.52 pound feet, much more reasonable.

So, all that being said, the selected motor was selected for these reasons:
1. The theoreticl maximum speed (33mph) is higher than originally wanted.
2. The wattage (1800) is much more than the bare theoretical minimum.
3. It's a waterproof motor.
4. It's brushless.

## Speed Controller

Finally, the motor needs a controller. Because it is brushelss, power cannot be directly applied as the internal wiring is more complex than a simple brushed motor. The motor is 1800W and will be driven at 12v. Watts can also be calculated based on voltage and current using the formula `wattage = volts * amps`, or `amps = wattage / volts`. As such, the maximum current draw of the selected motor is `150A = 1800W / 12V`.

Having a speed controller rated for that current would be ideal, however they proved to be prohibitively expensive for a prototype. A better option was [this](https://www.amazon.com/gp/product/B07JZVZJKS/ref=ppx_yo_dt_b_asin_title_o06_s02?ie=UTF8&psc=1) speed controller, also located on Amazon.com. It is waterproof (perfect for a bicylce) and programmable. This means that a [programming device](https://www.amazon.com/gp/product/B08FCF8JHV/ref=ppx_yo_dt_b_asin_title_o05_s00?ie=UTF8&psc=1) can be used to tweak various parameters, such as braking power and acceleration. It can only provide 80A, however. That said, 80A at 12V is 960W, still much higher than our theoretical minimum. It also provides a simple upgrade path in the future; a new speed controller can be swapped in to provde over twice the performance without needing an entirely new motor and drivetrain.

### Throttle Input

The final piece of the motor control system is a mechanism to command the speed controller to run at a specific speed. Because the selected controller is intended for a remote control car, is uses standard RC servo signalling [^2]. The intention in this project is to eventually have a complete electrical control system (providing battery charge, speed, current draw, etc) to the rider, which can also be used as a throttle input (more detail in the finishing touches section). For the prototype however, this is not necessary, so a simple [RC servo tester](https://www.amazon.com/gp/product/B07TQSKLBK/ref=ppx_yo_dt_b_asin_title_o05_s00?ie=UTF8&psc=1) was selected. It provides a simple knob to control motor speed.


[^1]: "Brushless Motor Efficiency and Constants -", _Radiocontrolinfo.com_, 2021. [Online]. Available: https://www.radiocontrolinfo.com/brushless-motor-efficiency/. [Accessed: 08- Dec- 2021]
[^2]: "Servo control - Wikipedia", _En.wikipedia.org_, 2021. [Online]. Available: https://en.wikipedia.org/wiki/Servo_control. [Accessed: 08- Dec- 2021]
