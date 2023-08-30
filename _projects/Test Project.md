---
name: Test Project
tools: [Python, ML, Geospatial]
image: /assets/images/land_use_examples.jpg" caption="EuroSat image data
description: Monitoring Deforestation using Deep Learning with Satellite Data
---

# Monitoring Deforestation using Deep Learning with Satellite Data

<p>
{% include elements/button.html link="https://github.com/pauldingus/EuroSat-land-classifier/blob/main/Readme.md" text="View the Code on GitHub" %}
</p>

### CNN Land Classification Model and Application for the Indonesian province of Ketapang

 Accounting for over 10% of global GHG emissions, tropical deforestationone of the major drivers of greenhouse gas emissions. Therefore, monitoring and preventing deforestation is key to mitigating climate change. Satellite image data is becomming more readily and freely accessible, making it one of the most promising methods to quickly identify and measure deforestation activity.

This project aims to demonstrate the viability of free, open-source deforestation measurement via machine learning. The goal is to develop a reliable classification model that could be applied to deforestation monitoring at a global scale, and apply it in real-world deforestation detection in Indonesia.

### Step One: Train a land classification algorithm 

#### *The data*

To build the classifier model, I used the [EuroSAT dataset](https://github.com/phelber/EuroSAT), which consists of 27,000 labeled and georeferenced images provided by the Sentinel-2 satellite. The dataset was assembled as part of a 2018 article published by Helber et al.5 The images are categorized into 10 land use classes: (a) industrial buildings (b) residential buildings, (c) annual crop (d) permanent crop (e) river (f) sea and lake (g) herbaceous vegetation (h) highway (i) pasture (j) forest.

{% include elements/figure.html image="/assets/images/land_use_examples.jpg" caption="EuroSat image data" %}

One advantage of the Eurosat dataset is that it uses [Sentinel-2 satellite image data](https://sentinel.esa.int/web/sentinel/sentinel-data-access), which is open source and freely available. This means we can test our algorithm on newly-pulled Sentinel-2 data in Indonesia.

Another advantage is the dataset's size and standard usage as a dataset for training land-use classification algorithms. However, the majority of its image data are from europe, and it includes very few forest images (and no rainforest). This means that applicability to out-of-distribution data like images of Indonesian rainforest could be a problem.

#### *Training the Model*

For this project, I built two models, both of them CNNs, as I wanted to experiment with home-grown networks as well as transfer learning.

**Custom CNN**: For the custom model, I built a 20-layer neural network (19 hidden layers), which includes 3 “sets” of layers, each with 3 convolutional layers followed by batch normalization layers. These sets of layers are each followed by a max pooling layer, decreasing the dimensions of the data, but increasing the depth (from 256, to 512, to 728). There is then one dense layer of size 1024 before the output layer. This model performed reasonably well, reaching over 88% test accuracy after only 10 epochs of training without any hyperparameter tuning.

{% include elements/figure.html image="/assets/images/Custom_CNN_Performance.png" caption="" %}

**Transfer learning with ResNet 152v2**: Transfer learning involves first downloading and instantiating an existing pre-trained neural network. We used ResNet152v2, a high-performing but relatively low-weight neural network. ResNet152v2 is a 152-layer network that makes clever use of skip-connections and other learning techniques to allow for much deeper models. Since ResNet normally expects a 224 by 224 image, I added a 64 by 64 input later, as well as a fully-connected layer and an output layer at the end. I first trained just the new input and output layers for 20 epochs at a normal learning rate to allow them to “catch up” to the rest of the weights. We then trained the entire model at a very low learning rate for another 10 epochs. This strategy is generally in line with the norms of transfer learning. The results for this method were extremely promising, reaching nearly 95% accuracy (in line with state-of-the-art research). Due to its superior performance, I elected to use this model for the remainder of our analysis.

{% include elements/figure.html image="/assets/images/Transfer_CNN_Performance.png" caption="" %}

#### *Applying the Model to New Data*


#### *Mapping Deforestation*

