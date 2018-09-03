# micropython-sonoff-basic
Alternate firmware for sonoff-basic written in micropython.



Notes:
- Current use of umqtt.robust.wait_msg() blocks WebREPL.
- Buttons are not yet implemented, mqtt control only.

Working with:
- micropython firmware esp8266-20180511-v1.9.4 on Sonoff Basic
- https://hub.docker.com/_/eclipse-mosquitto/
- https://hub.docker.com/r/homeassistant/home-assistant/

#### home-assistant config.yaml
```yaml
mqtt:
  broker: 10.0.1.5

switch:
  - platform: mqtt
    name: "Sonoff1"
    state_topic: "stat/sonoff1/POWER"
    command_topic: "cmnd/sonoff1/power"
    payload_on: "ON"
    payload_off: "OFF"
    state_on: "ON"
    state_off: "OFF"
    optimistic: false
    qos: 0
    retain: true
```