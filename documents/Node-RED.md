# Node-RED

Node-RED is an open-source flow-based programming tool with a visual editor that allows you to wire together nodes to create flows. It was originally built as a rapid application development tool for the IoT. A set of powerful input and output nodes are built-in and the Node-RED community is constantly sharing new nodes.

## Installation

### Prerequisites

To install Node-RED locally you will need a supported version of Node.js.

### Installing

`npm install -g --unsafe-perm node-red`
will install Node-RED as a global module along with its dependencies (in Windows under %APPDATA%\npm\node_modules)

### Running

`node-red` starts Node-RED  
`ctrl-c` stops Node-RED  
`.node-red` is the home folder in %HOMEPATH% for the Node-RED configuration for the current user.

### Upgrading Node-RED

If Node-RED was installed as a global npm package, run the following command to upgrade to the latest version:

`npm install -g --unsafe-perm node-red`

### Command-line Usage

`node-red` can take various arguments:

`node-red [-v] [-?] [--settings settings.js] [--port PORT] [--title TITLE] [--safe] [flows.json|projectName]`

| Option          | Description                                               |
| --------------- | --------------------------------------------------------- |
| -p, --port PORT | sets the TCP port the runtime listens on, default is 1880 |
| --safe          | starts Node-RED without starting the flows                |
| -v              | enables verbose output                                    |
