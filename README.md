# ws2812-clock

... with optional MQTT control mechanism.

The MQTT control can be used to add the WS2812 clock as a MQTT switch to Home Assistant e.g.

## Limitations
- Fixed command and state topics (Added as postfix _set_ and _state_ at the end of the configured topic).
Could be changed to support something like %prefix% as in tasmota
- MQTT password needs to be entered in plain text input. However, it will not be printed on serial and displayed only as asterisks later on in the config portal.

## Example configuration
Configuration in config portal:

<img src="https://github.com/Philipp-E/ws2812-clock/blob/media/ConfigPortal.png" width="300">

Entry in configuration.yaml for HomeAssistant:
```yaml
# MQTT WS2812-Clock:
mqtt:
  switch:
    - unique_id: WS2812-Clock
      name: "WS2812-Clock"
      state_topic: "home/office/ws2812-clock/state"
      command_topic: "home/office/ws2812-clock/set"
      payload_on: "CLOCK_ON"
      payload_off: "CLOCK_OFF"
      state_on: "CLOCK_ON"
      state_off: "CLOCK_OFF"
      optimistic: false
      qos: 0
      retain: true
```
