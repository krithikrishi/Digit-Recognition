#  Real-Time Handwritten 

This project uses a webcam (via OpenCV) and a neural network (via TensorFlow/Keras) to recognize handwritten digits held up to the camera in real-time.

It's an interactive application that combines computer vision with deep learning. A model is first trained on the classic MNIST dataset, and then that model is used to make live predictions on pre-processed frames from your webcam.

##  Features

Real-Time Inference: Uses OpenCV to capture your webcam feed and run predictions live.
Simple UI:
Click the video window to start/stop the recognition.
A "threshold" slider allows you to adjust the image binarization in real-time to improve detection.
A white box shows the Region of Interest (ROI) where the model is "looking".
CNN Model: A Keras/TensorFlow model trained on the MNIST dataset.
Model Persistence: The script automatically saves the trained model as model.keras after the first run, so it loads instantly on future uses.
##  How It Works

1.  Model Training (First Run Only):

The script first checks if model.keras exists.
If not, it downloads the MNIST dataset.
It trains a simple neural network (Flatten -> Dense(512, relu) -> Dense(10, softmax)).
The trained model is saved to disk. 2.  Webcam & CV:
OpenCV launches the primary webcam.
A mouse callback is set: clicking the window toggles inference on/off.
A trackbar is created to control the image threshold value. 3.  Live Inference (When Toggled On):
The video feed is converted to grayscale.
A binary threshold is applied to create a stark black-and-white image, similar to the MNIST data.
A 150x150 pixel box is cropped from the center of the frame.
This cropped image is resized down to 28x28 pixels to match the MNIST model's input shape.
The 28x28 image is fed into the model.predict().
The predicted digit (the one with the highest probability) is displayed on the screen.
##  Technologies Used

Python 3
TensorFlow (Keras) for building and training the model.
OpenCV (cv2) for all webcam capture, image processing, and UI (windows, sliders).
NumPy for numerical operations and image array manipulation.
Matplotlib / PIL (used in imports, though not heavily in the main loop).
##  How to Run

1.  Clone the Repository:

git clone github.com/krithikrishi/Digit-Recognition
cd Digit-Recognition
2.  Install Dependencies: It's highly recommended to install and add these to the project environment.

tensorflow
opencv-python
numpy
matplotlib
Pillow
3.  Run the Script:

python project.py
4.  Using the App:

A window will open showing your webcam feed.
Click the window to start recognition. A white box and predicted digit will appear.
Hold a white piece of paper with a black digit (like from a marker) inside the box.
Adjust the "threshold" slider until the digit is clearly visible and the background is black.
Click the window again to stop recognition.
# Digit-Recognition
