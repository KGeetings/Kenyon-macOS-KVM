# Kenyon MacOS KVM

By: Kenyon Geetings

## Table of Contents

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Installation](#installation)

## Introduction

This is a guide to setting up a macOS VM in QEMU, accelerated by KVM. This guide is based on the [Arch Wiki](https://wiki.archlinux.org/index.php/QEMU#macOS) and [OSX-KVM](https://github.com/kholia/OSX-KVM).

## Requirements

- WSL
  - Open PowerShell as Administrator and run the following command:
    - ```wsl --install```
    - Install Ubuntu from the Microsoft Store (honestly can't remember if this is installed by default with WSL or not)
- VNC Viewer
  - Download and install VNC Viewer from [here](https://www.realvnc.com/en/connect/download/viewer/)

## Installation

- Install this repo, and cd into it from an Ubuntu window
- Instal QEMU and virtualization
  - ```./windows-instal.sh```
  - This will load the QEMU kernel menu, select Virtualization, and make sure your system processor type is selected (probably Intel)
  - Then exit and save that configuration
  - Now is a good time to run the following commands to make sure virtualization is enabled
    - ```kvm-ok```
    - ```cat /sys/module/kvm_intel/parameters/nested```
  - You should get "KVM acceleration can be used" and "Y" respectively
- Install macOS by running the following command:
  - ```./setup.sh```
  - This will run "fetch-macOS-v2.py" and bring you through some options
    - Select the version of macOS you want to install (Ventura is the latest, and probably want you want for XCode)
    - This will also take some time, so go grab a coffee or something:)
- Once "setup.sh" finished, you can now run the following:
  - ```sudo HEADLESS=1 ./basic.sh```
- This will start the VM, and you can connect to it with VNC Viewer
  - Connect to "localhost:5900"
  - Then select the MacOS Installer in OpenCore, and hit enter
- Once the installer is running, select "Disk Utility" and select the biggest drive (64GB) and click "Erase/Format"
  - Format the drive as macOS Extended Journaled (NOT case-sensitive)
  - I chose to name it "Macintosh SSD" but you can name it whatever you want
  - Now select the "Reinstall macOS" and go thorugh the setup screen, selecting the disk you just formatted
- And that should (hopefully) be it. You should now have a working macOS VM!