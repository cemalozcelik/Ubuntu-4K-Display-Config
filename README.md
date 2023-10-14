# Custom Xorg Configuration for 4K Monitor

## Overview

This repository provides a basic guide on how to create a custom Xorg configuration file to support a 4K monitor on an Ubuntu system. The instructions involve creating a new configuration file and adding the necessary sections for the monitor and screen settings.

## Prerequisites

- Basic understanding of the Linux command line.
- A 4K monitor connected to your Ubuntu system.

## Instructions

1. **Create the Xorg Configuration Directory**

    ```bash
    sudo mkdir /etc/X11/xorg.conf.d
    ```

2. **Create a New Configuration File**

    ```bash
    sudo nano /etc/X11/xorg.conf.d/20-custom.conf
    ```

3. **Add Configuration Settings**

    Copy and paste the following configuration into the file `/etc/X11/xorg.conf.d/20-custom.conf`:

    ```plaintext
    Section "Monitor"
        Identifier "Monitor0"
        Modeline "3840x2160_60.00" 712.75 3840 4160 4576 5312 2160 2163 2168 2237 -hsync +vsync
        Option "PreferredMode" "3840x2160_60.00"
    EndSection

    Section "Screen"
        Identifier "Screen0"
        Monitor "Monitor0"
        DefaultDepth 24
        SubSection "Display"
            Depth 24
            Modes "3840x2160_60.00"
        EndSubSection
    EndSection
    ```

4. **Save and Exit**

    Press `Ctrl + X`, then `Y` to confirm changes, and finally `Enter` to exit.

5. **Restart Xorg or Reboot**

    ```bash
    sudo systemctl restart gdm
    ```

    or

    ```bash
    sudo service lightdm restart
    ```

## Notes

- Replace the modeline with the appropriate values for your monitor. Refer to your monitor's documentation for accurate details.
- Use caution when editing configuration files, as incorrect settings may lead to issues.
