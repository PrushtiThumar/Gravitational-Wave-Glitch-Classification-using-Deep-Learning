*Overview*

Gravitational wave detectors such as the LIGO interferometers continuously record enormous amounts of data while searching for signals from astrophysical events like binary black hole mergers and neutron star collisions. However, the detectors also capture a variety of instrumental and environmental noise artifacts, commonly known as glitches.
These glitches can mimic real gravitational wave signals or contaminate the data, making accurate detection more challenging. Identifying and classifying these glitches is therefore an important step in improving the reliability of gravitational wave observations.
This project builds a deep learning pipeline to automatically classify gravitational wave glitches using spectrogram images from the Gravity Spy dataset. The model learns patterns in time–frequency representations of detector data and classifies them into different glitch categories.
The goal is to demonstrate how machine learning techniques can assist astrophysical data analysis pipelines by automating glitch identification.

*Dataset*

The project uses the Gravity Spy Gravitational Waves dataset available on Kaggle.
Gravity Spy is a citizen science project that combines machine learning and human classification to label glitches in gravitational wave detectors.
The dataset contains spectrogram images representing different glitch types observed in LIGO data.


The project follows a standard deep learning workflow for image classification.

1. Data Loading

Image paths are collected using Python’s Path and glob utilities.
The folder names are used to extract class labels.

This information is then stored in Pandas DataFrames, making it easier to work with image generators during training.

2. Data Preprocessing

Before training, images are preprocessed and normalized.

The following preprocessing steps are applied:
Image rescaling
Data normalization
Label extraction
Dataset splitting into training, validation, and testing sets
To improve model generalization, data augmentation techniques are applied.

Augmentation methods include:
Zooming
Horizontal flipping
Vertical flipping
Shearing
Width and height shifting

These techniques help the model learn more robust patterns and reduce overfitting.

3. Image Data Generators
The project uses Keras ImageDataGenerator to efficiently load images during training.
Using generators allows:
loading images dynamically from disk
memory-efficient training
automatic label encoding
This approach is especially useful when working with large image datasets.

4. Model Architecture

The classification model is built using a Convolutional Neural Network (CNN) implemented in TensorFlow/Keras.
CNNs are particularly effective for image-based tasks because they can automatically learn spatial patterns and hierarchical features.

The architecture includes:
Multiple convolutional layers for feature extraction
Batch normalization to stabilize training
Max pooling layers to reduce spatial dimensions
Dropout layers to reduce overfitting
Fully connected layers for classification
A softmax output layer for multi-class prediction
The network learns to recognize patterns in spectrogram images corresponding to different glitch types.

5. Model Training

The model is trained using:
Adam optimizer
Categorical cross-entropy loss
Accuracy as evaluation metric
Early stopping is used during training to prevent overfitting and stop training once the model stops improving.

Training performance is monitored using:
training accuracy
validation accuracy
training loss
validation loss

6. Model Evaluation

After training, the model is evaluated on the test dataset to measure its performance on unseen data.

Performance analysis includes:
classification accuracy
training and validation curves
comparison of model behavior during training
Visualization of training metrics helps understand how well the model learns and whether overfitting occurs.

*Results*

The trained CNN successfully learns to classify spectrogram images of gravitational wave glitches.
The model demonstrates that deep learning can effectively distinguish between different noise patterns in detector data, which is a key step in improving gravitational wave signal detection.

Automated glitch classification can help researchers:
clean detector data
improve gravitational wave search pipelines
reduce false detections
analyze large datasets more efficiently
