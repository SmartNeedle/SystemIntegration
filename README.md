# SystemIntegration

Miro diagram of system architecture: https://miro.com/welcomeonboard/MEpValZOZnhVNVEzejczRWxhb0hpWUJZbVVZQThjS1Qxa0llTnRRdUVpM0ZudG5nc2ROakY0ZzFqemxSRjdQN3wzMDc0NDU3MzQ5OTI1NjQwNzA3?invite_link_id=26421202184

Using https://plantuml.com/sequence-diagram:

![alternative text](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/SmartNeedle/SystemItegration/main/system_integration_diagram.txt)

## Launching Shape-Sensing Needle Node
1. Launch the FBG interrogator node to gather the sensor readings:

For the demo node:
```bash
ros2 launch hyperion_interrogator hyperion_demo.launch.py ip:=<demo IP address of the interrogator> numCH:=<number of FBG channels> numAA:=<number of FBG active areas per channel>
```
For the actual hardware interface node
    
```bash
ros2 launch hyperion_interrogator hyperion_streamer.launch.py ip:=<demo IP address of the interrogator>
```
2. (If connected to hardware) Ensure that the sensorized needle is straight to prepare for sensor calibration
3. Perform sensor calibration by launching the `calibrate_sensors` node

```bash
ros2 run hyperion_interrogator calibrate_sensors --ros-args -r __ns:=/needle
```

4. Launch the (multi-threaded) shape sensing node. (Look at the *ros2_needle_shape_publisher* README for information on the parameters)

```bash
ros2 launch needle_shape_publisher sensorized_shapesensing_needle_decomposed.launch.py needleParamFile:=path/to/needle_params.json numSignals:=200 optimMaxIterations:=15
```
