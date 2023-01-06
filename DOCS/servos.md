# Configuring servos

Before assembling the robot, all servos need to be configured. Because they come with the same pre-configured IDs, once connected on a chain the servos cannot be accessed because of duplicate IDs. Therefore is it very important to update the IDs of all the servos *before* they are mounted on frames and connected with the cables. In addition to IDs we will also change the communication speed and a small amount of other parameters to simplify their management after assembly in the robot.

We use two models of Robotis servos: [XL430-W250](https://emanual.robotis.com/docs/en/dxl/x/xl430-w250/) and [2XL430-W250](https://emanual.robotis.com/docs/en/dxl/x/2xl430-w250/). Logically the two servos have identical control characteristics, with the main difference that 2XL430 has a dual axis construction, behaving as two XL430 servos in one. Most of the control registers are therefore presented in duplicate, one for each axis, with a few notable exceptions that we will highlight in the following instructions.

## Connecting the servos

In order to configure the servos we will use the [DynamixelWizard2](https://emanual.robotis.com/docs/en/software/dynamixel/dynamixel_wizard2/) application provided by Robotis. The application is available for Windows, Mac and Linux operating systems and should be downloaded and installed according to the instructions provided in the link above.

To connect the servos to the computer we recommend using an interface like [U2D2](https://emanual.robotis.com/docs/en/parts/interface/u2d2/) that connects to computers using standard USB ports and provides high-speed Dynamixel ports compatible with all Robotis servos.

> **Note:** <br>
> U2D2 does not provide power to the servos, only data control signals. In order to power the servos being configured you need to use an external power supply and an adapter board that makes that power available over the Dynamixel bus. Our recommendation is to use the [U2D2 Power Hub](https://emanual.robotis.com/docs/en/parts/interface/u2d2_power_hub/) which pairs conveniently with the U2D2 interface. Robotis also has a [Starter Set](http://en.robotis.com/shop_en/item.php?it_id=902-0161-200) that includes the U2D2 interface, the Power Hub and a 5A 12V power supply.

When configuring the servos, you should connect only one at a time, to avoid conflicts with duplicate IDs. Theoretically, once you have configured a servo, you could add a new by daisy-chaining it to the previous one as we're setting IDs above 10 and there will not be duplicates, but frankly there is no advantage for having multiple servos connected at this stage and you should anyway avoid constructing chains of more than 6 servos as you could experience a degradation of communication performance. We recommend connecting one servo for configuration and then removing it before connecting the next servo.

To connect the servos follow the diagram below:

![Connecting Servos](imgs/u2d2_phb_05.jpg)

Servos have two connectors and any of them can be used to connect to the U2D2 interface.

The power supply should be connected to the DC plug on the Power Hub. The servo will indicate that has powered and is initialized successfully by short blinking the LED once. This LED should not be on continuously.

## DynamixelWizard setup

When first using the Dynamixel Wizard you will have to configure several settings like the communication port and the speed. Click the "Options" button in the toolbar:

![Options](imgs/dw-options.png)

This will open the following dialog window:

![Options Dialog](imgs/dw-opt-dialog.png)

In this window we will specify the following:

* **Protocols:** we will only use Protocol 2.0 as both models of servos come pre-configured with this communication protocol. For more details on what this protocol means you can read the excellent [documentation](https://emanual.robotis.com/docs/en/dxl/protocol2/) provided by Robotis.
* **Port:** you should make sure that the port that generated when connecting the U2D2 over the USB is checked. Depending on the platform you can identify the port by simply running DynamixelWizard first without the U2D2 interface connected and then with the interface connected. The additional port that is shown when the interface is connected is the one that should be checked in the dialog.
* **Baudrate:** before configuring a servo the application needs to scan the bus and identify all the servos that are connected. Servos come pre-configured with a communication speed of 57,600 bps, so this speed should be clicked on the dialog. We will configure the servos to work at 2Mbps, so this option should also be selected in the dialog. Other speeds are not necessary and should be deselecting. Selecting additional speeds will increase the time that the application will spend to scan the bus, because it will probe for all IDs in the range (specified a little bit later in the dialog) for all communication speeds. If we are sure that we do not have to work with any other speeds we can exclude them from scanning, thus reducing the amount of time is spend during this process. If you are unsure or you have problems with servos that are not detected during scanning (for instance servos that have been used previously in other projects and were configured with other communication speeds) you can activate additional communication speeds.
* **ID range:** the new servos come with a pre-allocated number 1 for XL430 and 1 and 2 for 2XL430. We will assign IDs in the range 11 through 52 for our robot, so we could enter an interval 0 through 60 in this section to reduce the amount of time spent on scanning the bus. Similar to the comments earlier about the communication speed, if the servos have been previously used and configured with IDs higher than that you would need to extend the range to include them. If unsure, expand the range from 0 to 252 (max ID), although you will see an proportional increase in scanning time.

Once you finished updating the settings, press the "Scan" button. A progress dialog box will be displayed showing all combinations of settings used in scanning. If a servo is detected it will immediately be shown on the left side of the window, together with all the related details.