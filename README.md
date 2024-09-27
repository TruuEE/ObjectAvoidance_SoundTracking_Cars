# Marco Polo Car Project

<div align="center">
  <img src="https://github.com/user-attachments/assets/97f2c6d9-bb0e-448a-880e-b288643cb7ce" alt="image">
</div>

This repository contains the source code and instructions for the **Marco Polo Car** project, developed as part of the ECE4375 Embedded Systems course at Vanderbilt University. The project involves setting up a "Marco Polo" game using Freenove 4WD Smart Car Kits, where autonomous predator cars chase a prey car, guided by object avoidance, echolocation, and networking communication.

<div align="center">
  <img src="https://github.com/user-attachments/assets/18becc45-9c53-4834-aa26-7670ee2b3142" alt="image">
</div>

## Table of Contents

- [Introduction](#introduction)
- [Dependencies and Installation](#dependencies-and-installation)
- [Preparing the Cars](#preparing-the-cars)
- [Running the Game](#running-the-game)
- [License](#license)

## Introduction

In this project, two predator cars autonomously navigate through obstacles to find a prey car. The predators use echolocation, guided by microphone arrays, to track the prey, which emits periodic sounds to reveal its location. Key functionalities include:

- **Predator**: Object avoidance, echolocation, and networking communication.
- **Prey**: Command-based control and networking communication.

The project is implemented using Python and hardware from the Freenove 4WD Smart Car Kit.

## Dependencies and Installation

### 1. Installing Python
Ensure your system is updated, and install Python 3:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install autoconf build-essential libtool-bin pkg-config python3-dev
```

### 2. Downloading the Hardware Control Library
Clone the Freenove hardware control library to manage the car's hardware:

```bash
git clone https://github.com/Freenove/Freenove_4WD_Smart_Car_Kit_for_Raspberry_Pi
```

### 3. Installing ZMQ Networking Tools
ZMQ Sockets are used for communication between the prey and predator cars. Install ZMQ using:

```bash
sudo apt install python3-zmq
```

## Preparing the Cars

### 1. Predator Car: Object Avoidance and Echolocation
Set up the predator car by wiring the ultrasonic sensors and servos as shown in the manual. Ensure the camera connector is removed for smoother servo movement. For echolocation, use the SeeedStudio ReSpeaker Mic Array V2.0:

```bash
sudo apt-get update
sudo pip install pyusb click
git clone https://github.com/respeaker/usb_4_mic_array.git
cd usb_4_mic_array
sudo python dfu.py --download 6_channels_firmware.bin
```

### 2. Prey Car
Install the Freenove library and test the buzzer using the following command:

```bash
sudo python Freenove_4WD_Smart_Car_Kit_for_Raspberry_Pi/Code/Server/Buzzer.py
```

## Running the Game

The predator and prey programs are available in this repository. To run them:

### 1. Predator Car
Update the IP address in `FinalProjectSubscriber.py` to match the Prey car’s IP. Then, run:

```bash
sudo python FinalProjectSubscriber.py
```

The predator car will undergo a calibration process, after which it starts moving autonomously, avoiding obstacles and listening for sounds emitted by the prey.

### 2. Prey Car
Run the prey program with:

```bash
python FinalProjectPublisher.py
```

Control the prey car with `w`, `a`, `s`, `d` for movement, and press `b` to emit a sound, signaling the predators.

## License

This project is open-source and available under the [MIT License](LICENSE).
