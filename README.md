# homebridge-heatmiser-mk2
## Heatmiser Thermostats Homebridge plugin

This repository is based on https://github.com/iainbullock/homebridge-heatmiser-ib.

This is an Accessory plugin for Nick Farina's Homebridge implementation (https://github.com/nfarina/homebridge)

Based on homebridge-heatmiser by pumamood (https://github.com/pumamood/homebridge-heatmiser), which is in turn based on the version by Thosirl (https://github.com/thosirl/homebridge-heatmiser).

Reads and writes with the Heatmiser are done asynchronously by polling, which makes the plugin faster and less prone to lockups caused by slow Heatmiser responses.

Tested with Heatmiser Wifi accessory, not with Netmonitor.


# Installing Plugin

Requirements:

- Node.js 18+
- Homebridge 1.6+

This plugin is maintained as a repository-only project.


Add to config.json under "accessories" array

Options for "your_model" are: "DT", "DT-E", "PRT", "PRT-E", "PRTHW" (see https://github.com/carlossg/heatmiser-node/blob/master/lib/wifi.js#L40)

The mintemp & maxtemp options set the range on the thermostat faceplate. The target temperature step size is now 1 degree as required by Heatmiser.

The refreshInterval option controls how often the Heatmiser is polled to read/write its parameters (in milliseconds). A sensible default is applied if omitted.

```json
    {
      "accessory": "HeatmiserWifi",
      "ip_address": "your_heatmiserwifi_ip",
      "pin": your_pin,
      "port": 8068,
      "model": "your_model",
      "mintemp": 5,
      "maxtemp": 24,
      "name": "Thermostat",
      "room": "Hall",
      "refreshInterval": 60000
    }

```
