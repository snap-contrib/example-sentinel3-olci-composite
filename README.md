# example-sentinel-3-olci-composite

[![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)

A **development container** is a running [Docker](https://www.docker.com) container with a well-defined tool/runtime stack and its prerequisites. The [VS Code Remote - Containers](https://aka.ms/vscode-remote/download/containers) extension allows you to clone a repository or open any folder mounted into (or already inside) a dev container and take advantage of VS Code's full development feature set.

The well-defined tool/runtime stack in this **VS Code Remote container** is:

- ESA's SNAP EO Toolbox
- SNAP snappy Python bindings
- snapista, a SNAP Python thin layer on top of snappy for creating and running SNAP GPT processing graphs
- Python development support tools such as flake8, black, mypy, etc.
- a Python project that does the SAR calibration of Sentinel-1 GRD data

## Installation

To get started, follow these steps:

1. Install and configure [Docker](https://www.docker.com/get-started) for your operating system.

    **Windows / macOS**:

    1. Install [Docker Desktop for Windows/Mac](https://www.docker.com/products/docker-desktop).

    2. If you are using Windows Subsystem for Linux (WSL) 2 on Windows, to enable the [Windows WSL 2 back-end](https://aka.ms/vscode-remote/containers/docker-wsl2): Right-click on the Docker taskbar item and select **Settings**. Check **Use the WSL 2 based engine** and verify your distribution is enabled under **Resources > WSL Integration**.

    **Linux**:

    1. Follow the [official install instructions for Docker CE/EE for your distribution](https://docs.docker.com/install/#supported-platforms). If you are using Docker Compose, follow the [Docker Compose directions](https://docs.docker.com/compose/install/) as well.

    2. Add your user to the `docker` group by using a terminal to run: `sudo usermod -aG docker $USER`

    3. Sign out and back in again so your changes take effect.

2. Follow the steps in https://github.com/snap-contrib/docker-volume-eo/blob/master/README.md to create a local docker volume with the Sentinel-1 GRD acquisition

3. Install [Visual Studio Code](https://code.visualstudio.com/) 

4. Install the [Remote Development extension pack](https://aka.ms/vscode-remote/download/extension).

5. In Visual Studio Code, run `Remote-Containers: Clone Repository in Container Volume...` from the Command Palette (F1)

6. Add the URL to this git repository: `https://github.com/snap-contrib/example-vscode-remote-snap-sar-calibration.git`

7. Select "Master" and Create New Volume 

8. Wait a few minutes for the build to complete

9. Activate conda env and install the 'sar-calibration' app:
```
conda activate env_snap
python setup.py install
``` 
11. Exploit the Sentinel-3 OLCI RGB composite command line utility or evolve the python project
