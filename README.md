# esp32-water-tank-sensor
This project aims to help you creating a water tank level sensor with off the shelf components. It uses esphome for Home Assistant integration.

# Step 1 : Create OTA switch in HA
Go to HA > Parameters > Devices and services > Input.
Create a new Switch sensor and call it "prevent deep sleep".
Then activate it.

# Step 2 : Add your device to ESPhome
Open your Esphome installation and add a new device, call it "Water tank sensor" or whatever you want.
