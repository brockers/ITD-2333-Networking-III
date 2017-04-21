## Serial Connectivity

There are two sides for a serial conneciton.  The dummy side (DTE) and the smart side (DCE).  The smart side will need a clockrate assigned to it so the serial line knows what speed to use for communication.  Clockrates should NOT be done on the dummy side.

* DTE Data Terminal Equipment (dumb side)
* DCE Data Communications Equipment (modem/clock)
* interface Serial 2/0
* clock rate 56000
* ip address 192.168.1.1 255.255.255.0
* no shutdown