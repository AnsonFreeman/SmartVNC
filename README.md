# SmartVNC

SmartVNC is a versatile script that facilitates the setup, management, and auto-cleanup of VNC servers with optional noVNC web access. Designed to run effortlessly on Linux systems, SmartVNC automates the process of starting a virtual network computing (VNC) server and optionally a noVNC server, enhancing remote desktop accessibility.

## Features

- **Automatic Display Number Detection**: Auto-detects an available VNC display number if not provided.
- **Password Protection**: Secure your VNC session with a password.
- **Customizable Geometry**: Specify the resolution of the VNC display.
- **Optional Web Access via noVNC**: If a HTTP port is provided, a noVNC server will be started, allowing access via a web browser.
- **Openbox Window Manager**: Utilizes Openbox for managing windows within the VNC session.
- **Auto-Close Feature**: Automatically terminates the VNC and noVNC servers when the main command finishes execution or when no connection is detected.
- **Extensive Cleanup**: Ensures all processes are terminated cleanly on script exit.

## Prerequisites

Before you can run SmartVNC, you need to install the following dependencies on your system:

### For Debian-based distributions (like Ubuntu):

```bash
sudo apt update
sudo apt install xorg xserver-xorg xvfb tigervnc-standalone-server tigervnc-common x11vnc novnc openbox net-tools

```

### For Red Hat-based distributions (like CentOS):

```bash
sudo yum update
sudo yum install xorg-x11-server-Xorg xorg-x11-server-Xvfb tigervnc-server x11vnc novnc openbox net-tools
```

## Usage

To use SmartVNC, you may start the script with various options to control its behavior:

```bash
./smartvnc [options]
```

### Options

- `-d, --display <display_number>`: Set the display number for the VNC server.
- `-P, --password <password>`: Set a custom password for the VNC server.
- `-c, --startup <command>`: Specify a command to run within the VNC session.
- `-o, --openbox_config <path>`: Specify a path to an Openbox configuration file.
- `-g, --geometry <geometry>`: Set the geometry of the VNC display (e.g., 1920x1080).
- `-p, --http-port <port>`: Specify a port number for starting the noVNC server.
- `--auto-close`: Enable auto-closing of the VNC/noVNC servers when the main command finishes.

### Example

Run a VNC server with a custom geometry and password:

```bash
./smartvnc -g 1920x1080 -P yourPassword -c 'firefox' -p 6080
```

This command will start a VNC session running Firefox, accessible via a browser at 
<br>
`http://<server-ip>:6080/vnc_lite.html?scale=true&password=yourPassword`.

## Cleanup

SmartVNC includes robust cleanup mechanisms to ensure no residual processes or files remain after the script exits. This includes killing all related processes and deleting temporary files.

## Contributing

Contributions to SmartVNC are welcome! Please feel free to fork the repository, make your changes, and submit a pull request.

## License

SmartVNC is released under the MIT License. See the LICENSE file in the repository for more details.
