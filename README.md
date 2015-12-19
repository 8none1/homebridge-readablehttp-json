# homebridge-readablehttp-json

Supports http[s] devices on the HomeBridge Platform and provides a readable callback for getting the "On" characteristic to Homekit for URLs which return a simple JSON string containing {"state":true} or {"state":false}.

This is probably only useful for my homebrew home automation.

I have changed the namespace a bit so you can install this alongside the other http plugins without them clashing.

I've also made more of the config optional to keep things a bit tidier for my use.

Thanks to https://github.com/mattharris5.

# Installation

1. Install homebridge using: npm install -g homebridge
2. [YOU CAN't DO THIS YET]  Install this plugin using: npm install -g homebridge-readablehttp-json
2a.  [INSTEAD DO THIS FOR NOW]  Copy these files to a folder on your homebridge machine, and from that folder run "sudo npm link"
3. Update your configuration file. See sample-config.json in this repository for a sample. 

# Configuration

The configuration for this plugin is the same as [homebridge-http](https://github.com/rudders/homebridge-http) but includes an additional method to read the power state of the device. Specify the `readable_url` in your config.js that returns the status of the device as JSON in the following format:

{"state":true}    or    {"state":false}

As mentioned above, this is tweaked for my HA set up, so I don't need some of the config options.

Configuration sample:

 ```
"accessories": [
    {
	"accessory": "Http",
	"name": "Central Heating",
	"on_url": "http://192.168.1.22/set/ch/on",
	"off_url": "http://192.168.1.22/set/ch/on",
	"readable_url": "http://192.168.1.22/get/ch",
	"http_method": "POST",
	"service": "Switch"
    }
]

```
