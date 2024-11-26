# Codrone Simulator Python Interface

This Python script, `codrone_simulator.py`, serves as the interface for controlling a simulated drone using Python. It provides a robust API to interact with the [drone simulator](https://github.com/10botics/codrone-simulator), enabling users to test drone functionalities programmatically.

---

## Features

- **Comprehensive Drone Commands**: Includes APIs for movement, rotations, LED control, buzzers, range detection, and more.
- **Customizable Behavior**: Offers methods for custom actions like grabbing, releasing, and teleporting.
- **Simulator Integration**: Communicates seamlessly with the drone simulator over a UDP connection.
- **Extensive Notes Enum**: Defines musical notes for drone buzzer control, enabling creative sound outputs.

---

## Installation

1. **Download and Install Dependencies**:
   - Install Python (3.6+ is required).
   - Install the Codrone Simulator package via pip:
     ```bash
     pip install codrone-simulator
     ```

2. **Download the Drone Simulator**:
   - [Download the simulator](https://github.com/10botics/codrone-simulator) from the official repository.

3. **Set Up the Drone Simulator**:
   - Run the simulator executable.

---

## How to Use the Sample Python File

1. **Download the Sample File**:
   - Download the sample Python file from the **Releases** tab in this repository.

2. **Open the File**:
   - Open the downloaded Python file using either **VS Code** or **PyCharm**.

3. **Run the Script**:
   - Ensure the drone simulator is running before executing the script.
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