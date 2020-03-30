# Fluid channel modeling

This repository contains files for Python-based modeling of void fraction in microfluidic channels. Here is a description of the worklow:
1. Image data is stored inside the *\data* directory.
2. The Python notebook *channel_modeling.ipynb* is run, which crops the images in the *\data* directory to remove regions outside the channel area.
3. The trimmed image data is saved to a Python dictionary in the numpy file called *trimmed_images.npy*.
4. The Python notebook *channel_modeling.ipynb* then reads in the saved images from *trimmed_images.npy* and performs Monte Carlo modeling of possible bubble configurations inside the channel to attempt to reconstruct the measured images.
5. Basic parameters of the model are saved to the *model_parameters.npy* file as a Python dictionary.
5. The individual channel models created by *channel_modeling.ipynb* are saved as Python dictionaries in the *\models* directory.
6. The Python notebook *model_visualization.ipynb* is used to open each model from file and plot statistics about the model. The notebook *model_visualization.ipynb* also reads model parameters from the *model_parameters.npy* file.


The modeling results are saved and read from file so that any step in the workflow can be executed without restarting the entire process. This is imporant since constructing the actual channel models can take up to two hours for the entire image list.


Each model in the *\models* directory is a Python dictionary saved as a numpy *.npy* binary file, which contains the following information:
* **label**: (filename) of the original channel image
* **img_model**: simulated channel image
* **img_voidfrac**: measured void fraction image
* **cent**: the centers of the simulated bubbles, in ordered pairs (x, y)
* **rad**: the radii of the simulated bubbles
* **percent_error**: total percent error between the measured channel image and the simulated channel image


## Description of files

## Examples
Shown below is an example of void fraction images and simulated model images.
![Example of channel images and models](./img/example_models.JPG)

Shown below are plots of model statistics which summarize bubble populations.
![Example of bubble statistics](./img/stats.JPG)