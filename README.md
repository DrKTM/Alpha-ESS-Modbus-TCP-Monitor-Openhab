# Alpha-ESS-Modbus-TCP-Monitor-Openhab
Communication between Alpha ESS Storion / Smile T10-HV and OpenHab via Modbus TCP protocol

## Prerequisites
ETH cable connected to your Storion / Smile. (Probably could be used WiFi connection)

Fixed IP address of your Storion / Smile.

## Check of connection
1/ Download and run Modbus Tool -> https://www.modbustools.com/download.html

2/ Press F3 to Connection setup and enter your storion/smile IP, port = 502, confirm

3/ Press F8 to Read/Write definition -> setup Slave ID = 85, Address mode Decimal and Address = 0, Quantity = 30, press Apply

4/ You should see first data from your storion/smile
![connection](https://user-images.githubusercontent.com/95654690/191451730-9dfc080d-231e-4094-8a29-e15353971c58.png)

5/ You could check all addresses which you want to use via Alpha Modbus Protocol. [Alpha-Modbus-Protocol_V1.28.pdf](https://github.com/DrKTM/Alpha-ESS-Modbus-TCP-Monitor-Openhab/files/9614615/Alpha-Modbus-Protocol_V1.28.pdf)

## OpenHab (OH3)
1/ Disconnect or close Modbus Tool!

2/ Install Modbus Binding

3/ Create Thing Modbus TCP Slave -> Setup IP address of your storion/smile, port = 502, ID = 85. Thing should be online after creating.

4/ Create Modbus Pooler -> Bridge = Modbus TCP slave, Start = 0, Length = 30, type = Holding register (start = address from Modbus tool, length = quantity). Thing should be online after creating.

5/ Create Modbus Data -> Bridge = Pooler, Read address = decimal address from list Alpha Modbus protocol. (eg. 20) for Voltage of A phase) Thing should be online after creating.

6/ Select Channel tab of created modbus Data and link item to channel Value as number.

Notes> Openhabs Modbus connection does not working if Modbus Tool is running respecively connected! You have to have few poolers, each for one range of modbus addresses. You could use partitions of address from alpha modbus protocol and veryfi it via Modbus tools. Each register item has Modbus Data Thing = a lot of new things.
