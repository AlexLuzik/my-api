# node-red-contrib-ftp-client

FTP client node for Node-RED.

[![NPM](https://nodei.co/npm/node-red-contrib-ftp-client.png?downloads=true)](https://nodei.co/npm/node-red-contrib-ftp-client/)

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [Example](#example)
- [License](#license)

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

You can configure these operations using input messages and set options such as the filename, local filename, and more.
