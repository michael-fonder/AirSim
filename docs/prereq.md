# Prerequisites

## What hardware do you need?
### Computer
A good decent desktop or a laptop that has a GPU with at least 4GB of RAM, 32GB of RAM on the machine and a SSD. Large environments in Unreal requires a lot more RAM and a beefy GPU card. The typical computer hardware we use for the development purposes usually have 6 to 12 cores and a graphics card such as NVidia TitanX or NVidia GTX 1080 with 32GB to 64GB RAM and dual SSDs.

### RC Transmitter and Receiver
This is the remote control that you usually use for real RC vehicles such as quadrotors. Our favorite is [FrSky Taranis X9D Plus](https://hobbyking.com/en_us/frsky-2-4ghz-accst-taranis-x9d-plus-and-x8r-combo-digital-telemetry-radio-system-mode-2.html) because it has built-in USB ports. 

[Alternative to RC](docs/sitl.md)

### Flight controller
Our favorite flight controller is [Pixhawk](https://store.3dr.com/products/3dr-pixhawk).  You can also use other variants such as Pixfalcon, or the new Pixhawk Mini; however, we haven't tested them yet. In theory, you should be able to use any flight controller that supports MavLink protocol.

[Why do you need flight controller and alternatives](docs/why_flightcontroller.md)

## Setup steps
1. Make sure your RC reciever is bound with its RC transmitter. Connect the RC trasmitter to the flight controller's RC port.
2. Download [QGroundControl](http://qgroundcontrol.com/), launch it and connect your flight controller to the USB port.
3. Install the PX4 firmware v1.4.4 from [github](https://github.com/PX4/Firmware/releases/tag/v1.4.4). The later releases have a bug that we are working with PX4 team to fix.
4. In QGroundControl, configure your Pixhawk for HIL simulation by selecting the HIL Quadrocopter X airframe.  After PX4 reboots, check that "HIL Quadrocopter X" is indeed selected. You might also want to use QGroundControl to calibrate your RC and set up Flight Mode switch among other things (see below) so everything is green.

## Using the Remote Control
When using hardware-in-loop mode, you can use remote controls such as Fly Sky, Spektrum etc.
1. Connect the receiver for your remote control to the Pixhawk board. Make sure your remote control is bound to that receiver.
2. In QGroundControl, go to Radio tab and calibrate (make sure, remote control is on and the receiver is showing the indicator for the binding). 
3. Go to the Flight Mode tab and chose one of the remote control switches as "Mode Channel". Then set (for example) Stabilized and Attitude flight modes for two positions of the switch.
4. Go to the Tuning section of QGroundControl and set appropriate values. For example, for Fly Sky's FS-TH9X remote control, following settings gives more realistic feel: Hover Throttle = mid+1 mark, Roll and pitch sensetivity = mid-3 mark, Altitude and position control sensitivity = mid-2 mark.
5. You can usually arm the vehicle by lowering and bringing two sticks of RC together (you don't need QGroundControl after the initial setup). Now you can use RC to fly in the simulator. Typically the Altitude mode gives better experience for beginners because this mode lets the autopilot automatically maintain an altitude when the throttle stick is approximately in the middle.