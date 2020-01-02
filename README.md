# Object_Detection_Tensorflow
This custom object detector has been created with the help of Tensorflow Object Detection API. It has been trained to detect just 3 categories of objects
•	Person
•	Bird
•	Animal
Note:
Under the ‘Animal’ category , I have taken only 3 animals into consideration i.e. dog, cat and horse (due to lack of GPU which led to increase in computational cost and quick exhaustion of memory resources).
I have used the Faster RCNN model for this custom object detector. In short the model does follow these steps:
•	A region proposal algorithm to generate “bounding boxes” or locations of possible objects in the image
•	A feature generation stage to obtain features of these objects, usually using a CNN
•	A classification layer to predict which class this object belongs to
•	A regression layer to make the coordinates of the object bounding box more precise.
Let’s expand the working of Faster RCNN model further:
•	Part 1 : Convolution layers
In this layers we train filters to extract the appropriate features from the image, for example let’s say that we are going to train those filters to extract the appropriate features for a human face, then those filters are going to learn throughout training shapes and colors that only exist in the human face. Convolution networks are generally composed of Convolution layers, pooling layers and a last component which is the fully connected layer.
•	Part 2 : Region Proposal Network (RPN)
RPN is small neural network sliding on the last feature map of the convolution layers and predict whether there is an object or not and also predict the bounding box of those objects. Instead of using selective search algorithm on the feature map to identify the region proposals, a separate network is used to predict the region proposals. The predicted region proposals are then reshaped using a RoI pooling layer which is then used to classify the image within the proposed region and predict the offset values for the bounding boxes.
•	Part 3 : Classes and Bounding Boxes prediction
Now we use another Fully connected neural networks that takes as an input the regions proposed by the RPN and predict object class (classification) and Bounding boxes (Regression). To train this architecture, we use SGD to optimize convolution layers filters, RPN weights and the last fully connected layer weights
