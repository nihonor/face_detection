# Face Tracking System

A real-time face tracking system that uses a webcam to detect faces and controls a stepper motor to follow the movement of detected faces. The system consists of a Python application for face detection and an Arduino sketch for motor control.

## Features

- Real-time face detection using OpenCV's Haar Cascade classifier
- Smooth panning motion with a 28BYJ-48 stepper motor
- Adjustable tracking parameters (sensitivity, deadzone, etc.)
- Visual feedback with face bounding boxes and center point
- Configurable serial communication with Arduino

## Hardware Requirements

- Webcam
- Arduino board (Uno, Nano, etc.)
- 28BYJ-48 stepper motor with ULN2003 driver board
- Jumper wires
- 5V power supply for the stepper motor

## Software Dependencies

### Python Dependencies
- Python 3.6+
- OpenCV (`pip install opencv-python`)
- PySerial (`pip install pyserial`)

### Arduino Dependencies
- Arduino IDE
- No additional libraries required

## Setup Instructions

1. **Hardware Setup**
   - Connect the ULN2003 driver board to your Arduino:
     - IN1 -> Pin 8
     - IN2 -> Pin 9
     - IN3 -> Pin 10
     - IN4 -> Pin 11
   - Connect the stepper motor to the driver board
   - Provide 5V power to the driver board

2. **Upload Arduino Sketch**
   - Open `face.ino` in Arduino IDE
   - Select the correct board and port
   - Upload the sketch to your Arduino

3. **Configure Python Script**
   - Edit `python.py` and update the serial port to match your Arduino's port:
     ```python
     ser = serial.Serial('COM17', 9600, timeout=1)  # Change 'COM17' to your port
     ```

## Usage

1. Make sure the Arduino is connected and the sketch is running
2. Run the Python script:
   ```
   python python.py
   ```
3. A window will open showing the webcam feed with face detection
4. The stepper motor will automatically track detected faces
5. Press 'q' to exit the application

## Configuration

You can adjust the following parameters in `python.py`:
- `KP`: Proportional gain for smoother/faster tracking
- `DEADZONE`: Pixel offset before the motor moves (larger = less sensitive)
- `MIN_ANGLE`/`MAX_ANGLE`: Physical limits for the stepper motor (30° to 150° by default)

## Troubleshooting

- **No face detection**: Ensure good lighting and that your face is clearly visible to the camera
- **Stepper motor not moving**: Check connections and power supply
- **Serial port errors**: Verify the correct COM port is specified in the Python script

## License

This project is open source and available under the MIT License.

## Acknowledgments

- Uses OpenCV's Haar Cascade classifier for face detection
- Arduino code based on standard stepper motor control patterns                                                                                     
