Paper: [An embedded system for the automated generation of labeled plant images to enable machine learning applications in agriculture](https://arxiv.org/pdf/2006.01228.pdf)

M.A. Becka, C.-Y. Liu, C.P. Bidinosti, C.J. Henry, C.M. Godee, M. Ajmani

**2020** | **arxiv** | **Submitted to: PLoS One**

# Overview

The authors propose a more efficient/automated data collection and labelling method that uses a 3-axis gantry robot to collect images from weed seedlings at different angles and heights. A blue background and pot colour enables rapid background subtraction and plant labeling. 34,666 sub-images were generated of the weeds below in 10 runs, for a total run time of 47h30.

The main contributions of the paper are:

1. Imaging system for labeled datasets
2. High imaging rate of the system
3. Any angle/distance automated imaging
4. Diverse plant types possible for imaging, large imaging area
5. CNN model evaluated on the data

### Technical Details

* Camera: GoPro Here 7 Black
* Nema 24, 2.7 Nm torque steppers per axis
* ATMega controller
* Pan tilt servos - Dynamixel

#### Labelling

Images were labelled with a geometric approach - the location of each plant within the image was recorded based on relative position to the camera. It is robust - does not rely on ML accuracy or an image processing pipeline.

#### Weeds

8 weed species relevant to Manitoban fields were used:

* Barnyardgrass (*Echinochloa crus-galli*)
* Canada thistle (*Cirsium arvense*)
* Canola (*Brassica napus*)
* Dandelion (*Taraxacum officinale*)
* Smartweed (*Persicaria spp.*)
* Wild buckwheat (*Fallopia convolvulus*)
* Wild oat (*Avena fatua*)
* Yellow foxtail (*Setaria pumila*)

### Trained CNN

The authors trained a resnet-50 on the dataset achieving 99.71% accuracy after 50 epochs - the validation accuracy quickly flatlined - possible indication of low variability in the dataset and overfitting. The key findings from adjusting training scenarios:

1.  When tested on unseen plants of same collection time model performed well (98.37) - indicated it could generalise
2. Using randomised camera angles and distances: no significant impact on the model's overall accuracy suggesting the variety of angles included in the datasets was sufficient.
3. Under new imaging conditons using a smart phone on a neutral background the accuracy remained high at 89%.
4. The model did not perform as well on other field collected datasets - but had reasonable accuracy between 63% and 81.56%, however, these conditions and images are very different

### Conclusions and Future Work

The system performed as designed and automatically captured and labelled a large dataset, each image require approximately 4.7 seconds. There are areas of improvement suggested:

1. Adding progammable LED lighting
2. Gantry size: limits the size and number of plants that can be imaged. One option is to mount it inside large growth chambers.
3. Develop 3D plant data using stereogammetry or adding 3D scanners/LIDAR
4. Capture images of plant organs

The data has been made publicly available with the authors producing datasets on wheat, canola, soybean and pulses. The current data is available [here](https://doi.org/10.5061/dryad.gtht76hhz) (though not yet uploaded 10/06)

