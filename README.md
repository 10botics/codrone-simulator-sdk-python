# Codrone Simulator Python Interface

This Python script, `codrone_simulator.py`, serves as the interface for controlling a simulated drone using Python. It provides a robust API to interact with the [drone simulator](https://github.com/10botics/codrone-simulator), enabling users to test drone functionalities programmatically.

---

## Features

- **Comprehensive Drone Commands**: Includes APIs for movement, rotations, LED control, buzzers, range detection, and more.
- **Customizable Behavior**: Offers methods for custom actions like grabbing, releasing, and teleporting.
- **Simulator Integration**: Communicates seamlessly with the drone simulator over a UDP connection.
- **Extensive Notes Enum**: Defines musical notes for drone buzzer control, enabling creative sound outputs.

## Getting Started
Follow these steps to get started with the Drone Simulator:

### Pre-requisites
Before using the simulator, make sure you have the following installed:
1. Python 3.6+: [Download Python](https://www.python.org/downloads/)
2. Codrone Simulator Package: Install the package via pip through Windows CMD or MAC Terminal
    ```bash
    pip install codrone-simulator
    ```
![image](https://github.com/user-attachments/assets/1c6959f4-a0b8-456a-b108-b75fb3660a62)

3. Installed VS Code or PyCharm: [Download VS Code](https://code.visualstudio.com/download) or [Download PyCharm](https://www.jetbrains.com/pycharm/download/)
4. Install python extensions in VS Code or PyCharm
    - VS Code: [Python Extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

![image](https://github.com/user-attachments/assets/d4fcc94d-a63e-4a37-80b5-8ce558b66455)

- PyCharm: [Pycharm Setup](https://learn.robolink.com/lesson/0-3-pycharm-installation-cde/)
5. Download the Drone Simulator: [Download Latest](https://github.com/10botics/codrone-simulator/releases/latest)
6. Download Hello World Drone Commands File: [HelloWorld python File](https://github.com/10botics/codrone-simulator/blob/main/HelloWorld.py)
---
### Running Simulator
1. Extract downloaded zip file to Desktop Folder
2. Open extracted Folder
3. Run the Drone.exe File

![image](https://github.com/user-attachments/assets/3e4a8ec0-4c17-42ab-935a-66cef9b43cac)

4. Wait for the simulator to open
5. Allow Firewall Access

![image](https://github.com/user-attachments/assets/12fbed66-ff86-4b30-aa56-14cc0cf57293)

6. Select Free Play

![image](https://github.com/user-attachments/assets/bd0d8d5d-c9a6-4a6d-bc5e-2bcafe4b1b20)

---
### Test Hello World Python File to Move Drone
1. Open the [HelloWorld python File](https://github.com/10botics/codrone-simulator/blob/main/HelloWorld.py) in either VS Code or PyCharm
2. Make sure you see this window in the simulator

![image](https://github.com/user-attachments/assets/8973434f-f91e-4903-a16a-b88c335b4e62)

3. Run the Python File and watch your drone takeoff make noise and land
---

## Custom Drone Simulator API
### Extra Drone API
- grab()
   - The drone will grab up an arbitrary grabbable object within the grab range of the drone. The current range of the drone is an 1.1m height capsule with 0.3m radius, with the upper spherical center of the capsule as the center of the drone. Note that only one arbitrary object will be grabbed if there are multiple grabbable object within range. Also, if the drone already grabbed an grabbable object, this command will be ignored.

- release()
   - The drone will release the grabbed object if the drone has grabbed one. The released object will be placed on the drone position with height equal zero(y = 0). If there is no grabbed object, this command will be ignored. Note that this command need to be run before running the land command as the drone with grabbed object will not be able to land.

- reset_position_and_rotation()
   - The drone will be teleported to the initial position and rotation. The initial position and rotation is the position and rotation of the drone when the drone simulator is opened. Note: This Command will not reset the Timer or the score. Only Reset the Drone Position)

- send_message(message):
   - The Drone will send out a message to the console. The message is the inputted string message. The message will be shown in the console of the drone simulator. Note that the message will be shown in the console of the drone simulator, not the python console.

### Extra API
- teleport_to(x, y, z)
   - The x, y and z formed the coordinate of the position that the drone will going to teleport. It is an y-up left-handed coordinate system. The drone will directly teleport to the inputed position drone after the execution of this line. Note that there are boundary set for the teleport range.

- teleport_by(x, y, z)
   - The x, y and z formed the offset translate vector that the drone will going to teleport toward. It is an y-up left-handed coordinate system. The drone will directly teleport toward with the inputed offset after the execution of the line. Note that there are boundary set for the teleport range.

- teleport_yaw_to(yaw)
   - The yaw is the rotation angle that the drone will rotate to. Positive yaw value is clockwise rotation while negative yaw value is anti-clockwise rotation. The unit of the yaw value is in degree. The forward direction(positive z-axis) yaw angle is 0. The drone will directly rotate toward with the input rotation after the execution of the line.

- teleport_yaw_by(yaw)
   - The yaw is the rotation angle offset that the drone will rotate toward. Positive yaw value is clockwise rotation while negative yaw value is anti-clockwise rotation. The unit of the yaw value is in degree. The drone will directly rotate toward the input offset angle with the input rotation after the execution of the line.

- set_restart_pos(x, z)
   - The x and z formed the coordinate of the position that the drone will be teleported to after next restart function is executed. Note that there are boundary set for the restart range.

- set_restart_yaw(yaw)
   - The yaw is the rotation angle that the drone will rotate to after next restart function is executed. Positive yaw value is clockwise rotation while negative yaw value is anti-clockwise rotation. The unit of the yaw value is in degree. The foward direction(positive z-axis) yaw angle is 0.
---