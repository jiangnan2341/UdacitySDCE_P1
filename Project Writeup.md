# Project overview
This project is for practicing 2D object detection in an urban environment. A dataset of images from Waymo is provided for this project. The target is to identify 3 classes of objects –cyclists, pedestrians, and vehicles, with a pre-trained deep learning algorithm.

The main purpose of object detection for self-driving vehicles (SDV) is to locate and classify objects in the vehicle's surrounding. This is a vital task for the safe operation of an SDV, allowing it to "see" other actors in its environment. Only if this is achieved, safe maneuvers can be planned and executed.

# Set up
I completed the project in the project workspace provided by Udacity. The workspace had all of the necessary libraries and data provided.

# Dataset
## Dataset Analysis
The implementation and original images for the exploratory analysis of our dataset can be found in the [Exploratory Data Analysis](Exploratory+Data+Analysis.ipynb) notebook.

At first glance, it becomes obvious that the class distribution in our dataset is highly imbalanced. There are a lot of vehicles, as opposed to lesser pedestrians and almost no bicycles. Model performance (average precision, recall etc.) should thus be monitored closely especially for the minority classes. In order to avoid poor performance of the object detection for the minority class, one could adopt multitude of strategies such as data augmentation for the underrepresented class.
Further proposals, such as adapting the performance metrics, can be found here.
The total occurence and proportion of the different object types is very heterogenuous across images. There are images with vehicles only (e.g. on a highway), while there are others with more pedestrians than vehicles (e.g. on a crossroad).
Light conditions vary heavily across the dataset, with sunny conditions (leading to bright images with high contrast) as well as rainy/foggy conditions (causing reflections and blurs in the images) alike. Also, there are recordings of night drives.
Image distortions can be observed as well, especially on the image edges.
In images with multiple objects, objects tend to be clustered and occlude each other.
## Cross-validation

# Training
## Reference experiment
## Improve on the reference
