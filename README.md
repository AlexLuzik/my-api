# node-red-contrib-ftp-client

FTP client node for Node-RED.

[![NPM](https://nodei.co/npm/node-red-contrib-ftp-client.png?downloads=true)](https://nodei.co/npm/node-red-contrib-ftp-client/)

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Example](#example)

## Overview

The `node-red-contrib-ftp-client` package is a Node-RED node that allows you to interact with FTP servers. With this package, you can perform various operations like listing files, getting files, putting files, appending to files, deleting files, and creating directories on a remote FTP server.

## Installation

To use this package, you need to have Node-RED installed. If you haven't already, you can install it from [Node-RED's website](http://nodered.org).

Once Node-RED is installed, you can install `node-red-contrib-ftp-client` using npm:

```shell
npm install node-red-contrib-ftp-client
```

After installation, restart your Node-RED instance, and the FTP nodes will be available in the Node-RED palette for use.

## Usage

`node-red-contrib-ftp-client includes the following modules:
### FTP Node
The FTP node provides the following operations:
* LIST: List files and folders on a remote FTP server.
* GET: Download a file from the remote server.
* PUT: Upload a file to the remote server.
* APPEND: Append data to an existing file on the remote server.
* DELETE: Delete a file on the remote server.
* MKDIR: Create a directory on the remote server.

Inputs

* msg.operation (string): Type of the operation. Allows 'LIST', 'GET', 'PUT', 'APPEND', 'DELETE' and 'MKDIR'. Default: 'LIST'
* msg.host (string): The hostname or IP address of the FTP server. Default: 'localhost'
* msg.port integer: The port of the FTP server. Default: 21
* msg.secure (mixed): Set to true for both control and data connection encryption, 'control' for control connection encryption only, or 'implicit' for implicitly encrypted control connection (this mode is deprecated in modern times, but usually uses port 990) Default: false
* msg.secureOptions (object): Additional options to be passed to tls.connect(). Default: (none)
* msg.user (string): Username for authentication. Default: 'anonymous'
* msg.password (string): Password for authentication. Default: 'anonymous@'
* msg.connTimeout (integer): How long (in milliseconds) to wait for the control connection to be established. Default: 10000
* sg.pasvTimeout (integer): How long (in milliseconds) to wait for a PASV data connection to be established. Default: 10000
* msg.keepalive (integer): How often (in milliseconds) to send a 'dummy' (NOOP) command to keep the connection alive. Default: 10000
* msg.filename (string): Path/name of the file on the remote FTP server.
* msg.localFilename (string) | (buffer): Path/name of the file on the local machine. Default the same as filename

Outputs

1. Standard output (LIST):
    msg.payload (array):
        Array of the file/folders in the user's default FTP folder

2. Standard output (GET, PUT, APPEND, DELETE and MKDIR):
    msg.payload (string):
        Message that processing is complete.

3. Standard error:
    msg.payload (string): Error message.
        You can configure these operations using input messages and set options such as the filename, local filename, and more.

## Example

Here's an example flow demonstrating how to use the FTP node to delete a file from a remote FTP server:

```json
[{"id":"ea12685a5ea07fc8","type":"debug","z":"9c66d804bff1630b","name":"debug 1","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"true","targetType":"full","statusVal":"","statusType":"auto","x":360,"y":100,"wires":[]},{"id":"0f119f317f8339c0","type":"inject","z":"9c66d804bff1630b","name":"","props":[{"p":"host","v":"localhost","vt":"str"},{"p":"port","v":"21","vt":"str"},{"p":"user","v":"luzik","vt":"str"},{"p":"password","v":"111","vt":"str"},{"p":"operation","v":"DELETE","vt":"str"},{"p":"filename","v":"DiscordSetup.exe","vt":"str"}],"repeat":"","crontab":"","once":false,"onceDelay":0.1,"topic":"","x":100,"y":100,"wires":[["c15ef24c2beb93de"]]},{"id":"c15ef24c2beb93de","type":"ftp","z":"9c66d804bff1630b","name":"","x":230,"y":100,"wires":[["ea12685a5ea07fc8"]]}]
```

