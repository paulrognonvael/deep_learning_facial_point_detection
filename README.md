# Facial points detection with Deep Learning

This project approaches the computer vision problem of detecting facial keypoints in an image using deep learning techniques. The training dataset consists of 7,049 96x96 gray-scale images. For each image, we're supposed learn to find the correct position (the x and y coordinates) of 15 2D keypoints, such as left_eye_center, right_eye_outer_corner, mouth_center_bottom_lip, and so on. For some of the keypoints we only have about 2,000 labels, while other keypoints have more than 7,000 labels available for training.

We start with data augmentation. We build a series of functions to alter a single image: top-down flip, rotation, change of brightness, shift. The functions alter a single image and not an entire array, so we can later randomly choose the transformation applied (instead of adding a transformed copy of the image for each possible transformation). The functions also sort the rotation angle (-12º or 12º), brightness alteration factor (0.6 or 1.2) and the shift ((-6,6), (6,-6) or (6,6)).

Our architecture is composed of 5 identical blocks, each of them made of one convolutional layer followed by a max pooling layer. The size of the kernels is identical across all convolutional layers at (3,3). The pool size is also identical across all max pooling layers at (2,2). Activation function used is ReLU. We have two dropout layers with dropout rate 0.5 after the second block and after the fourth block. 

Mean pixel error on test set:  1.3610508
