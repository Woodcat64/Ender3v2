# Ender3v2 Klipper Config Files and Home Assistant Moonraker integration

## Creality v4.2.2 board using display port UART to comunicate with Raspberry Pi3+

![BinMakeMenuConfig](https://user-images.githubusercontent.com/50119854/140626327-e5875e38-2fc2-4e43-9f97-6341aff2be53.png)
![DisablingSerialConsole](https://user-images.githubusercontent.com/50119854/140626331-bd5ec515-b8d0-44c5-b7d2-8bf3cbc69f21.png)

## Home Assistant Moonraker integration

Based on:

https://github.com/denkyem/home-assistant-moonraker

https://github.com/mSarheed/home-assistant-moonraker

https://github.com/Arksine/moonraker/blob/master/docs/example-home-assistant.yaml

https://moonraker.readthedocs.io/en/latest/web_api/#printer-status



1. Create directory `packages` in your Home Assistant `config/` directory

2. Rename moonraker -public.yaml to moonraker.yaml and move it to `packages/` directory

3. Edit moonraker.yaml. Change 192.168.x.x:7125 to your Moonraker's API IP address

4. Put folowing in configuration.yaml

```
homeassistant:
  packages:
    moonraker: !include packages/moonraker.yaml
```       

If rest sensors are not created check that you have access Moonraker's API in your browser. (Again change ip address accordingly).

http://192.168.x.x:7125/printer/objects/query?heater_bed&extruder&print_stats&toolhead&display_status&virtual_sdcard&gcode_move&filament_switch_sensor%20Filament%22


## Home Assistant Dashboard example

![e3v2_ha](https://user-images.githubusercontent.com/50119854/168455933-99bec194-e86b-4444-9ba7-df19a433c92e.png)

Cards used:

column 1: entities card with custom:love-lock-card, entities card, custom:bar-card

column 2: glance card, entity card, custom:bar-card, entities card, button cards in horizontal-stack card with custom:love-lock-card

column 3: picture-entity card, picture-entity card with glance card

column 4: entities card


Also vertical-stack cards are used to keep columns together.

Example [Dashboard_Printer_tab.yaml](https://github.com/Woodcat64/Ender3v2/blob/main/Dashboard_Printer_tab.yaml) file is above

