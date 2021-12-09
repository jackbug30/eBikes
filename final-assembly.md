# Final Assembly

[Home](index) | [Motor size](motor) | [Batteries](batteries) | [Motor mounting](motor-mount) | Final assembly

FInally, final assembly.

## Battery Mounting

The batteries could be mounted in a few different positions, however inside the front frame is advantageous because they are mostly protected in the event of a collision and are centrally located. It was also considered using a front mount basked to hold the batteries, however this would mean longer wire runs to the rear wheel. Large diameter hose clamps are used to hold the batteries to the frame, with foam tape between the battery and the frame to help prevent vibration.

## ESC Mounting

The speed controller is mounted as near the motor as possible.

## Throttle Mounting

The throttle (currently just an RC servo tester) is zip-tied to the handlebars, however a more permanent 3d printed mount is being designed.

## Wiring

The batteries are connected to the speed controller via thick, 12 guage wire and crimp terminals. Bullet connectors are used in the wires between the batteries and speed controller, such that the male terminals are on the battery side. This makes recharging easy; the connectors are simply pulled apart and a battery charger's aligator clips can be attached to the male bullets.

Thinner, 22 guage wire was used to extent the wires from the servo tester to the speed controller.

Zip ties were used to hold the wire to the frame.

## Upgrades

An all-in-one management system is planned. Currently, there is no battery guage, so the batteries will die with little warning. Also, there is no speed display. It would be great to build a simple controller for these with a microcontroller; it could easily detect the battery voltage and convert that to charge percentage. The speed could be figured if a magnet was mounted on one of the wheels, and a hall effect sensor (magnet sensor) on the frame; counting how many times per second the magnet passes the sensor can be converted to RPM, which can in turn obe converted to speed based on the wheel's diameter. Finally, a small microcontroller would likely have enough power remaining to convert a more permanent potentiometer to the proper signal for the speed controller, eliminating the need for the servo tester.
