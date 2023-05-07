# Object-Detection-with-Voice-Feedback-using-Raspberry-Pi-4-and-Bullseye-OS.

## Introduction
In this Project, I teach you how to set up the TensorFlow Lite and Voice Feedback on the Raspberry Pi 4 using latest Bulleye OS (Debian version: 11) and use it to run object detection models with voice feedback. In this work, I will use the Raspberry Pi 3 and 4 running either Bulleye OS or latest Debian 64 bit version supported.(Raspbian OS Repo Link: https://www.raspberrypi.com/software/operating-systems/).

## Lesson 1 - How to Set Up TensorFlow Lite on the Raspberry Pi

### Step 1. Check Python Version in Raspberry Pi
In this tutorial Tensorflow Lite installation currently supported python version is 3.5, 3.6, 3.7, 3.8 & 3.9(above)..
```
python3 --version
```
### Step 2. Update the Raspberry Pi

```
sudo apt update
```
```
sudo apt install rpi-update
```
### Step 3. Download & Unzip My Github Repository

clone My GitHub repository

```
git clone https://github.com/thyagarajank/Object-Detection-with-Voice-Feedback-using-Raspberry-Pi-4-and-bullseye-OS.git
```

Unzip the Folder "Object-Detection-with-Voice-Feedback-using-Raspberry-Pi-and-Tensorflow-Lite". Move the all files to "tflite1" folder.

```
uzip Object-Detection-with-Voice-Feedback-using-Raspberry-Pi-4-and-bullseye-OS
```
### Step 4. Create New Directory
Create New Dir at (/home/pi/)
```
mkdir tflite1
```
Copy all Files to "tflite1"
```
cp -r Object-Detection-with-Voice-Feedback-using-Raspberry-Pi-4-and-bullseye-OS/* tflite1/
```
Work in this "/home/pi/tflite1" directory.
```
cd /home/pi/tflite1
pwd
```
### Step 5. Create a Virtual Environment called "tflite1-env".
Intall Virtualenv
```
sudo pip3 install virtualenv
```
Create the "tflite-env" Virtual Environment
```
python3 -m venv tflite1-env
```
Activate Virtual Environment
```
source tflite1-env/bin/activate
```
### Step 6. Install TensorFlow Lite & Other Dependencies.
OpenCV  required packages and other libraries mention in .sh (shell) script. it will automatically download and installed.
```
cd rpi-bullseye-opencv4.5.5/
```
Run shell script(Installing OpenCV 4.6.0 and the dependencies on your Raspberry Pi 64-bit OS) It will take minimal 2.0 hour !
```
bash install.sh 
```
```
cd ..
```
Install TensorFlow Lite Runtime.
```
sudo apt-get install python3-tflite-runtime
```
Install Opencv-python.
```
pip3 install opencv-python
```
Install shell script TFlite and Packages
```
cd tensorflow-lite-bullseye/
```
Install Tensorflow-lite.sh
```
bash tensorflow-lite.sh 
```
```
python3 -m pip install tflite-runtime
```
Install Tensorflow Lite 2.5.0(tflite_runtime-2.5.0.post1-cp39-cp39-linux_armv7l.whl)
```
pip3 install https://github.com/google-coral/pycoral/releases/download/v2.0.0/tflite_runtime-2.5.0.post1-cp39-cp39-linux_armv7l.whl
```

### Step 7. Download Google's sample TFLite model
coco_ssd_mobilenet_v1_1.0_quant_2018_06_29 object detection model run on TensorFlow Lite
```
wget https://storage.googleapis.com/download.tensorflow.org/models/tflite/coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip
```
Unzip the download folder.
```
unzip coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip -d Sample_TFLite_model
```
**NOTE: If use own custom detection model.
Do not Download Google's SSDLite-MobileNet-v2 object detection model(step 7).
Copy your own custom Model File to Sample_TFLite_model.**

## Lesson 2 - Run Object Detection in TensorFlow Lite 
**Checklist**
- 1. Setup your webcam or Picamera plugged in  
- 2. Enabled camera interface in Raspberry Pi
     (Click the raspberry icon in the top left corner of the screen, select--> Preferences --> Raspberry Pi Configuration, and go to the Interfaces tab and verify Camera is set      to Enabled. After reboot the Raspberry Pi.)
- 3.   Closing applications you aren't using and free up memory. 
- 4.  Before running the command, make sure the tflite1-env environment is active. (tflite1-env) appears in front of the terminial.
This command for run  object detection model only.
### Step 8. Run the TensorFlow Lite Object Detection Model Only
Webcam Image object Detection Python Program.
```
python3 object_only_webcam.py --modeldir=Sample_TFLite_model
```
### Step 9. Install Text to Speech Packages.
- 1. pyttx3  
- 2. espeak
Intall "pyttsx3" Text to Speech (TTS) library for Python 2 and 3
```
pip install pyttsx3
```
Install espeak library
```
sudo apt-get install espeak
```
### Issue in install espeak Package
Try this 2 Command
```
sudo apt update && sudo apt install rpi-update
```
```
sudo apt-get install python-espeak
```
### Step 10. Run the TensorFlow Lite Object Detection Model with Voice Feedback.
This Python Program for run object detection with voice feedback.
```
python3 object_voice_webcam.py --modeldir=Sample_TFLite_model
```
## Lesson 3 - Train own Custom Object Detection Model
https://github.com/thyagarajank/tensorflow-own-custom-object-detection-model-in-google-colab
Tensorflow (.pb file) Custom Model Training In colab (Code Availble in My Github).
Tensorflow(.pb) file to Tensorflow Lite (.tflite) file Convertion Program (Upload Soon).

