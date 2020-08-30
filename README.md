# Example Server for the Skills Companion Specification

This example server based on [open62541](https://github.com/open62541/open62541) shows the usage of the
proposed [OPC UA Skills Companion Specification](https://github.com/opcua-skills/skill-nodeset).

In this repository, the provided NodeSet2.xml is compiled into a OPC UA server and the skills are implemented by a simulated execution.
This simulation simply writes to the output console the current skill state.

## Quick start

Currently this is tested on Linux, but should also work on other platforms.

1. Install open62541 as mentioned here: https://open62541.org/doc/current/installing.html
1. Clone this repo: `git clone https://github.com/opcua-skills/skill-nodeset-server.git`
1. `cd skill-nodeset-server && mkdir build && cd build`
1. `cmake ..`
1. `make -j`
1. And then start the server: `./src/nodeset-example-server`
1. Connect any OPC UA Client to the server, e.g., UaExpert. `opc.tcp://localhost:4840`

![UaExpert Screenshot](/tools/uaexpert.png?raw=true "UaExpert Screenshot")