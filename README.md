# AdaptCPR

A cheap CPR machine that straps onto a person's chest and does the compressions for them. A motor pushes a round pad down on the chest. You pick the pad for a baby, a child or an adult.

![Full 3D assembly](images/render_full_machine_v06.png)

## Why I made it
CPR machines cost a lot, and most people can't get one. I wanted to see if I could design one that costs under $500 and works for different body sizes.

## What it does
- A motor turns a crank, and the crank pushes a pad up and down. The push is a fixed 56 mm, so it can't go deeper.
- There are three pad sizes: adult (80 mm), child (50 mm) and infant (28 mm).
- Four straps with buckles hold it on, like a seatbelt.
- A big red emergency stop button cuts the motor power right away. No software is involved.
- The controller watches the motor current to stop it if it pushes too hard or gets stuck.
- The head unit on top is for a camera and voice guide. That part comes later and is not in this version.

## How it is meant to be used
1. Strap the machine onto the chest and tighten the four straps.
2. Put on the pad that fits (baby, child or adult).
3. Turn the key switch to ARM and make sure the guard is closed.
4. Send the commands over USB: HOME, then PRESET, then TOUCH, then START. The firmware tells you how far to raise or lower the unit.
5. Press the emergency stop at any time to cut the motor power.

I will test it on a CPR manikin only, never on a real person.

## Where I'm at
The design is done in CAD and the firmware is written. I have not built it yet and nothing has run on a real motor. The firmware only compiles and passes its logic tests on a computer.

## 3D model
- Onshape (view only): https://cad.onshape.com/documents/fa358ed90b8fd5fb3b60ef66/w/35dd953a1cb4b45c5f4f9979/e/284874982c788f843d12aaa8
- `cad/CPR_machine_rig_assembled.step` is the full assembly.
- `cad/parts/` has one `.step` file for each part (45 files). `pod_post` and `pod_lens_bezel` each contain two identical copies.

## Wiring
![Wiring diagram](images/wiring_diagram.png)

There is no custom PCB. It uses ready-made boards: an ESP32, a BTS7960 motor driver and an INA219 current sensor. The diagram is also in `images/wiring_diagram.svg`.

## Firmware
`firmware/cpr_motor/` is the code for the ESP32 (Arduino). It is untested on real hardware.

## Parts list
`bom.csv` has the parts with links and prices. The total is about $497.50 before tax and shipping. Some parts (motor, crank discs, rod, base plate, plywood, wire, magnets) are price estimates.

## Files
- `README.md`: this file
- `bom.csv`: parts list
- `cad/`: STEP files
- `images/`: render and wiring diagram
- `firmware/cpr_motor/`: ESP32 code

## AI help
I used Claude (an AI assistant) to help with research, the CAD scripts, the firmware and the diagrams. I'm building and testing the machine myself, and my journals are in my own words.
