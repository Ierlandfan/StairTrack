# 🪜 Motion based, real time, Stair Lighting with off the shelf parts!

Lights follow you up or down the stairs in real-time! Easy, fast to built. Esphome based, Flashable from wihtin Home Assistant. Only needs 1 motion sensor. 
Use any kind of motion sensor. Whether it's serial based, bluetooth based, Z-Wave / Zigbee based. As long as it integrates with Home Assistant you are ok. Or make your own, example included.

- Connect the LSC RGBIC+CCTIC Ledstrip to you usb-to-serial device.
- Flash the LSC RGBIC+CCTIC Ledstrip with this code.
Done. 


---

## 💡 What This Does

- Lights up stairs dynamically based on your position
- Home Asistant integration
- Works with various motion or distance sensors (Bluetooth, Z-Wave, Zigbee, etc.) And you can even make your own if you prefer. 
- Using an LSC RGBIC+CCTIC Ledstrip with ESPHome (But you can make your own strip if you prefer) 
- Designed for simplicity, flexibility, and off-the-shelf parts.

## 🔧 What you need
Hardware:

- [LSC RGBIC+CCTIC Ledstrip](https://www.action.com/nl-nl/p/3203632/lsc-smart-connect-ledstrip/) (Action)
- LD2411S or LD2420 or LD2450 [Example](https://www.tinytronics.nl/nl/sensoren/beweging/hi-link-hlk-ld2411s-24ghz-radar-sensor-module-met-bluetooth) (Or without bluetooth, any LDXX wil do, I preferred to use the buetooth version)

  Actually any kind of motion sensor works. Whether it's serial based, bluetooth based, Z-Wave / Zigbee based motion sensor that can integrate with Home Assistant will do.
  I used an ESP32 to connect to the bluetooth of the LD2411 [Using this one](https://www.tinytronics.nl/nl/development-boards/microcontroller-boards/met-wi-fi/seeed-studio-xiao-esp32-c3) (But any will do)

- TTL to USB convert [Example](https://www.tinytronics.nl/nl/communicatie-en-signalen/serieel/usb/ch340-3.3v-5v-ttl-usb-serial-port-adapter) (But any similair will work)
- Soldering iron to solder the four wires to the LSC ledstrip . 

Software
- This Repo
- [Home Assistant](https://www.home-assistant.io/)
- [BK7231GUIFlashTool](https://github.com/openshwprojects/BK7231GUIFlashTool)


## 🔧 How It Works

A motion sensor reports it's distance to Home Assistant.
Home Assistant translates the distance to steps. (In this case 15 steps and 30 CM per step)
LSC ledstrip receives the step and  will light up the corresponding stair step (And dimmed the below and after step) 

Highly customizable. You can even create your own ledstrip with an esp32 and flash it all on one device. The BK7231N in the LSC ledstrip has (afaik) no working software support for bluetooth otherwise it would be even easier. (Without Home Assistant)

## 🔧 FAQ 
- Why not connect the LD2411 to the LSC strip itself you would ask? 
Since I had the 5V version and BK7231N is 3.3V only. So I used the bluetooth part of the LD2411. Did not want to buy another. 
you can buy the 3.3V version of an LDXX and connect it to the BK7231N but using the bluetooth part made it flexible as bonus in the placing of the motion sensor

- Why not connect the esp32 to the serial output of the LD2411?  
You can. No problem. I tested with serial as well. 
 
- Why didn't you? Anything that can receive bluetooth will do? 
The Esp32 is a used to integrate the LD2411 in Home Assistant. You can create some code to intercept the bluetooth on your Home Assitant server but that is to be done for now. 
And using bluetooth you are saving soldering two wires :-) And since I had to power the LD2411 anyway it did not matter. A battery powered zigbee / z-wave based motion sensor is on order. 

## 🔧 Credits:

[DiyYari - LightTrack-PRO](https://github.com/DiyYari/LightTrack-PRO)  Loosely based on his idea of using 1 motion sensor.  
[Twentoer](https://www.twoenter.nl/blog/smarthome/addressable-ledstrip-rgbiccctic-lsc-action-home-assistant) For the idea of using the LSC ledstrip and the flashing part.

[arhein123 in this Home Assistant forum post](https://community.home-assistant.io/t/using-lsc-3203632-1-rgbic-cctic-ledstrip-with-esphome/812822/21?u=twoenter) 
Using his Sound Effect configuration I was able to come up with the logic for the led steering.

[TinyTronics](https://www.tinytronics.nl) (Not afilliated) They are fast , reliable and have a lot of fun things in stock :-)

## 🔧 What next:

Trying to light up the Warm white / Cold white leds instead of using the RGB part of the strip. Just estatic change. Should be a small change. 
