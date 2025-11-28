# Installation

!!! warning "Hardware Prerequisites"

    Panoptic has been designed and conceived to be executed on a local computer. Many optimization efforts have been made so that the software can run on as many machines as possible; nevertheless, as the number of images increases, a machine with a good processor and at least 16GB of RAM will be recommended for a good user experience.


## With Installation Files (Recommended)

### Installation

This script-based installation allows you to install the correct version of Python, as well as all dependencies to ensure compatibility:

!!! note

    You will be asked during the installation if you wish to install a version for a graphics card. This speeds up image import, which can be long, but will take up more space on your disk.
    It is important to note that this only works with NVidia graphics cards.





=== "Windows"

    An executable is available [at this link](https://github.com/CERES-Sorbonne/Panoptic/blob/main/install/windows/panoptic.exe) and allows you to install and launch Panoptic within a virtual environment.

=== "Linux"

    ```sh
    wget https://raw.githubusercontent.com/CERES-Sorbonne/Panoptic/refs/heads/main/install/start_panoptic_linux.sh -O start_panoptic_linux.sh
    chmod +x start_panoptic_linux.sh
    ./start_panoptic_linux.sh
    ```

=== "macOS"

    ```sh
    curl -O https://raw.githubusercontent.com/CERES-Sorbonne/Panoptic/refs/heads/main/install/start_panoptic_mac.sh
    chmod +x start_panoptic_mac.sh
    ./start_panoptic_mac.sh
    ```

### Launch

=== "Windows (cmd)"

    Simply launch panoptic.exe

=== "Linux"

    ```sh
    ./start_panoptic_linux.sh
    ```

    In addition, the script normally also adds an icon allowing you to launch Panoptic with a click on the icon.


=== "macOS"

    ```sh
    ./start_panoptic_mac.sh
    ```

## With Python

### Installation

If you already have Python installed, with a version greater than or equal to `3.10`, you can simply execute in a terminal:

=== "Windows (cmd)"

    ```bash
    pip install panoptic
    ```

=== "Linux"

    ```sh
    pip3 install panoptic
    ```

=== "macOS"

    ```sh
    pip3 install panoptic
    ```

!!! warning "Mac OS Users"

    Xcode tools need to be installed beforehand for Panoptic to function properly on MacOS.

    These can be installed via:
    `xcode-select --install`

    Furthermore, many dependencies must have precise versions to work on Mac. It is therefore recommended to use the Panoptic installation script provided below.

!!! note

    In all three cases, it is possible to replace `panoptic` in the command with `panoptic[vision]` to install Panoptic directly with the similarity module.


#### Launch

Enter the command `panoptic` in your terminal

### Using a Virtual Environment

Since Python packages can easily conflict depending on versions, it is advisable to install Panoptic in a dedicated Python environment.

=== "Windows (cmd)"

    ```bash
    python -m venv panoptic_env
    panoptic_env\Scripts\activate
    pip install panoptic
    ```

=== "Linux"

    ```sh
    python3 -m venv panoptic_env
    source panoptic_env/bin/activate
    pip3 install panoptic
    ```

=== "macOS"

    ```sh
    python3 -m venv panoptic_env
    source panoptic_env/bin/activate
    pip3 install panoptic
    ```

#### Launch

=== "Windows (cmd)"

    ```bash
    panoptic_env\Scripts\activate
    panoptic
    ```

=== "Linux"

    ```sh
    source panoptic_env/bin/activate
    panoptic
    ```

=== "macOS"

    ```sh
    source panoptic_env/bin/activate
    panoptic
    ```



## Installation with Docker

If you have encountered problems with the classic installation, or if you prefer to use Docker, an image is available. First, you need to:

### Install Docker
- [On MacOS](https://docs.docker.com/desktop/install/mac-install/)
- [On Windows](https://docs.docker.com/desktop/install/windows-install/)
- [On Linux](https://docs.docker.com/desktop/install/linux-install/)


### Option 1: A single folder for images and for Panoptic data:

This implies having created a special folder called "images" within the folder you will specify as input to Panoptic. In the following example, it would therefore be necessary that in the folder: `/path/to/your/folder`, there exists an `images` folder whose full path would consequently be `/path/to/your/folder/images`.

Then, run the following command (with Docker already launched):

```bash
docker run -it -p 8000:8000 -v /path/to/your/folder:/data --name panoptic ceressorbonne/panoptic
```

### Option 2: A folder for images, and a folder for Panoptic data:

```bash
docker run -it -p 8000:8000 \
-v /path/to/your/data:/data \
-v /path/to/your/images:/data/images \
--name panoptic \
ceressorbonne/panoptic
```
