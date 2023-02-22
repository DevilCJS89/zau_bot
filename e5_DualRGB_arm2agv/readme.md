## Full calibration of Mobile Manipulator () https://github.com/JorgeFernandes-Git/zau_bot/issues/8
_______________________________

Summary: 
* Using ATOM framework to perform full calibration of a mobile manipulator with two cameras. One on the AGV and other on the end-effector of the manipulator.
* Aims to determine the transformations: 
    * Manipulator arm base w.r.t. the AGV.
    * RGB1 w.r.t. AGV. 
    * RGB2 w.r.t. end-effector.
* The cameras used was a depth astra. 
* The calibration used a total of 76 collections.
* The output is a URDF file with the optimized poses of the sensors.
_______________________________

Launch optimized URDF:

    roslaunch e4_dualrgb_optimized e4_dualrgb_optimized.launch

_______________________________

Evaluate two datasets: ...

_______________________________

## Calibration Results per collection:

_______________________________

## Calibration tree and Transformations:

_______________________________

## Videos:
* Recording bag file: 
* Set initial estimate: 
* Collect data: 
* Run calibration: 
* Evaluation procedure:
_______________________________

## Configure the calibration using the transformations in the bagfile instead of the ones produced by the xacro description:

    rosrun atom_calibration configure_calibration_pkg -n e4_dualrgb_calibration -utf

## Commands:
Launch AGV for calibration:

    roslaunch zau_bot_bringup zau_bot_bringup

Launch teleop to control the AGV through the keyboard:

    roslaunch zau_bot_bringup my_teleop.launch 

Record bag file:

    roslaunch e4_dualrgb_record_bag record_sensor_data.launch

Playback dataset for calibration (2 terminals):

    roslaunch e3_rgb2agv_calibration dataset_playback.launch

    rosrun atom_calibration dataset_playback -json /home/jorge/datasets/e4_dualrgb/dataset.json 

Run calibration (2 terminals):

    roslaunch e0_rgb2ee_calibration calibrate.launch

    rosrun atom_calibration calibrate -json $ATOM_DATASETS/e4_dualrgb/dataset.json -v -rv -si -vo
