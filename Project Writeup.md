# Project overview
This project is for practicing 2D object detection in an urban environment. A dataset of images from Waymo is provided for this project. The target is to identify 3 classes of objects –cyclists, pedestrians, and vehicles, with a pre-trained deep learning algorithm.

The main purpose of object detection for self-driving vehicles (SDV) is to locate and classify objects in the vehicle's surrounding. This is a vital task for the safe operation of an SDV, allowing it to "see" other actors in its environment. Only if this is achieved, safe maneuvers can be planned and executed.

# Set up
I completed the project in the project workspace provided by Udacity. The workspace had all of the necessary libraries and data provided.

# Dataset
## Dataset Analysis
The implementation and original images for the exploratory analysis of our dataset can be found in the [Exploratory Data Analysis](https://github.com/jiangnan2341/UdacitySDCE_P1/blob/main/Exploratory%20Data%20Analysis.ipynb) notebook.

The class distribution in our dataset is highly imbalanced. There are a lot of vehicles, as opposed to lesser pedestrians and almost no bicycles. Model performance (average precision, recall etc.) should thus be monitored closely especially for the minority classes. In order to avoid poor performance of the object detection for the minority class, one could adopt multitude of strategies such as data augmentation for the underrepresented class.

The total occurence and proportion of the different object types is very heterogenuous across images. There are images with vehicles only (e.g. on a highway), while there are others with more pedestrians than vehicles (e.g. on a crossroad).

Light conditions vary heavily across the dataset, with sunny conditions (leading to bright images with high contrast) as well as rainy/foggy conditions (causing reflections and blurs in the images) alike. Also, there are recordings of night drives.
Image distortions can be observed as well, especially on the image edges.
In images with multiple objects, objects tend to be clustered and occlude each other.

The class distribution and the light condition distribution are illustrated in diagrams below:
![](class_pie.png)
![](brightness_EDA.png)

## Cross-validation
The creation of training vs. validation split, which is usually performed based on the exploratory analysis, was already done in the workspace, with 87 : 10 TFRecords in the training and validation set, respectively. This corresponds to a 90% : 10% split, which is common practice.
# Training
## Reference experiment
The results yielded by the first reference run with the pretrained model were surprisingly bad. As the training steps increase, all loss values flutuated a lot from the very beginning and even worse, the normalization, regularization and total loss values jumped to an unbelievably high value toward the end of the default 2500 steps. Within the default 2500 steps, from the tensorboard diagrams, I don't see any good trend. 
![](experiments/reference/Reference1.png)
I didn't bother to try evaluation with this bad training result and figured that maybe I can get a better training result with increased steps. Based on mentor's answer to someone else's questions, I increased the number of steps to 5000.
This time, the yielded results were still not optimal but looked much better and similar to what is demonstrated in the project instructions. The loss values still fluctuated a lot, but at least there is clear descrease trend shown in the captured tensorboard diagrams. From the diagrams, I can see that even within the 25000 steps, the loss values during the training process were not as bad as the first trial. I'm guessing maybe the first trial was so bad because the chosen data happened to be extremely bad? 
![](experiments/reference1/Reference5000steps1.png)
Looking at the evaluation metrics, we can observe that the average precision and recall values are all very low (for a IoU threshold of 0.5) and that hence the model does not yet perform well on a new dataset.
## Improve on the reference
