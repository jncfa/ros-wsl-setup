
# (Melodic) ROS on WSL with X11 Forwarding Setup Guide

Description: Step-by-step list of what I did in WSL to get ROS working;

This guide will focus on ROS Melodic on Ubuntu Bionic (18.04), however it should work for other distros (?).

---
## Pre-Requisites:
 - Install WSL and Ubuntu 18.04 (enable it on Windows Features, then install Ubuntu via  Store);
 - Install ROS using the tutorial available on the [wiki](http://wiki.ros.org/melodic/Installation/Ubuntu);
 - On Windows, install OpenSSH Windows Client via [Windows Features](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse);

## X11 Fixes
1. Allow X11 forwarding on Windows by adding these lines on `%userprofile%\.ssh\config`:
    
    ```
    Host localhost
        ForwardAgent yes
        ForwardX11 yes
    ```
2. Append this line to `~/.bashrc`:
    
    ```
    export DISPLAY=localhost:0.0
    ```

## ROS Bugs & Fixes
 - No fixes were needed / found for these bugs: 
   - Unreplicatable bug found on `rqt`, particularly the `rqt_plot` plugin: at first the program was crashing upon resizing the window, but it no longer does it and I cannot replicate it whatsoever (so, problem solved 😅);
   - Small graphic bug on `rqt` plugins: text highlighting was often broken (see image below):    
     ![rqt bug](https://raw.githubusercontent.com/jncfa/ros-wsl-setup/master/rqt_bug.png?token=AE4E2QOS4RHHABSRNH6XUOC7Q36IU "rqt bug")
  
