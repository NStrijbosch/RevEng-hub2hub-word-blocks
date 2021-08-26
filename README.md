# Reverse Engineering the Hub to Hub Word Blocks of the LEGO MINDSTORMS Robot Inventor (51515)

The hub to hub communication blocks exploit the Bluetooth Low Energy (BLE) capabilities of the MINDSTORMS Hubs

The protocol is based on broadcasting data in the advertisement data similar to Beacons. 

When transmitting data using the wordblock: <img src="images/broadcast.svg" alt="transmit block: hub transmit signal signal111 with abcd" style="height:20pt;"/> the hub starts advertising the following data

```
0xFF, 0x03, 0x97, 0x01, 0x1D, 0xC6, 0x73, 0x49, 0x61, 0x62, 0x63, 0x64
  ^     ^     ^     ^     ^     ^     ^     ^     ^
  |     |_____|     |     |_________________|     |_________________
  |     |           |     |                     ASCII string containing transmitted data (number of bytes depends on the length of the transmitted data, the maximum is 23 bytes)
  |     |           |    Signal name encoded as a CRC32 hash
  |     |         Index of the message
  |     Company identifier
  Indicating manufacturer data (notice there is no starting byte indicating the length of the data)
  ```


