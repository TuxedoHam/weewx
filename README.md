# weewx
This is a copy of the weewx.conf file I use with my PanTech PT-WH2900 aka WH65B which is a rebranded FineOff. The data is collected by a RTL SDR dongle with the [WeeWX-SDR](https://github.com/matthewwall/weewx-sdr) module

Added couple bits to do little maths under `StdCalibrate` for the Barometer BMP085 added to Raspberry Pi, and for Radiation take from Lux value.

```
[StdCalibrate]
    [[Corrections]]
        # For each type, an arbitrary calibration expression can be given.
        # It should be in the units defined in the StdConvert section.
        # Example:
        foo = foo + 0.2
        barometer = barometer + (outTemp-32) * 0.0091
        radiation = light * 0.007893
```

### Work in progress
Get RSSI/SNR/Noise data added to `Sensor Status` on the web page
