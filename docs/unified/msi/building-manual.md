# Building manual

## Intro

This documents describes the procedure for compiling Dasharo firmware
compatible with MSI PRO Z690-A and MSI PRO Z790-P.

## Requirements

* `Ubuntu 20.04/21.04/22.04` as a host OS was tested
* Internet connection
* Docker installed
    - follow [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
    - follow [Post-installation steps for Linux](https://docs.docker.com/engine/install/linux-postinstall/)
* Git, wget, unzip installed

```bash
sudo apt install git unzip wget
```

* UEFIExtract installed
    - this tool is used in the `build.sh` script to extract CPU microcode from
      the original MSI firmware

```bash
sudo apt install wget
wget https://github.com/LongSoft/UEFITool/releases/download/A59/UEFIExtract_NE_A59_linux_x86_64.zip
unzip UEFIExtract_NE_A59_linux_x86_64.zip
sudo cp ./UEFIExtract /usr/local/bin
```

## Procedure

Obtain Dasharo source code:

=== "PRO Z690-A (WIFI) DDR4"
    > Replace the `REVISION` with one of the:
    >
    > - `msi_ms7d25/release` for the latest released version
    > - `msi_ms7d25_vVERSION` (e.g. `msi_ms7d25_v1.1.2`) for the given release

=== "PRO Z690-A (WIFI)"
    > Replace the `REVISION` with one of the:
    >
    > - `msi_ms7d25/release` for the latest released version
    > - `msi_ms7d25_vVERSION` (e.g. `msi_ms7d25_v1.1.2`) for the given release

=== "PRO Z790-P (WIFI) DDR4"
    > Replace the `REVISION` with one of the:
    >
    > - `msi_ms7d25/release` for the latest released version
    > - `msi_ms7e06_vVERSION` (e.g. `msi_ms7e06_v0.9.0`) for the given release

=== "PRO Z790-P (WIFI)"
    > Replace the `REVISION` with one of the:
    >
    > - `msi_ms7d25/release` for the latest released version
    > - `msi_ms7e06_vVERSION` (e.g. `msi_ms7e06_v0.9.0`) for the given release

```bash
git clone https://github.com/Dasharo/coreboot.git -b REVISION
cd coreboot
```

Start the build process:

=== "PRO Z690-A (WIFI) DDR4"
    ```bash
    ./build.sh z690a_ddr4
    ```

    The resulting Dasharo firmware image will be placed at `$PWD/msi_ms7d25_VERSION_ddr4.rom`.

=== "PRO Z690-A (WIFI)"
    ```bash
    ./build.sh z690a_ddr5
    ```

    The resulting Dasharo firmware image will be placed at `$PWD/msi_ms7d25_VERSION_ddr5.rom`.

=== "PRO Z790-P (WIFI) DDR4"
    ```bash
    ./build.sh z790p_ddr4
    ```

    The resulting Dasharo firmware image will be placed at `$PWD/msi_ms7e06_VERSION_ddr4.rom`.

=== "PRO Z790-P (WIFI)"
    ```bash
    ./build.sh z790p_ddr5
    ```

    The resulting Dasharo firmware image will be placed at `$PWD/msi_ms7e06_VERSION_ddr4.rom`.
