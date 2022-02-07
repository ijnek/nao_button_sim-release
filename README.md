# Nao Button Sim

[![Build and Test (foxy)](../../actions/workflows/build_and_test_foxy.yaml/badge.svg)](../../actions/workflows/build_and_test_foxy.yaml)
[![Build and Test (galactic)](../../actions/workflows/build_and_test_galactic.yaml/badge.svg)](../../actions/workflows/build_and_test_galactic.yaml)
[![Build and Test (rolling)](../../actions/workflows/build_and_test_rolling.yaml/badge.svg)](../../actions/workflows/build_and_test_rolling.yaml)

This packages provides a simple way to simulate button presses on the NAO from a command line.
This is useful when you cannot physically press the button on the robot, such as when:
* working with simulated robots
* working with a real robot in a location far away

The package simply converts key presses to [nao_sensor_msgs/msg/Buttons](https://nao-interfaces-docs.readthedocs.io/en/latest/sensor-msgs.html#buttons) and publishes
it on `/sensors/buttons` at the rate specified by the frequency parameter (default: 50Hz)

## Installing 

In your ROS2 workspace,

```
git clone git@github.com:ijnek/nao_button_sim.git src/nao_button_sim
rosdep install --from-paths src
colcon build
```

## Running the Button Simulator

In a new terminal, run:

```
ros2 run nao_button_sim nao_button_sim
```

**If you see your terminal getting spammed**, increase the width of your terminal window, 
or zoom out (Ctrl and -) a couple of times, to ensure the terminal window
is at least 110 characters wide.
Once the spamming stops, kill the node (Ctrl + C), and rerun it.

To simulate a button press, click on a key specified in the assigned keys list below:

```
---------  Assigned Keys  ---------                                 
G - Chest button
C - Left Foot Bumper Left
V - Left Foot Bumper Right
B - Right Foot Bumper Left
N - Right Foot Bumper Right
```

The program provides visual feedback for which buttons are being pressed. The word "Pressed" will show
in the corresponding column, as shown below:

```
---------------------------------------  BUTTON PRESS STATUS  ---------------------------------------

|     Chest (G)     | LFoot BumperL (C) | LFoot BumperR (V) | RFoot BumperL (B) | RFoot BumperR (N) |
=====================================================================================================
|      Pressed      |                   |                   |      Pressed      |                   |
```

Multiple keys can be pressed at the same time.

## Published Topics
 
* `/sensors/buttons` ([nao_sensor_msgs/msg/Buttons](https://nao-interfaces-docs.readthedocs.io/en/latest/sensor-msgs.html#buttons))
 
## Parameters

* `frequency` (int, default=50)
