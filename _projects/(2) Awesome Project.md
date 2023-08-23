---
name: ML Deforestation Detection
tools: [Python, ML]
image: https://www.sketchappsources.com/resources/source-image/movie-badges-jurajjurik.png
description: Using ResNet 152v2 tuned for land use classification of satellite image data to detect deforestation activity in Indonesia.
---

# Monitoring Deforestation using Deep Learning with Satellite Data

#### CNN Land Classification Model and Application for the Indonesian province of Ketapang

<p>
{% include elements/button.html link="https://github.com/pauldingus/EuroSat-land-classifier/blob/main/Readme.md" text="View the Code on GitHub" %}
</p>

Monitoring and preventing tropical deforestation is key to mitigating climate change, as it accounts for 10% of global GHG emissions. Satellite data can help monitor land use changes around the world. With decreasing acquisition costs, access to satellite data has been made increasingly readily available. In this project, I demonstrate the entire data pipeline that can enable real-time deforestation monitoring via publicly available satellite data.

#### The Data

This project uses the EuroSat dataset:

{% include elements/figure.html image="images/land_use_examples.png" caption="Examples of image data in the EuroSat dataset." %}
