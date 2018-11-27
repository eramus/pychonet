# mitsubishi_echonet
A library for interfacing with Mitsubishi HVAC with the Echonet lite protocol
over WiFi adaptors such as the MAC-568IF-E.

It is specifically designed for use with Home Assistant, and its functionality
is limited to HVAC systems, but it could be potentally extended for other
Echonet applications and become a more general purpose library.

Similar implementations seem to be Node JS middleware running on Docker
containers to interface into the MQTT API however this is designed to be used
as a straight up library, no middleware, Node JS or Docker containers needed!


It is designed to work with Python 3.7 out of the box as
that was the environment I was working on.

# Instructions
Simplest way to install is to use pip:
pip install mitsubishi_echonet

# Using the library
There are two files under /bin
'example.py' is an executable Python3 script that will discover your
Mitsubishi HVAC and play with some settings.

'mitsubishi.py' is for use with Home Assistant.
Copy it into your 'custom_components'

In configuration.yaml add the following lines:

climate:
  - platform: mitsubishi
    ip_address: 1.2.3.4

# Help! Home Assistant could not run the module?

When I was playing around with this I had difficulty getting hass.io to install
the library from pip. No idea why, but eventually I found the correct
combination to get it to work as it is supposed to.

However, there is a workaround:

1. Clone the repo
2. Copy the 'mitsubishi_echonet' subfolder directly out of the repo and
into the 'custom_components' directory.
3. Flip the comments on the following lines in mitsubishi.py:

from mitsubishi_echonet import lib_mitsubishi as mit
&#35; from custom_components.mitsubishi_echonet import lib_mitsubishi as mit

Make sure you enable the ECHONET Lite service in the official Mitsubishi App.

Comments and suggestions are welcome!

# Thanks
Thanks to Jeffro Carr who inspired me to write my own native Python ECHONET library for
Home Assistant. Some ideas in his own repo got implemented in my own code. (https://github.com/jethrocarr/echonetlite-hvac-mqtt-service.git)

Also big thanks to Futomi Hatano for open sourcing a high quality and extremely well documented ECHONET Lite library in Node JS that  formed the basis of my reverse engineering efforts: https://github.com/futomi/node-echonet-lite

# Licence
This application is licensed under an MIT license, refer to LICENSE for details.