# Reverse Engineering the Hub to Hub Word Blocks of the LEGO MINDSTORMS Robot Inventor (51515)

The hub to hub communication blocks exploit the Bluetooth Low Energy (BLE) capabilities of the MINDSTORMS Hubs

The protocol is based on broadcasting data in the advertisement data similar to Beacons. 

When a hub is sending a message using the wordblock `hub transmit signal AA with Hello` consist of the following advertisment data:

```
0xFF, 0x03, 0x97, 0x01, 0xXX, 0xXX, 0xXX, 0xXX, 0xXX, 0xXX, ....
  ^     ^     ^     ^     ^     ^     ^     ^     ^
  |     |_____|     |     |_________________|     |_________________
  |     |           |     |                     Transmitted data (varying number of bytes)
  |     |           |    4 Bytes encoding the signal name
  |     |         Index of the message
  |     Company identifier
  Indicating manufacturer data (notice there is no starting byte indicating the length of the data)
  ```