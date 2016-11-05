I made a few changes to the library to enable an additional pin, when additional power is requested. Wire up your sensors according to this schematic:

![Schematics](https://github.com/dersimn/ArduinoOneWirePullup/raw/pullup_support/docs/Pullup%20for%20DS18B20.png)

and specify the used pins when creating the OneWire object like this:

    OneWire oneWire(ONE_WIRE_BUS, PULLUP_PIN);

Whenever you call the `OneWire::write(uint8_t v, uint8_t power)` method with `power=1` the additional pin will be set to provide more power.  
The [DallasTemperature](https://github.com/milesburton/Arduino-Temperature-Control-Library) library for e.g. does this. If you're using this library you don't need to do more than changing the single line above.