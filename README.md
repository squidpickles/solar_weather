# ESPHome config for Solar Weather Station

This is an ESPHome configuration file for the solar weather station described at https://www.instructables.com/Solar-Powered-WiFi-Weather-Station-V30/

It's based in large part on the configuration at https://github.com/hugokernel/esphome-weather-station/blob/master/weatherstation.yaml, but modified to work with the pinouts and components from the station above.

I removed some of the on-device calculated output, because I tend to use this with a pretty capable Prometheus/Grafana setup, and tend to prefer to do aggregation there instead.

Note that the wind direction in particular will likely need tuning for your particular installation direction and setup. This config outputs the raw ADC and resistance values, so it shouldn't be too hard to collect ranges and update your config appropriately. (I may move this to Grafana as well at some point, and stop doing it on-device.)

## Deployment
Copy `secrets.yaml.sample` to `secrets.yaml`, and fill in values for everything based on your setup.

If you don't have esphome installed, visit 
https://esphome.io/guides/getting_started_command_line.html

Now you can run
```
esphome run solar_weather.yaml
```
with a USB cable plugged into the device. It should flash the board and restart with logs.
