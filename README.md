# OPC UA Modeling Tutorial Server

This repository contains an example Server for the OPC UA Modeling Tutorial on
https://opcua.rocks/from-modelling-to-execution-opc-ua-information-model-tutorial/

and the corresponding model:
https://github.com/Pro/opcua-modeling-tutorial/

## Quick start

Currently this is tested on Linux, but should also work on other platforms.

1. Install open62541 as mentioned here: https://open62541.org/doc/current/installing.html
1. Clone this repo: `git clone https://github.com/Pro/opcua-modeling-tutorial-server`
1. `cd opcua-modeling-tutorial-server && mkdir build && cd build`
1. `cmake ..`
1. `make -j`
1. And then start the server: `./src/opcua-modeling-tutorial-server`
1. Connect any OPC UA Client to the server, e.g., UaExpert. `opc.tcp://localhost:4840`