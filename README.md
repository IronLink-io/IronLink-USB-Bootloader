# IronLink USB DFU Bootloader
The default bootloader that is provided with the IronLink boards to allow uploading of firmware via the USB port without the need of a debugger.

## Supported Boards
* [IronLink LoRa 915](https://www.mouser.co.uk/ProductDetail/Altitude-Tech/irpi01-915?qs=sGAEpiMZZMuC4zZxLL0ZTaUbvRfmACZthNrtXxjuUOcXyfvNG%252BLTcQ%3D%3D)
* [IronLink LoRa 868](https://www.mouser.co.uk/ProductDetail/Altitude-Tech/irpi01-868?qs=sGAEpiMZZMuC4zZxLL0ZTaUbvRfmACZtue%252BOs2c8LAt1Uzt0LHNsXw%3D%3D)
* [IronLink NB-IoT Global](https://www.mouser.co.uk/ProductDetail/Altitude-Tech/irpi01-nbiot?qs=sGAEpiMZZMuC4zZxLL0ZTaUbvRfmACZtcPAXt420D1ZphwWR2qPbjA%3D%3D)

## Entering Bootloader Mode
The IronLink bootloader can be entered through a jump in software or by connecting **GPIO1** to **GND**. If GPIO1 is connected to GND while the device is powering on it will enter bootloader mode and a DFU device will become available via USB.

![DfuSe Flashing Software](https://github.com/IronLink-io/ironlink-usb-bootloader-setup/blob/master/images/IronLink_Boot.jpg)

## Bootloader Details
The IronLink default bootloader will flash and run applications from the address 0x08008000 which gives the developer 96Kb of application flash for their projects. When the application jumps to the users application in flash all 16Kb of system RAM is available.

Parameter | Value
------------ | -------------
**User App Flash Address** | 0x08008000
**Total Available Flash** | 128Kb
**Bootloader Flash Size** | 32Kb
**Application Flash Size** | 96Kb

## Uploading Firmware using the Bootloader
Your application must be in DFU format in order to upload it to the IronLink. In the [examples](/examples) directory of this repository you will find a number of example programs in the DFU format that can be used to test the IronLink.

1. Download and install the ST DfuSe software which will be used to flash programs onto the IronLink. https://www.st.com/en/development-tools/stsw-stm32080.html

2. Open the application **DfuSeDemo**. If the IronLink is connected correctly you will see a device called "STM Device in DFU Mode" with 64 sectors of memory.

![DfuSe Flashing Software](https://github.com/IronLink-io/ironlink-usb-bootloader-setup/blob/master/images/DfuSe_Application.png)

3. Next click "Choose..." and select the DFU files that you wish to upload onto the IronLink

![DfuSe Flashing Software](https://github.com/IronLink-io/ironlink-usb-bootloader-setup/blob/master/images/DfuSe_Choose.png)

4. Finally click on upgrade and the DFU firmware file should be uploaded to the board. Reboot the board and the new firmware should now execute on the board.

![DfuSe Flashing Software](https://github.com/IronLink-io/ironlink-usb-bootloader-setup/blob/master/images/DfuSe_Upgrade.png)

## DFU Example Programs

Files | Description
------------ | -------------
[usb serial systick.dfu](examples/usb%20serial%20systick.dfu) | Prints the current value of the systick over the USB serial.
