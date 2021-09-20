# Project1-Software-EC601
Self-supervision for graph data structures  
Study the problem of large data and visual graphs. Experiment with self-supervised models to find relationship between data to display and predict.  
# 1. Introduction to self-supervision
## 1.1 What is self-supervision
Self-supervised learning is a subset of unsupervised learning methods. Self-supervised learning refers to learning methods in which ConvNets are explicitly trained with automatically generated labels. This review only focuses on self-supervised learning methods for visual feature learning with ConvNets in which the features can be transferred to multiple different computer vision tasks.  
## 1.2 Why it is important?
To train deep neural networks, large-scale labeled data are generally required in order to obtain better performance in visual feature learning from images or videos for computer vision applications. To avoid extensive cost of collecting and annotating large-scale datasets, as a subset of unsupervised learning methods, self-supervised learning methods are proposed to learn general image and video features from large-scale unlabeled data without using any human-annotated labels.   
## 1.3 How does it work?--Pretext tasks
To learn visual features from unlabeled data, a popular solution is to propose various pretext tasks for networks to solve, while the networks can be trained by learning objective functions of the pretext tasks and the features are learned through this process. Various pretext tasks have been proposed for self-supervised learning including colorizing grayscale images, image inpainting, image jigsaw puzzle, etc. The pretext tasks share two common properties: (1) visual features of images or videos need to be captured by ConvNets to solve the pretext tasks, (2) pseudo labels for the pretext task can be automatically generated based on the attributes of images or videos.  
![image](https://user-images.githubusercontent.com/78338843/133964841-db670b87-a971-44fb-8ef8-f240d3647edb.png)
During the self-supervised training phase, a pre-defined pretext task is designed for ConvNets to solve, and the pseudo labels for the pretext task are automatically generated based on some attributes of data. Then the ConvNet is trained to learn object functions of the pretext task. After the self-supervised training finished, the learned visual features can be further transferred to downstream tasks (especially when only relatively small data available) as pretrained models to improve performance and overcome over-fitting. Generally, shallow layers capture general low-level features like edges, corners, and textures while deeper layers capture task related high-level features. Therefore, visual features from only the first several layers are transferred during the supervised downstream task training phase.  
# 2. Applications
## 2.1 Colorful Image Colorization
This paper propose a fully automatic approach that produces vibrant and realistic colorizations. They embrace the underlying uncertainty of the problem by posing it as a classification task and use class-rebalancing at training time to increase the diversity of colors in the result. The system is implemented as a feed-forward pass in a CNN at test time and is trained on over a million color images. 
![image](https://user-images.githubusercontent.com/78338843/133965037-995df868-68d0-40bf-bd68-613914c4319a.png)
## 2.2 Placing image patches in the right place
In this paper they study the problem of image representation learning without human annotation. By following the principles of self-supervision, they build a convolutional neural network (CNN) that can be trained to solve Jigsaw puzzles as a pretext task, which requires no manual labeling, and then later repurposed to solve object classification and detection. To maintain the compatibility across tasks they introduce the context-free network (CFN), a siamese-ennead CNN. The CFN takes image tiles as input and explicitly limits the receptive field (or context) of its early processing units to one tile at a time.
![image](https://user-images.githubusercontent.com/78338843/133965605-8abb1179-9df6-4d98-b851-706738b40943.png)
## 2.3 Placing frames in the right order
This project validate the effectiveness of the learned representation using our method as pre-training on high-level recognition problems. The experimental results show that our method compares favorably against state-of-the-art methods on action recognition, image classification and object detection tasks.
![image](https://user-images.githubusercontent.com/78338843/133966077-857bf040-9b29-4193-9829-a296198ba80f.png)
