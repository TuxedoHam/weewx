# weewx
This is a copy of the weewx.conf file I use with my PanTech PT-WH2900 aka WH65B which is a rebranded FineOff. The data is collected by a RTL SDR dongle with the [WeeWX-SDR](https://github.com/matthewwall/weewx-sdr) module

Added couple bits to do little maths under `StdCalibrate` for the Barometer BMP085 added to Raspberry Pi and added `barometer` correction as not sure if it changes based on temperature, and for `radiation` taken from Lux value.

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
My alterations to `[[Defaults]]` so resaults are shown in metric system.
```
    [[Defaults]]

        # Which language to use for all reports. Not all skins support all languages.
        # You can override this for individual reports.
        lang = en

        # Which unit system to use for all reports. Choices are 'us', 'metric', or 'metricwx'.
        # You can override this for individual reports.
        unit_system = metricwx

        [[[Units]]]

            # Option "unit_system" above sets the general unit system, but overriding specific unit
            # groups is possible. These are popular choices. Uncomment and set as appropriate.
            # NB: The unit is always in the singular. I.e., 'mile_per_hour',
            # NOT 'miles_per_hour'
            [[[[Groups]]]]
                 group_altitude     = meter              # Options are 'foot' or 'meter'
                 group_pressure     = hPa                # Options are 'inHg', 'mmHg', 'mbar', or 'hPa'
                 group_rain         = mm                 # Options are 'inch', 'cm', or 'mm'
                 group_rainrate     = mm_per_hour        # Options are 'inch_per_hour', 'cm_per_hour', or 'mm_per_hour'
                 group_temperature  = degree_C           # Options are 'degree_C', 'degree_F', or 'degree_K'
                 group_speed        = km_per_hour        # Options are 'mile_per_hour', 'km_per_hour', 'knot', 'meter_per_second', or 'beaufort' 
                # The following line is used to keep the above lines indented properly.
                # It can be ignored.
                unused = unused

            # Uncommenting the following section frequently results in more
            # attractive formatting of times and dates, but may not work in
            # your locale.
            [[[[TimeFormats]]]]
                 day        = %H:%M
                 week       = %H:%M on %A
                 month      = %d-%b-%Y %H:%M
                 year       = %d-%b-%Y %H:%M
                 rainyear   = %d-%b-%Y %H:%M
                 current    = %d-%b-%Y %H:%M
                 ephem_day  = %H:%M
                 ephem_year = %d-%b-%Y %H:%M
                # The following line is used to keep the above lines indented properly.
                # It can be ignored.
                unused = unused
```

Added `group_speed` to `[[[[Groups]]]]` as it was not added in the default config
```
                 group_speed        = km_per_hour        # Options are 'mile_per_hour', 'km_per_hour', 'knot', 'meter_per_second', or 'beaufort'.
```

### Work in progress
Get RSSI/SNR/Noise data added to `Sensor Status` on the web page
