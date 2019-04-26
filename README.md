# Object-Localization
Our submitted model for Flipkart GRID Teach The Machines online competition. 

## Approach
We started by implementing a data loader which picks images of batch size 32, loads these images to the VRAM and pre-processing them by normalizing the images across RGB channels at every step. Also the image resolution of these images were changed from 640*480 to 480*480.

### Metric and Loss function
We used the IOU metric as specified by the problem statement and smooth L1 loss function.

### Architecture
We used ResNet-18 architecture with a final fully connected layer having 4 outputs and regularized it using L2 regularizer. Swish activation function was used. We used Adam optimizer for the first 35 epochs and then we switched to Adadelta optimizer and ran the saved model for another 40 epochs until we reached training loss and validation loss of 18.2336 and 20.2420 respectively. We used a learning rate scheduler that started with a learning rate of 1e-3 for 20 epochs, 1e-4 for 15 epochs and finally 1e-5 for 5 epochs.  
