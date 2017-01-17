# Testing cc1350 as Node and Concentrator
Testing communication between two cc1350 based on the original TI examples of dual mode Node and Concentrator. This is a slightly different setup than the original to be a proof of concept for a bunch of nodes collecting sensor information from the ADC and sending it over long range mode sub-GHz to a concentrator that in turn sends BLE Eddystone beacons with the received data.

The node:
* Collects internal temp and ADC from LMT70 hooked up to DIO25
* Transmits and receives acks for 120b sensor packets over 868 MHz 625bps 14dBm
* Can toggle to also send BLE data after pushing a button. Then sends BLE Eddystone URL + TLM beacons with latest received sensor data and sensor adress as part of URL.

The concentrator:
* Receives 120b sensor packets and transmits acks on 868 MHz 625bps 14dBm
* Continously sends BLE Eddystone URL + TLM beacons with:
  * Latest sensor adress as URL
  * Latest received sensor data in TLM
  * Time since latest sensor data was received

## How to setup
1. Clone repo
1. Open CCS and set workspace to the repo directory
1. In CCS click "File" > "Open Projects from File System" and select the repo directory and import projects.
1. Build
1. Debug!

## Todos
* Tidy up sensor controller code.
* Measure current.
* Sleep node heavily for 5 mins between transmissions. Measure current again.
* Pressing button on concentrator makes it send out BLE Eddystone beacon with adress and number of nodes it is tracking instead of temp.
