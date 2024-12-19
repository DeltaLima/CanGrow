# CanGrow

### Origin: https://git.la10cy.net/DeltaLima/CanGrow
For source code and releases, please go there! :)

![CanGrowLogo](Logo/CanGrow_Logo.png)


An easy to use DIY grow controller firmware (for cannabis).

![Screenshot_WebUI_root.png](Screenshot_WebUI_root.png)
![CanGrow_PCB_Front.png](CanGrow_PCB_Front_small.png)

# WORK IN PROGRESS

## Motivation
I havn't found an already existing grow controller project within the ESP / Arduino Core eco system which 
met my personal requirements. 
Those are an easy DIY, using low cost parts, Arduino Core sourcecode to hack own things together, having a WebUI, grab some Metrics for monitoring, standalone and my very special need that the Hardware should run completely with 12V. 

### Update 14.09.2024 - Code Rewrite v0.2

I took some "summer break" from the project, and had the opportunity to talk to different people about it.
My conclusion at this point is, that the focus of this project is not the Hardware, it came out that it should be the software.
So I decided to completely rewrite the code from 0 - with recycling some parts of it. 
Goal of the Rewrite is that the Firmware becomes more independent of the hardware used. It has to support both ESP8266 and ESP32 
and let the user decide at which pin which output, sensor or whatever will be connected to. Like done in the [Tasmota](https://github.com/arendst/Tasmota) Firmware, I also want to support "Hardware Templates" which come with presets for PCBs like the one I created.

**Checklist for v0.2 Firmware**
- Support ESP8266 and ESP32 
- AsyncWebserver instead ESP8266Webserver
- LittleFS instead of EEPROM()
- deliver static HTML, dynamic Stuff with Javascript
  - (or is there a better way? please tell me!)
- Free configurable outputs
  - Main outputs for Light, Air, Water 
  - Support for Tasmota Wifi Plugs (and others?)
  - No Limitation for Amount of outputs 
  - Light
    - support for I2C 0-10V Dimm control
    - PWM dimm control
  - Air
    - support for I2C 0-10V Dimm control
    - PWM dimm control
    - Support for humidifier, heater (, CO2?)
    - Read Fan RPM
  - Water
    - Usual watering
    - Pump for fertilizer
- Free configurable Inputs
  - Support for various I2C devices
    - All kind of sensors for Temp, Humidity, Moisture, and so on
    - Support for ADCs to connect multiple analoge sensors
  - Support for Analog inputs
    - onboard ones or I2C (ADC)
    - Analog Multiplexer support (like CD4051)
  - Calibrate sensors 
    - define 0% and 100% values
    - Offsets
- MQTT support
- API

  
  
## Old v0.1 Features / ToDo List

- Measure values :white_check_mark:
  - Humidity :white_check_mark:
  - soil moisture :white_check_mark: 
  - temperature :white_check_mark:
  - water level for water tank :white_check_mark:
- LED grow light control (on/off, dimming, max. 12V 50W load ) :white_check_mark:
  - You can of course use a relais as well, if you want to drive 220V lights :white_check_mark:
- fan control (on/off, (PWM?) max 1A) :white_check_mark:
- pump control for automatic watering (max 1A) :large_blue_circle:
- Web UI and REST API for data and controlling :large_blue_circle:
  - simple web ui :white_check_mark:
  - REST API :large_blue_circle:
  - Send notifications with web call (e.g. for mastodon) :red_circle:
  - predefined grow profiles :large_blue_circle:
  - persistent data :white_check_mark:
    - Start of Grow :white_check_mark:
    - day of grow :large_blue_circle:
    - grow profile 
      - watering amount per week :large_blue_circle:
      - light cycle :white_check_mark:
    - wifi settings :white_check_mark:
    - settings in general :white_check_mark:
- Easy to build and use for beginners (i hope so!) :white_check_mark:
  - PCB layout to order from manufacture (jlcpcb or pcbway) :white_check_mark:
  - easy to build up on a perfboard :white_check_mark:
  - easy to etch pcb :white_check_mark:
  - easy to access and modify :white_check_mark:
  - low cost as possible! :white_check_mark:

:white_check_mark: Done - :large_blue_circle: In Progress - :red_circle: ToDo
