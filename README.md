# aqua_illumination-ha
Home Assistant Custom Component Connector for Aqua Illumination Products

Code initially written by [@mcclown](https://github.com/mcclown)  https://github.com/mcclown/home-assistant-custom-components

Cleaning it up a bit for newer Home Assitant API and HACS integration


### AquaIllumination Lights

Support for a range of aquarium lights, from AquaIllumination.

Based on top of one of a python modules I wrote, [AquaIPy](https://github.com/mcclown/AquaIPy). There is no documented API for AquaIllumination lights, so this has all had to be reverse engineered. Beta quality component, but still its use is at your own risk.

A brief rundown of features/caveats:

* This component implements 3 different types of platforms, for each light. A schedule enabled switch, a light for each channel and a sensor for each channel.
* Each individual light channel appears as a different light entity.
* Each individual light channel also has a corresponding sensor entity, with the brightness level. This is useful for graphing the light channel levels.
* It is possible to turn off the "scheduled mode" for the light but if it isn't turned off, then light brightness changes will appear for a few seconds then change back to the normal schedule.
* Support is only for the HD range of lights. No support for earlier models yet.
* No support for setting more than one channel at once.
* No support for increasing the channels to over 100% (the HD range). Although a schedule can still set values over 100%.

A sample configuration is shown below. This adds a light entity for each of the colour channels called <name>_<channel name>.

```YAML
aqua_illumination:
  - host: 192.168.1.100
    name: sump ai
  - host: 192.168.1.101
    name: dt ai
```
