# Motor Sizing

The motor is the primary component, so the rest of the system should be built around it. As such, we'll start by talking about it.

## Bike Physics

In my application, I am aiming for a bike that can be driven as if it was an electric motor cycle, ie with a powerful enough motor to accelerate from a stop and maintain a reasonable speed. Others may be looking for more performance, or perhaps less (just a simple assist to help get up hills). Either way, we must start by figuring out how much energy we must exert to move me and the bike.

### Bike Force

To find how much energy it takes to move, assume the bike and rider are one. If we put some energy into that object (whether by pedaling or using a motor), that energy has to go somewhere and will move us. We just need to find out how much energy.

For my application, because I want to accelerate from a stop up to say, 20mph, so I can ride at a reasonable speed on the road. My bike and I also weigh about 185 pounds. Because we're talking about adding energy to our bike, let's find the energy at 0mph and 20mph. Using the formula `E=.5mv^2` (energy [in joules] = .5 * mass [kilograms] * velocity [meters per second] squared), we find the energy in a nomoving bicycle to be 0 J, and a 20mph (8.9m/s), 185 lb (83.9kg) bike to have about 3353 joules. Finding the difference between the two, we know that to make a bike move at 20mph, we must add 3353 joules to it.

Finally, I want to be able to accelerate from 0 to 20mph in 10 seconds. There's a cool unit called the Watt, which represents how fast energy is flowing. We know that it takes 3353 joules to accelerate the bike. If we wanted to accelerate really slowly, we could pump energy in slowly (low wattage), or fast to accelerate fast (high wattage). The nice thing is that the formula for wattage is just `Wattage = Joules / Seconds`. Plugging our numbers in, we get `335W = 3353J/10S`.

Just a note, this is a quite simplified way to work out the math, as it completely ignores friction and air resistance. But, it's a good starting point.

Finall
