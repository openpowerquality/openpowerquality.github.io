---
layout: userguide
title: Quick Start
---

# 0. Caveat

This quick start refers to our first generation system. We are working on the second generation system and will publish an updated quick start in the near future.

# 1. Obtain an OPQBox

The first step in getting started is to obtain an OPQBox.

We are currently manufacturing OPQBoxes on an as-needed basis.  To obtain cost and availability information, please [contact us](contact.html).

# 2. Create an OPQHub account

Once you have your OPQBox, you are ready to create an account on OPQHub.

1. Visit [http://emilia.ics.hawaii.edu:8194](http://emilia.ics.hawaii.edu:8194).
2. Select the `Sign-Up` button on the home page.
3. Fill out the user information fields. You will use your email address to log into OPQHub.
4. Fill out the alert information fields. When power events occur OPQhub can send you an e-mail, a text message, or both! *
5. Select the `Create OPQHub Account` button.
6. You should now be looking at the device administration page. Continue with step 3.

_* If you would prefer to not get alerts, you can leave wither the alert e-mail field or the SMS number field blank._

# 3. Register your OPQBox

After you have created your account, you can register your OPQBox (or OPQBoxes) with your account.

1. Make sure you are on the [device administration page](http://emilia.hawaii.edu:8194/admin/device).
2. Locate the device id on the underside of your OPQBox.
3. Enter the device id in the field marked `Device Id`.
4. Come up with a key for your device. The key acts as a password to your data. The same key will be needed when configuring your OPQBox.
5. Enter the key in the field marked `Key`.
6. Select the `Add Device` button. This will take you to the device information page.
7. Enter a short description for your device in the `Description` field.
8. Select `Make Data Public` checkbox if you wish to anonymously share your power quality data.
9. Select a square on the map which best represents where you will place your OPQBox. *
10. Select the `Update` button.

_* By zooming in and out on the map, it is possible to select a square that is more accurate or less accurate. This makes it possible to share your power quality data while also remaining anonymous. You might select a square that has you and your neighbors homes in it. Or you might select a square that has your entire neighborhood in it. Play around with the map until you find a square that you are comfortable with._

# 4. OPQBox Configuration

Once you have obtained your OPQBox, you begin the configuration process by providing it with information about your WiFi network and the location of your chosen OPQHub using the provided USB stick.  Once your OPQBox is communicating with the OPQHub, the setup process is complete.

### Edit config.ini
All configuration for the OPQBox is controlled by editing the file `config.ini` on the provided USB stick.

1. Insert the provided USB stick into your computer.
2. Navigate to the USB directory and open `config.ini` using your favorite text editor.
3. Edit the configuration file. The details of the configuration file are provided below.
4. Save the configuration when you are done editing it.
5. Eject the USB drive from your computer.
6. Place the USB drive into the available USB slot on the side your OPQBox.


When you open config.ini, you will see something similar to the following. Note that lines that start with the `#` symbol are comments.
### Example config.ini
    [wifi_config]
    ssid = name_of_your_network
    key = password_for_your_network
    security = network_security_type

    [device_config]
    access_key = key_from_step_3

    # Default values
    opqhub_addr = ws://emilia.ics.hawaii.edu:8194/private/ws
    event_throttle = 3600
    expected_voltage = 120
    voltage_tolerance = 7
    expected_frequency = 60
    frequency_tolerance = 4.2
    heartbeat_interval = 1800

Let us take a look at this file in detail.

##### `ssid = name_of_your_network`
* This stores the name of the wireless network you wish to connect to
* Replace `name_of_your_network` with the name of the wireless network you wish to connect to

##### `key = password_for_your_network`
* This stores the key or password of the wireless network you wish to connect to
* Replace `password_for_your_network` with the correct password/key for the network you wish to connect to

##### `security = network_security_type`
* This stores the type of security the wireless network is using
* Replace `network_security_type` with one of `wep`, `wpa`, or `none`
* Note that `security = network_security_type` also covers `wpa2`

##### `access_key`
* This stores the key used to protect your data and device.
* This should be the same key you entered in step 3.

The rest of the fields under `# Default values` generally do not need to be changed. However they are described here for completeness.

##### `opqhub_addr`
* The web address of the OPQHub you wish to use with your OPQBox.

##### `event_throttle`
* This number throttles the number of events your OPQBox can generate in a given amount of time.
* A value of 3600 means that you will only receive an event once every 3600 seconds (one hour).
* A smaller value means you may receive more power events.

##### `expected_voltage`
* This is the number of volts you expect to be coming into your OPQBox.
* This can be adjusted if you know that your voltage is not the standard 120 Volts.

##### `voltage_tolerance`
* This is a value in Volts that tells the OPQBox to generate a power event when the voltage is outside of `expected_voltage` +/- `voltage_tolerance`.

##### `expected_frequency`
* This value is the frequency in Hertz you expect to be coming into your OPQBox.
* This can be adjusted if you know the frequency is not the standard 60 Hz.

##### `frequency_tolerance`
* This is a value in Hertz that tells the OPQBox to generate a power event when the frequency is outside of `expected_frequency` +/- `frequency_tolerance`.

##### `heartbeat_interval`
* This value specifies how often the OPQBox should send a heartbeat to the OPQHub.
* The value of this field is in seconds.

# 5. Power up OPQBox

1. Place your OPQBox on a flat surface.
2. Make sure the USB drive is inserted into the device.
3. Turn on the device.
4. If you have configured e-mail or text message alerts, you should receive an alert telling you when the device comes online. This should happen within 3 minutes. 
5. If you do not receive an alert (or do not see data in your OPQHub account), then cut power to the device, take out the USB Drive, and check for a log file which should indicate the configuration problem.



