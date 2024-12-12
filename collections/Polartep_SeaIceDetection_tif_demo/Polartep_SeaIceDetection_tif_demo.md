## Caveat
The data shown here are to demonstrate the use of machine learning in 
Polar TEP and are not to be used for navigational purposes.

## Background

Manual ice charting from multi-sensor satellite data analysis has for many 
years been the primary method at the National Ice Services for producing 
sea ice information for marine safety. Ice analysts primarily use satellite 
synthetic aperture radar (SAR) imagery due to the high spatial resolution 
and the capability to image the surface through clouds and in polar 
darkness, but also optical imagery in clear sky and daylight conditions, 
thermal-infrared and microwave radiometer data from e.g. AMSR2. Ice 
analysts mention the coarse spatial resolution of microwave radiometers as 
the primary limitation to the use of the data.

The traditional manual ice charting method is time-consuming and limited 
in spatial and temporal coverage. Further, it is challenged by an increasing 
amount of available satellite imagery, along with a growing number of users
accessing wider parts of the Arctic due to the thinning of the Arctic sea ice.

The automation of the time-consuming and labor-intensive sea ice charting 
process has the potential to provide users with near-real-time sea ice 
products of higher spatial resolution, larger spatial and temporal coverage, 
and increased consistency.

![Examples of variables in the dataset](https://raw.githubusercontent.com/gtif-cerulean/assets/main/collections/Polartep_SeaIceDetection_tif_demo/examples.png "Examples of variables in the dataset")

* Top left: Sentinel-1 SAR image HH polarization with NERSC noise correction applied.
* Top right: Sentinel-1 SAR image HV polarization with NERSC noise correction applied.
* Bottom right: AMSR2 brightness temperatures in the 89GHz channel.
* Bottom left: Example of the label (ice chart) data (colour scheme corresponding to the polygon ID numbers and not, e.g., ice concentration).

## Machine Learning Model

Convolutional Neural Networks (CNN) have great potential to help 
automate the interpretation of sea ice in satellite images. In the example 
used here, a CNN model based on U-Net has been employed.

U-Net has a near-symmetric encoder–decoder structure in which the 
contracting path captures rich low-level representations while the 
expanding path enables precise localization. Skip-connections are used 
between corresponding pairs of encoder and decoder blocks to propagate 
information from the contracting path to the expanding path. This facilitates
the recovery of high-frequency spatial information and improves the 
boundary accuracy. In the U-Net architecture, a block constitutes a 
sequence of two 3×3 convolutional layers, each followed by a batch 
normalization (BN) procedure and the rectified linear unit (ReLU) activation
function. In the contracting path, 2×2 max-pooling operations are used for 
feature map downsampling. Similarly, in the expanding path, every block is 
preceded by a bilinear upsampling operation. Each symmetric encoder and 
decoder block with a skip connection between them is defined here as a 
level. A schematic overview of a regular four-level U-Net architecture is 
shown in Fig. 1. The original U-Net in [1] uses the identical number of 
filters in the convolutional layers across the same level and doubles them 
for each level, i.e., 64, 128, 256, and 512. Here, we utilise 8 levels and limit 
the number of filters to 32 in the initial and final levels, and 64 in the other 
levels. The U-Net implementation is available at [2].

![Schematic overview of a four-level U-Net architecture](https://raw.githubusercontent.com/gtif-cerulean/assets/main/collections/Polartep_SeaIceDetection_tif_demo/model_schema.png "Schematic overview of a four-level U-Net architecture")

### References
[1] O. Ronneberger, P. Fischer and T. Brox, "U-Net: Convolutional networks for biomedical image segmentation", Proc. Int. Conf. Med. Image Comput. Comput.-Assist. Intervent., pp. 234-241, Oct. 2015.               
[2] A. Stokholm and A. Kucik, U-Net model PyTorch implementation, 2021, [online] Available: https://github.com/astokholm/AI4SeaIce.git.

## Training Data

Automating the process on SAR data alone is challenging. SAR images show
patterns related to ice formations, but backscatter intensities can be 
ambiguous, complicating the discrimination between ice and open water, 
e.g. at high wind speeds. To tackle the challenges, the training dataset used 
contains both Sentinel-1 active microwave data and corresponding 
Microwave Radiometer (MWR) data from AMSR2. While SAR data has 
ambiguities, it has a high spatial resolution, whereas MWR data has good 
contrast between open water and ice. However, the coarse resolution of the 
AMSR2 MWR observations introduces a new set of obstacles, e.g. land spill-
over, which can lead to erroneous sea ice predictions along the coastline 
adjacent to open water. Label data in the datasets are ice charts produced 
by the Greenland ice service at the Danish Meteorological Institute (DMI) 
and the Canadian Ice Service (CIS).

![Overview of the coverage of Sentinel-1 SAR scenes included in the training data](https://raw.githubusercontent.com/gtif-cerulean/assets/main/collections/Polartep_SeaIceDetection_tif_demo/overview.png "Overview of the coverage of Sentinel-1 SAR scenes included in the training data")

* (brighter color means higher data density, i.e. satellite coverage). The texts on the map refer to the names of ice charting regions used by CIS and DMI

## Model Results

When presented with corresponding Sentinel 1 and AMSR 2 satellite 
images, the model calculates three sea ice parameters:

* Sea ice concentration: expressed as 11 classes, from open water (0/10ths) to ice covered (10/10ths).
* Stage-of-development: expressed as six classes (Ice Free, New Ice, Young ice, Thin First-year ice, Thick First-year ice, Old ice).
* Floe size: expressed as seven classes (Ice Free, Ice cakes, Small floes, Medium floes, Big floes, Vast & Giant floes, Icebergs & Growlers).
