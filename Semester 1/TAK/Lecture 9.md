## I/O interfaces at a glance
+ Parallel interfaces:
	+ CENTRONICS
	+ ECP
	+ EPP
	+ ...
+ Serial interfaces:
	+ RS - 232C
	+ USB
	+ IEEE 1394
#### Parallel interfaces
**CENTRONICS** - designed by CENTRONICS for printers. Cable length - 2m
A greater distance can be achieved by twisting signal lines with ground lines.
Bus lines at the beginning were only one-way, and in later standards, bidirectional.
+ **EPP - Enhanced Parallel Port**
	+ Parallel, 8-bit, bidirectional interface
	+ Transfer rate up to 2 Mbps
	+ Cable length up to 2m
	+ Up to 64 devices can be connected to one port
+ **ECP - Extended Capabilities Port**
	+ Parallel, 8-bit, bidirectional interface
	+ Transfer rate up to 2 Mbps
	+ Cable length up to 2m
	+ Baud rate changes depending on line conditions
	+ It is designed to work with high-performance printers
#### Serial interfaces

**RS - 232C** - a standard of how devices can be connected
It allows transfers over distances up to 15m at speeds up to 1 Mb/s.
Voltage levels for logic states:
**1** - $-3 \div -15[V]$ 
**1** - $+3 \div +15[V]$
Devices connected via a serial interface are divided into:
+ **DTE (Data Terminal Equipment)** - Data transmission end device
+ **DCE (Data Communication Equipment)** - Data communication device
The RS-232C connection is made using a cable terminated with DB-9 or DB-25 connectors (from the DCE side - male, from the DTE side - female)
**Null Modem - a combination of two DTEs without a modem**

**IEEE 1394 - FireWire** - a serial link standard for high-speed communication and synchronous real-time services
+ Transfer rate: 100, 200, 400, 800, 1600, 3200 Mb/s
+ Number of devices: up to 63 on the bus
+ Bus length: up to 72m (16 sections per 4,5m)
+ Power supply up to 60W
+ Hot plugging
+ 4 or 6-pin connectors
+ Sony uses the name i.Link
+ Texas Instruments uses the name Lynx

**USB - Universal Serial Bus** - Communication interface replacing the old serial and parallel ports. It was developed by Microsoft, Intel, Compaq, IBM and DEC.

Allowable number of external devices - 127

Tranfer:
+ USB 1.1 - 1,5 Mb/s (low speed) 12 Mb/s (full speed)
+ USB 2.0 - 480 Mb/s (Hi Speed)
+ USB 3.0 - 5 Gb/s (Super Speed)
+ USB 3.1 - 10 Gb/s (Super Speed+)
+ USB 3.2 - 20 Gb/s (Super Speed+)

**Plug and Play** and **Hot plugging** compatible
Max. cable length: 3m and 5m

Devices in this standard can be connected to create a network in which devices with different transmission speeds can work.

#### Construction of the USB cable:

| Cable  | Number                      | Signal    | Description               |
| ------ | --------------------------- | --------- | ------------------------- |
| red    | 1                           | VBUS      | power +5V (max 0,9A)      |
| white  | 2                           | D-        | Data transmission Data-   |
| green  | 3                           | D+        | Data transmission Data+   |
| black  | 4 (5 w micro- and mini-USB) | GND       | ground                    |
| violet | 5                           | SSRX-     | Data reception USB 3.0    |
| orange | 6                           | SSRX+     | Data reception USB 3.0    |
| black  | 7                           | GND DRAIN | Ground USB 3.0            |
| yellow | 8                           | SSTX-     | Data transmission USB 3.0 |
| blue   | 9                           | SSTX+     | Data transmission USB 3.0 |
## IrDA
**Infrared Data Association (IrDa) -** wireless serial transmission standard in infrared. It was intended to create a temporary network of portable computers.

**Advantages:**
+ no cable connections
+ electrical insulation of cooperating devices
+ immunity to electromagnetic interference
**Disadvantages:**
+ wavelength: 850-1000 mm
+ transmitting cone 30 deg.
+ receiving cone 15 deg.
+ recommended distance 1m. Greater distance is possible by increasing transmitter power and receiver sensitivity
+ Transfer rate up to 30 Mb/s (synchronous transmission)

#### Bluetooth
**Bluetooth -** short-range wireless communication technology between electronic devices. This is a free standard described in the IEEE 802.15.1 specification. Uses radio waves in the 2.4 GHz band.

**Standard features:**
+ low power consumption
+ low power level
+ low price
+ small range

#### Wi-Fi
**Wi-Fi (Wireless Fidelity) -** a set of standards for constructing wireless computer networks. Wi-Fi is used to build radio local area networks ranging from several to several hundred meters. It is based on IEEE 802.11 recommendations.

The Wi-Fi network operates in the free frequency band from 2400 to 2485 MHz and 5000 MHz.
Wi-Fi is also used to build wide area networks (WAN), allowing users with Wi-Fi compatible devices to access the network wirelessly via hotspots.

#### Satellite link
Type of radio telecommunications link. The connection occurs through a suitable relay station, called a transponder, placed on an artificial satellite of the Earth. Signals to and from the transponder are sent duplex, bi-frequency. We call them uplink and downlink.
Depending on the type, transmission volume and number of active terminals, the satellite can be equipped with several to several hundred transponders depending on the required bandwidth

#### Radio communication station
A set of devices for transmitting or receiving radio signals. Radios are divided into transmitting, receiving and transmitting-receiving.
The range of radio station depends on the transmitter power and receiver sensitivity, antenna parameters, range of waves used, weather, seasons, terrain etc.

#### Line of sight radio line
A system pf equipment for transmitting and receiving analogue and digital radio transmissions. It works in the microwave band, with a horizontal antenna with strongly directional radiation characteristics. It provides bandwidth from a few Mbps to a few Gbps.


## Additional presentation: graphics cards
#### Components
+ **Graphics Processing Unit (GPU)**
	+ A specialized processor designed to accelerate the rendering of images, videos and animations
	+ **Key features:**
		+ Unlike the CPU, the GPU has 1000+ cores (CUDA cores, Stream Processors)
		+ Excels at performing many calculations simultaneously
		+ Highly specialized for mathematical and geometrical computations
		+ Equipped with high-speed VRAM
+ Video memory (VRAM)
+ Motherboard interface
+ Interconnection interface
+ Data Processing Unit (DPU)
+ Network interface
+ Voltage Regulator Module (VRM)
