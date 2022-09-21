# Alpha-ESS-Modbus-TCP-Monitor-Openhab
Communication between Alpha ESS Storion / Smile T10-HV and OpenHab via Modbus TCP protocol

## Prerequisites
ETH cable connected to your Storion / Smile. (Probably could be used WiFi connection)
Fix IP address of your Storion / Smile.

## Check of connection
1/ Download and run Modbus Pool - https://www.modbustools.com/download.html
2/ Press F3 to Connection setup and enter your storion/smile IP, confirm
3/ Press F8 to Read/Write definition and setup Slave ID = 85, Address mode Decimal and Address = 0, Quantity = 30
4/ You should see first data from your storion/smile
