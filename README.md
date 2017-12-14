# Overview
This is a simple image classifier.

It is largely based on Google's TensorFlow code lab, which explains how to use
InceptionV3 for transferred learning.

# Quick Start
Given a dataset of images, the classifier can be trained. To train:

``
./train.sh <image_dir>
``

Given an image, the classifier can predict based on the training. To run:

``
./run.sh <img_path>
``

# How To Run
Run the image classifier for a given image:

``
python3 -m scripts.label_image --image=<imgFile>
``

Run TensorBoard in background, to see graphs and visuals for the learning process:

``
tensorboard --logdir tf_files/training_summaries &
``

``
python3 -m scripts.label_image --image=<imgFile> --graph=tf_files/retrained_graph.pb
``

You can see your TensorBoard after it's launched at http://0.0.0.0:6006

# How To Train
Set Linux environment variables:

``
IMAGE_SIZE=224
``
``
ARCHITECTURE="mobilenet_0.50_${IMAGE_SIZE}"
``


Run training script:

``
python3 -m scripts.retrain   --bottleneck_dir=tf_files/bottlenecks   --how_many_training_steps=500   --model_dir=tf_files/models/   --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}"   --output_graph=tf_files/retrained_graph.pb   --output_labels=tf_files/retrained_labels.txt   --architecture="${ARCHITECTURE}"   --image_dir=tf_files/<image_dir>
``

# Requirements
- python3 3.5.X and beyond
- tensorflow 1.4.X and beyond
