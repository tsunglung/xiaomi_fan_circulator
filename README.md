# Xiaomi Mijia DC Frequency Conversion Circulating Fan

This is a custom component for home assistant to integrate the Xiaomi Mijia DC Frequency Conversion Circulating Fan.

Please follow the instructions on [Retrieving the Access Token](https://www.home-assistant.io/components/vacuum.xiaomi_miio/#retrieving-the-access-token) to get the API token to use in the configuration.yaml file.

Credits: Thanks to [Rytilahti](https://github.com/rytilahti/python-miio) for all the work.
This repository is forked from [syssi/xiaomi_fan](https://github.com/syssi/xiaomi_fan)

## Features

### Circulating Fan

* Power (on, off)
* Speed levels (Level 1, Level 2, Level 3, Level 4, Level 5)
* Oscillate (on, off)
* Oscillation angle (30, 60, 90, 120)
* Natural mode (on, off)
* Rotate by 7.5 degrees (left, right)
* Child lock (on, off)
* LED brightness (bright, dim, off)
* Attributes
  - model
  - led_brightness
  - buzzer
  - child_lock
  - natural_level
  - oscillate
  - delay_off_countdown
  - speed
  - direct_speed
  - natural_speed
  - angle
  - use_time


## Install

You can install this custom component by adding this repository ([https://github.com/tsunglung/xiaomi_fan_fa1](https://github.com/tsunglung/xiaomi_fan_fa1/)) to [HACS](https://hacs.xyz/) in the settings menu of HACS first. You will find the custom component in the integration menu afterwards, look for 'Xiaomi Mijia DC Frequency Conversion Circulating Fan Integration'. Alternatively, you can install it manually by copying the custom_component folder to your Home Assistant configuration folder.


## Setup

```yaml
# configuration.yaml

fan:
  - platform: xiaomi_fan_fa1
    name: Livingroom Smart DC Fan
    host: 10.8.1.100
    token: abcdefghi9jk1lm8240no3p5qrs6tu7x
```

Configuration variables:
- **host** (*Required*): The IP of your fan.
- **token** (*Required*): The API token of your fan.
- **name** (*Optional*): The name of your fan.
- **model** (*Optional*): The model of your device. Valid values are `zhimi.fan.fa1`. This setting can be used to bypass the device model detection and is recommended if your device isn't always available.

## Platform services

#### Service `fan.set_speed`

Set the fan speed.

| Service data attribute    | Optional | Description                                                                |
|---------------------------|----------|----------------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific fan entity. Else targets all.                       |
| `speed`                   |       no | Fan speed. Valid values are `Level 1`, `Level 2`, `Level 3` and `Level 4` as well as a value between 0 and 100. |

#### Service `fan.oscillate`

Oscillates the fan.

| Service data attribute    | Optional | Description                                                           |
|---------------------------|----------|-----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific fan entity. Else targets all.                  |
| `oscillating`             |       no | Flag to turn on/off oscillation. Valid values are `True` and `False`. |

#### Service `fan.set_direction`

Rotates the fan 5 degrees to the left/right.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific fan entity. Else targets all.                 |
| `direction`               |       no | Rotate the fan 5 degrees. Valid values are `left` and `right`.       |

#### Service `fan.xiaomi_miio_set_oscillation_angle`

Set the oscillation angle. Supported values are 30, 60, 90 and 120 degrees.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |
| `angle`                   |       no | Angle in degrees. Valid values are `30`, `60`, `90` and `120`.       |

#### Service `fan.xiaomi_miio_set_delay_off`

Set the scheduled turn off time. Supported values are 0, 1, 2, 3, 4, 5, 6, 7, 8 hours. When 0 is passed, delay_off is disabled.


| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |
| `delay_off_countdown`     |       no | Time in minutes. Valid values are `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8` hours. |

#### Service `fan.xiaomi_miio_set_natural_mode_on`

Turn the natural mode on.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |

#### Service `fan.xiaomi_miio_set_natural_mode_off`

Turn the natural mode off.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |

#### Service `fan.xiaomi_miio_set_buzzer_on`

Turn the buzzer on.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |

#### Service `fan.xiaomi_miio_set_buzzer_off`

Turn the buzzer off.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |

#### Service `fan.xiaomi_miio_set_child_lock_on`

Turn the child lock on.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |

#### Service `fan.xiaomi_miio_set_child_lock_off`

Turn the child lock off.

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |

#### Service `fan.xiaomi_miio_set_led_brightness`

Set the led brightness. Supported values are 0 (Bright), 1 (Dim), 2 (Off).

| Service data attribute    | Optional | Description                                                          |
|---------------------------|----------|----------------------------------------------------------------------|
| `entity_id`               |      yes | Only act on a specific xiaomi miio entity. Else targets all.         |
| `brightness`              |       no | Brightness, between 0 and 2.                                         |

