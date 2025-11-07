RCS-RADAR-CAR (Python Implementation)

This repository contains a Python implementation of an integrated control system
for the Scout Mini mobile platform that fuses GNSS/IMU data and radar
information to achieve safe and accurate path tracking. The system allows you
to configure straight‑line and circular trajectories, visualise the planned
route and radar returns, and control the vehicle via CAN bus.

Features

Vehicle control via CAN – communicates with the Scout Mini using the
CAN 2.0B interface at 500 kbit/s to send linear/rotational velocity
commands, enable control and clear errors
docs.roas.co.kr
.

GNSS/IMU pose reception – receives INSPVAXA messages from the inertial
navigation system over UDP; a configurable activation message triggers the
device to start streaming data.

Radar processing and target tracking – parses ARS40x radar
cluster_general messages to extract distance and radar cross section
(RCS), displays clusters in real time, and applies a one‑dimensional
Kalman filter to track the most significant target. A safety threshold
automatically performs an emergency stop if any target is detected within
1 m of the vehicle.

Path generation – supports generation of back‑and‑forth straight lines
and circular trajectories from geographic coordinates.

Stanley controller – implements a Stanley algorithm for lateral
control, computing steering commands based on the current pose and the
reference path.

Electronic geofence – automatically defines a boundary around the
planned path; if the vehicle leaves this area, the system stops the
vehicle and displays an alert.

PyQt5 user interface – provides interactive controls for selecting
motion mode, entering parameters and starting/stopping control. The GUI
displays the target path, actual vehicle track, radar returns and status
information in real time.

Getting Started

Ensure you have Python 3.11 and the following packages installed:
pyqt5, pyqtgraph, python-can, numpy.

Connect the Scout Mini CAN interface (e.g. can0) and the radar’s CAN
bus, and configure your GNSS/IMU device to stream INSPVAXA messages over
UDP.

Launch the integrated program:

python integrated_car_control.py


Use the UI to select the motion mode (straight line or circle), adjust
parameters and generate a path. Click 开始跟踪 to start the
control loop. The program will handle pose reception, radar processing
and vehicle control automatically.

Repository Structure

integrated_car_control.py – main program combining all functionality.

README_updated.md – this file.

SCOUT MINI用户手册.pdf – reference manual for the Scout Mini chassis.

ARS40X_Technical_Documentation_V 1.8_18.10.2017.pdf – reference for the
ARS40x radar.

Contributing

This project was created as part of a learning exercise. Feel free to fork
and modify the code to suit your own projects. Pull requests are welcome.
