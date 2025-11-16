Add this code to esphome to install

```
# wz-display.yaml
substitutions:
  name: wz-display
  friendly_name: WZ Display
  room: Wohnzimmer
  
esphome:
  name: ${name}
  build_path: ./build/${name}
  name_add_mac_suffix: false
  friendly_name: ${friendly_name}

esp32:
  board: esp32-s3-devkitc-1
  framework:
    type: esp-idf

api:
  encryption:
    key: "yourhomeassistantapikey"

ota:
  - platform: esphome
    password: !secret ota_password

# Wifi Setup
wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  manual_ip:
    static_ip: 192.168.178.53
    gateway: 192.168.178.1
    subnet: 255.255.255.0
    dns1: 192.168.178.1
  fast_connect: true

json:

packages:
  setup:
    url: https://github.com/smogaone/esphome-lvgl/
    files: [device/esp32-s3-touch-lcd-7.yaml,
            addon/time.yaml,
            addon/backlight.yaml,
            addon/network.yaml,
            assets/fonts.yaml,
            assets/icons.yaml,
            assets/images.yaml,
            theme/button.yaml,
            office/sensors.yaml,
            office/lvgl.yaml]
    refresh: 1sec
```
