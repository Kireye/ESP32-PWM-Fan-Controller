# ESP32-PWM-Fan-Controller
Description on how to implement a controllable PWM Fan into Home Assistant using ESPHome with an ESP32 board.

To begin with you will have to install ESPHome on the ESP32 board that you are using (in my case a XIAO-ESP-C3 from Seeed Studio).
It is recommended that you are using HTTPS with your Home Assistant server as this makes the installation process much, much easier. For this reason I will not be describing how to install it without using HTTPS

Make sure that you have the ESPHome addon in Home Assistant. If not add it through the addon store.
Now navigate to the ESPHome tab in the menu to the left. It has the icon of a small chip.

Now click on "New device" in the bottom right corner. This will prompt you to enter a name for your new device. Enter a name and press "next".
If ESPHome does not find WiFi credentials, you will now pe prompted to enter those credentials. Also make sure that you have connected a WiFi antenna to your ESP32 board.
After this you might need to perform an extra step to connect the board to WiFi. Go into the WiFi settings on your phone and see if there is a network whose name starts with "esphome". If there is, attempt to connect to this network. You will be taken to a page showing available WiFi networks. Simply click on the one you want your ESP32 board to connect to and type in the password and click "Connect".

Now make sure that your ESP32 board is connected to your computer via a USB cable.
A window titled "Installation" should now be visible. Simply click "Connect" to begin installing ESPHome onto your ESP32 board. A loading icon should now appear on your screen. The installation will take several minutes, so just be patient and don't click anything.

Now there should be a device visible in the ESPHome menu with the name that you entered earlier. Click the "Edit" button on this device. This will open the .yaml configuration file of your device.
The easiest way of continuing is to simply copy the layout of the .yaml file that I used. This can be found on this GitHub page as "esphome-copy-from-here.yaml".

IMPORTANT: DO NOT COPY THE ENTIRE FILE. ONLY "#FAN OUTPUT" AND BELLOW SHOULD BE COPIED AS OTHERWISE YOUR FILE WILL NOT FUNCTION

Also change "name:" under "# Fan configuration" to the name you want your fan to have. Also change "name:" under "# Tachometer pulse" to the name you want your RPM meter to have.
Now click "save" in the top right, and "install", also in the top right, and then the top option "Wirelessly" and wait for your .yaml fille to be uploaded to your ESP32 board.

You should now find two devices in the Home Assistan dashboard. One a fan and one a pulse meter both with the respective names that you entered in the .yaml file.

Now you need to wire up your fan and your ESP32 board if you have not already done so. Please follow the document "ESPHome PWM Fan.pdf" found on this GitHub page for how to do this.
I also recommend unplugging the power from the board while you are connecting wires to it so that if you connect something incorrectly you do not fry your board.

Once everything has been wired correctly, simply plug in power to your board again and you should be able to control the fan as well as see its RPM in Home Assistant.
A problem I ran into here is that there were multiple fans added to the Home Assistant dashboard and I used the wrong one and believed that something was broken when it was not. If this happens just control which fan device is the correct one and then delete the other one. This can be done by clicking on the device in the Home Assistan dashboard, clicking the three dots in the top right corner, clicking "device information", clicking "ESPHome" under "Device information", clicking the 3 dots to the right of the devices name that you wish to delete, and deleting it.

Now you should have a functioning way of controlling the speed of your fan as well as reading its RPM.

Useful resources:
esphome.io
