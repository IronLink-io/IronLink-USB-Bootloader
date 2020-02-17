# IronLink USB DFU Bootloader
The default bootloader that is provided with the IronLink boards to allow uploading of firmware via the USB port without the need of a debugger.

## Supported Boards
* [IronLink LoRa 915](https://www.mouser.co.uk/ProductDetail/Altitude-Tech/irpi01-915?qs=sGAEpiMZZMuC4zZxLL0ZTaUbvRfmACZthNrtXxjuUOcXyfvNG%252BLTcQ%3D%3D)
* [IronLink LoRa 868](https://www.mouser.co.uk/ProductDetail/Altitude-Tech/irpi01-868?qs=sGAEpiMZZMuC4zZxLL0ZTaUbvRfmACZtue%252BOs2c8LAt1Uzt0LHNsXw%3D%3D)
* [IronLink NB-IoT Global](https://www.mouser.co.uk/ProductDetail/Altitude-Tech/irpi01-nbiot?qs=sGAEpiMZZMuC4zZxLL0ZTaUbvRfmACZtcPAXt420D1ZphwWR2qPbjA%3D%3D)

## Bootloader Details
The IronLink default bootloader will flash and run applications from the address 0x08008000 which gives the developer 96Kb of application flash for their projects. When the application jumps to the users application in flash all 16Kb of system RAM is available.

Application | Value
------------ | -------------
**User App Flash Address** | 0x08008000
**Total Available Flash** | 128Kb
**Bootloader Flash Size** | 32Kb
**Application Flash Size** | 96Kb
