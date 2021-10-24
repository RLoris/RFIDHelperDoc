# RFIDHelper

![RFIDHelper](./assets/thumbnail.png)

- UE4 Plugin to handle RFID NFC tag operations
- It exposes async nodes to read and write on a compatible NDEF tag (NFC Data exchange format)
- Works only for android phones with NFC and with Android API level 19+
- Can be used in any blueprint

<br>

# Changelog

## v1.1

- Fix freeze when scanning
- Disabling NFC sound when discovering a tag
- NFC continuous state change detection

<br>

![Nodes](./assets/nodeshd.PNG)

[Link to the plugin in the marketplace](https://www.unrealengine.com/marketplace/en-US/product/f5bacbc14f7f42c2b0f1c8032315d4fd)

# Documentation

<br>

# Read

![Read](./assets/node1hd.png)

    Note: A small freeze may occur during reading on older devices

| Node | Inputs | Outputs | Note |
| ---- | ------ | ------- | ---- |
| RFIDReader | void | TagRead(FRFIDReadResult), Error(FRFIDReadResult) | Async node to read tag detected by the android phone |

# Write

![Write](./assets/node2hd.png)

    Note: A small freeze may occur during writing on older devices

| Node | Inputs | Outputs | Note |
| ---- | ------ | ------- | ---- |
| RFIDWriter | Message(FRFIDWriteMessage) |  TagWrite(FRFIDWriteResult), Error(FRFIDWriteResult) | Async node to write the first tag detected by the android phone with the provided message (overwrites all records stored on the tag with the new records)|

# Shutdown

    Note: Call this node when you want to stop the continuous detection of tags for read or write operations

![Shutdown](./assets/node3hd.png)

| Node | Inputs | Outputs | Note |
| ---- | ------ | ------- | ---- |
| ShutdownRFID | void | void | Stops all background processes (Reader and writer), you can call the nodes again if you want to restart the process |