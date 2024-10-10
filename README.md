# ESP32 Water Tank Level Sensor
This project aims to help you creating a water tank level sensor with off the shelf components. It uses esphome for Home Assistant integration.
The idea is based on hardware from DFrobot :

- Dfrobot Firebeetle 2 ESP32 C6: https://www.dfrobot.com/product-2771.html?tracking=CH2ahHLno922IMb3XFammUzJDnc1pryXEVmuVTHKYGav95g0jDeqjLk90uqz3qqL
- Ultrasonic waterproof sensor: https://www.dfrobot.com/product-1935.html?tracking=CH2ahHLno922IMb3XFammUzJDnc1pryXEVmuVTHKYGav95g0jDeqjLk90uqz3qqL
- PV module (6V - 1A): https://www.dfrobot.com/product-1775.html?tracking=CH2ahHLno922IMb3XFammUzJDnc1pryXEVmuVTHKYGav95g0jDeqjLk90uqz3qqL
- Optional: a SHT21 : https://s.click.aliexpress.com/e/_DF8JNHP
- A 2000mAh LiPo battery: https://s.click.aliexpress.com/e/_DDq0fF7
- PG7 cable glands: https://s.click.aliexpress.com/e/_DDJgjgV 

## Wiring
![Wiring information](https://raw.githubusercontent.com/tomsbasement/esp32-water-tank-sensor/refs/heads/main/wiring.png)

## Step 1 : Create OTA switch in HA
Go to HA > Parameters > Devices and services > Input.
Create a new Switch sensor and call it "Prevent deep sleep".
Then activate it.

## Step 2 : Add your device to ESPhome
Plug your device to your computer with a USB cable while holding the "Boot" button. Once it is plugged in, you can release the button.
Open your Esphome installation and add a new device, call it "Water tank sensor" or whatever you want.
Add it as an ESP32 device but don't install it yet, skip all steps.
Edit the config file and replace it by the one from this repository.
Just keep OTA key and API key so you can replace "CHANGE_ME" placeholders from the config file of this repo.
Save the configuration then close it

## Step 3 : Install your device
Still in ESPhome, click on the three dots in the right corner of your newly created device and choose "Clean Build Files".
Once done, click on "Install" in the same menu. Choose the option "Plug into this computer".
Wait for a few minutes until you have a confirmation the installation was successful.
Pull the USB plug from the device and put it back in to power cycle it.

## Step 4 : Profit
Now, go to Home Assistant, you should be prompted to add your device to your installation.
The device has deep sleep enabled to save energy, so if it becomes unavailable, you just have to plug the USB and put it back in.
Once it is added to HA, go to Parameters > Devices and services > Input and disable the switch.

The ESP32 will poll the temperature, humidity and water height every 5 minutes and then will go to sleep after 30s.
The battery will charge itself with the PV module so your sensor will be self sufficient.
