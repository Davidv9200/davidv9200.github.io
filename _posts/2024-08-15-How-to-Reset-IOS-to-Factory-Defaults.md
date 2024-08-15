---
layout: post
title: "How to Reset IOS to Factory Defaults"
date: 2024-08-15 11:22:00 -0000
categories: hardware networking
tags: tutorial config
image:
 path: /assets/img/headers/2024-08-15-How-to-Reset-Cisco-IOS-to-Factory-Defaults.webp
---

# How to Reset IOS to Factory Defaults

Factory resetting a network device can be a great move if you're running into connectivity issues, security concerns, or just weird behavior. It wipes everything back to the original settings, which can fix problems and get things running smoothly again. 

## 1. Access the Router
First, you need to connect to your Cisco router or switch. This can be done using a console cable connected to your computer and accessing the device via a terminal emulator (e.g., PuTTY, Tera Term, or HyperTerminal).

## 2. Enter Privileged EXEC Mode
Once you have access to the device, enter privileged EXEC mode by typing:

```sh
enable
```

You might be prompted to enter the enable password.

## 3. Erase the Startup Configuration
To reset the router to factory defaults, you need to erase the startup configuration file. This file contains the saved configuration that the device loads upon startup. To erase it, use the following command:

```sh
write erase
```

or

```sh
erase startup-config
```

## 4. Erase the VLAN Data
If you're working with a switch and want to clear VLAN data, you should also erase the VLAN database: Read why this is a good idea here ; link to post

```sh
delete flash:vlan.dat
```

## 5. Reload the Device
To apply the changes, you need to reload the device. Be aware that this will restart the device and disconnect your session:

```sh
reload
```

You will be prompted to confirm the reload. Type `yes` and press Enter:

```sh
Proceed with reload? [confirm]
```

## 6. Skip Initial Configuration Dialog
After the device reloads, it might enter the initial configuration dialog. If you want to skip this step and go directly to the command prompt, type:

```sh
no
```

or press `Ctrl+C` to exit the setup mode.

## 7. Verify the Reset
After the device has restarted, you can verify that the configuration has been reset by checking the running configuration. Enter the following command:

```sh
show running-config
```

The output should show the default configuration, with no user-defined settings.

## Summary of Commands
Here's a summary of the commands used to reset a Cisco IOS device to factory defaults:

1. Enter privileged EXEC mode:
    ```sh
    enable
    ```

2. Erase the startup configuration:
    ```sh
    write erase
    ```
    or
    ```sh
    erase startup-config
    ```

3. Erase VLAN data (for switches):
    ```sh
    delete flash:vlan.dat
    ```

4. Reload the device:
    ```sh
    reload
    ```

5. Skip initial configuration dialog (optional):
    ```sh
    no
    ```

6. Verify the reset:
    ```sh
    show running-config
    ```

Following these steps will reset your Cisco IOS device to its factory default settings, removing all user configurations and VLAN data if applicable.