![Atriom logo](/images/atriom-logo.png)

## Getting Started

### Introduction

The Atriom webpack plugin extracts data from the webpack build process and writes a `.dat` file to a user-specified output path. This plugin is intended for use with applications built with the Webpack 5 `ModuleFederationPlugin`.
The generated `.dat` file will contain the following information:

- name and id of the application
- application dependencies
- development dependencies
- optional dependencies
- application remote
- overrides
- consumed modules
- exposed modules

### Prerequisites

- Webpack version 5.31.0 or higher

### Installation

`npm i --save-dev atriom-plugin`

## Usage

Add Atriom plugin and configuration to your `webpack.config.js` file.

### Example

```
const AtriomPlugin = require('atriom-plugin');
const path = require('path');
```

```
plugins: [
    ...
    new AtriomPlugin({
        filename: "ATRIOM",
        outputPath: path.join(__dirname, "../"),
    }),
    ...
]
```
| Key | Description |
| ------------ | ------------------------------------------------------- |
| `filename` | Name of the output file\* |
| `outputPath` | File path for the .dat file generated by the plugin\*\* |

\*The `fileName` in each federated application's `webpack.config.js` file must be identical.

\*\*The `outputPath` for each federated application must point to the same location.  
\
\
Once the plugin has been added and configured correctly, simply run your build script for each federated application:

`webpack --mode production`
\
\
The Atriom plugin will generate a `.dat` file at the specified location, which is ready to be used with the [Atriom Dashboard](http://www.atriomdashboard.io).
