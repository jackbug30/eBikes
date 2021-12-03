# Motor Sizing

The motor is the primary component, so the rest of the system should be built around it. As such, we'll start by talking about it.

## Motor Types

There are a couple types of motors, two of which I considered:
1. Brushed motors. Simple, but they require literal brushes inside to transfer power which could wear out. Also, they aren't as efficient as brushless motors.
2. Brushless motors. More complex, and more efficient. Another nice feature is that they are widely available in different sizes for RC cars, and can be waterproof (quite useful for a bike that can ride in the rain). For that reason, I decided up front to use a brushless motor.

## Bike Physics

In my application, I am aiming for a bike that can be driven as if it was an electric motor cycle, ie with a powerful enough motor to accelerate from a stop and maintain a reasonable speed. Others may be looking for more performance, or perhaps less (just a simple assist to help get up hills). Either way, we must start by figuring out how much energy we must exert to move me and the bike.

### Motor Wattage

To find how much energy it takes to move, assume the bike and rider are one. If we put some energy into that object (whether by pedaling or using a motor), that energy has to go somewhere and will move us. We just need to find out how much energy.

For my application, because I want to accelerate from a stop up to say, 20mph, so I can ride at a reasonable speed on the road. My bike and I also weigh about 185 pounds. Because we're talking about adding energy to our bike, let's find the energy at 0mph and 20mph. Using the formula `E=.5mv^2` (energy [in joules] = .5 * mass [kilograms] * velocity [meters per second] squared), we find the energy in a nomoving bicycle to be 0 J, and a 20mph (8.9m/s), 185 lb (83.9kg) bike to have about 3353 joules. Finding the difference between the two, we know that to make a bike move at 20mph, we must add 3353 joules to it.

Finally, I want to be able to accelerate from 0 to 20mph in 10 seconds. There's a cool unit called the Watt, which represents how fast energy is flowing. We know that it takes 3353 joules to accelerate the bike. If we wanted to accelerate really slowly, we could pump energy in slowly (low wattage), or fast to accelerate fast (high wattage). The nice thing is that the formula for wattage is just `Wattage = Joules / Seconds`. Plugging our numbers in, we get `335W = 3353J/10S`.

Just a note, this is a quite simplified way to work out the math, as it completely ignores friction and air resistance. But, it's a good starting point. Lets count for some of those other issues now:

This simple math tells us that a bike moving at a constant speed doesn't change in energy, so we won't have to add any to it to keep it going. We know intuitively that this is wrong because on a flat road you still have to pedal occasionally, but it turns out that a bike at this weight will take about 250 watts to maintain 20mph. That number is lower than our earlier 335, which is nice.

Finally, electric motors are not completely efficient, so we'll have to put more energy into it than we can get out. Brushless motors are about 80% efficient, so we will need a motor 120% more powerful than we expect. As such, assuming these numbers, we'll need a motor `335W*1.2=402W`. Now, this is a theoretical minimum number, so I plan to use a motor quite a bit more powerful, because more power can't hurt.

### Motor Specs

Now we have the necessary motor wattage, it would be tempting to grab any cheap 400 watt motor and attach it. The problem with this, however, is that motors essentially provide two things: speed (how fast it spins) and torque (how strong the turning is). The formula for motor wattage basically depends on just these two factors. So, even though a motor is 400 watts, it may spin super slow. It'll be powerful, but too slow to be actually spin our tire fast enough. So, we must account for these two.

Like mentioned earlier, I decided on a brushless RC car motor. These are commonly sold based on two numbers, wattage and kV rating. Complicating matters, they usually don't explicitly give a torque rating, so more math is in order.

The kV rating basically tells how fast the motor will spin based on how much voltage is applied. More volts = more faster. In fact, 1 volt will spin the motor at the kV rating, 2 volts will spin it at twice, etc. So, to find how fast the motor will spin, we just need to use this formula: `Speed = kV rating * voltage`.
