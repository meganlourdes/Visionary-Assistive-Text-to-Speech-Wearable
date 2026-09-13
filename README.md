**Visionary 👓**

Visionary is a wearable assistive device designed to help visually impaired users identify and read text in their surroundings. The system uses an ESP32-CAM to capture an image, performs optical character recognition (OCR) on a connected computer, converts the detected text to speech, and plays the resulting audio back to the user.

**Overview**

Reading product labels, signs, and other printed text can be difficult for individuals with visual impairments. Visionary aims to make this information more accessible through a simple wearable system.

When the user presses a button:

The ESP32-CAM captures an image.
The image is transmitted wirelessly over Wi-Fi to a computer.
The computer processes the image using OCR to extract the visible text.
The detected text is converted into speech.
The generated audio is sent back to the wearable device.
The text is played aloud through a speaker.

This creates an end-to-end image → text → speech pipeline that allows the user to access printed information without needing to read it visually.

**System Architecture**

Button Press
     ↓
ESP32-CAM
     ↓
Image Capture
     ↓
Wi-Fi Transmission
     ↓
Python Processing
     ↓
OCR
     ↓
Text-to-Speech
     ↓
Audio Transmission
     ↓
Speaker Output
Hardware
ESP32-CAM
Camera module
Push button
Speaker
I2S audio interface
Supporting electronic components
Wearable housing / mounting hardware
Software

The system combines embedded C++ and Python to handle image acquisition, communication, OCR, and audio generation.

**ESP32**

Arduino / C++
Camera control
Push-button input
Wi-Fi communication
HTTP communication
I2S audio playback

**Computer**

Python
Image processing
EasyOCR
Text-to-speech generation
Communication with the ESP32-CAM
OCR Evaluation

The OCR system was evaluated under multiple real-world conditions, including changes in:
Lighting
Camera distance
Text orientation
Text size

A total of 258 valid trials were analyzed.

The system achieved:
49.6% exact OCR accuracy
83.7% overall task success when partially correct detections were included
128 correct detections
88 partial detections
42 incorrect detections

These results showed that even when the OCR system did not reproduce the complete text exactly, it was often able to extract enough information to provide useful feedback to the user.

**Design Considerations**

Because Visionary is intended to function as a wearable assistive device, the design required balancing several factors:
OCR accuracy
Processing latency
Wireless communication reliability
Camera positioning
Lighting conditions
Audio clarity
Wearability and user comfort

One major design decision was to perform OCR and text-to-speech processing on an external computer rather than directly on the ESP32-CAM. This provided significantly greater processing capability while allowing the wearable hardware to remain relatively lightweight.

**Limitations**

The current prototype has several limitations:
OCR performance depends on image quality and camera positioning.
Poor lighting, small text, and difficult viewing angles can reduce recognition accuracy.
Image processing currently depends on an external computer.
Wi-Fi connectivity is required for the complete processing pipeline.
The prototype would require further miniaturization and optimization for everyday use.
Future Improvements

**Future versions of Visionary could include:**

Improved OCR preprocessing and accuracy
More robust performance across lighting conditions
Faster end-to-end processing
A mobile phone application for OCR and text-to-speech processing
Private audio output through headphones or bone-conduction audio
A smaller and lighter wearable enclosure
Battery-powered operation
Greater independence from external computing hardware

Moving processing from a laptop to a smartphone or embedded edge-computing platform would be an important step toward making Visionary a fully portable assistive device.

**Acknowledgments**

Developed as part of EE 180: Wearable Systems Design at Tufts University.
