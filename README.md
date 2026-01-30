<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->

# Subsurface Web UI

A web-based user interface for [Subsurface](https://subsurface-divelog.org).

This project provides a read-only web interface that leverages the existing Subsurface core logic through the [subsurface-cli](https://github.com/subsurface/subsurface) command-line tool.

## Overview

The Subsurface Web UI is a Flask-based web application that serves dive log data through a browser interface. It communicates with the Subsurface CLI tool to access and render dive data, avoiding the need to reimplement the extensive C++ core logic.

## Use Cases

This web UI is designed for two major deployment scenarios:

### Local Use

For individual divers who want to view their dive logs in a web browser:

- **Git repository source**: Point to your local Subsurface git repository (the native cloud storage format)
- **XML file source**: Load dive data from a Subsurface XML or SSRF file

Likely most useful for testing - if you are on your local machine, why wouldn't you just use Subsurface in the first place?

### Cloud Server Use

For hosting dive logs on a server to share with others or access remotely:

- **Bare git repositories**: Serve dive data from bare git repositories on the server
- **Multi-tenant support**: Handle multiple users with separate dive log repositories

This mode is primarily designed for the Subsurace Cloud Storage servers and makes a bunch of assumptions around their design and file system layout. It sits behind the existing authentication setup.

## Requirements

- Python 3.x with Flask
- [Subsurface CLI](https://github.com/subsurface/subsurface) (`subsurface-cli` binary)
- A Subsurface dive log (git repository or XML file)

## Installation

1. Clone this repository
2. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Ensure `subsurface-cli` is available in your PATH or configure its location
4. Copy `cli-config.example.json` to configure your data source

## Configuration

See `config.py` for configuration options and `cli-config.example.json` for CLI configuration.

## License

This project is licensed under the GNU Affero General Public License v3.0 (AGPLv3). See [LICENSE.md](LICENSE.md) for the full license text.

The AGPLv3 ensures that if you run a modified version of this software on a server and let others interact with it, you must make the source code available to them.
