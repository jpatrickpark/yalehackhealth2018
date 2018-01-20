# Welcome to the Yale Hackathon 2018

This repository can be used as a starting point for challenges #1 or #2 as published in [here.](http://www.yalehackhealth.org)

### About Butterfly Network

Butterfly Network has taken advantage of an intersection of new technologies, from deep learning to cloud technology, to create an ultrasound platform that is affordable and accessible to everyone. By replacing the piezoelectric crystals traditionally used to generate ultrasound with semiconductor technology Butterfly has exponentially lowered the the cost of this life-saving technology. This new approach has also produced the first transducer that can image the entire body, making exams faster and more efficient.

To build out this vision, we need exceptional talent that is passionate about our mission. Thank you for being a part of this event!

### The Butterfly Network ultrasound dataset

The ultrasound dataset can be download directly using the following links:
[Set 1](https://github.com/ButterflyNetwork/YaleHackathon2018/releases/download/v.0.0.1/butterfly_dataset_test.tar.gz)
[Set 1](https://github.com/ButterflyNetwork/YaleHackathon2018/releases/download/v.0.0.1/butterfly_dataset_training1.tar.gz)
[Set 3](https://github.com/ButterflyNetwork/YaleHackathon2018/releases/download/v.0.0.1/butterfly_dataset_training2.tar.gz)

A mini-version (a small subset) of the dataset is available [here](https://github.com/ButterflyNetwork/YaleHackathon2018/releases/download/v.0.0.1/butterfly_mini_dataset.tar.gz).

These images have been published by Butterfly Network Inc. for the Yale Hackathon 2018. They may be used for non-commercial research purposes, but they may not be re-published without the express permission of Butterfly Network Inc.

You will be provided with 2 ultrasound datasets.
The large dataset (butterfly_dataset) contains 9 different classes of ultrasound images acquired with the Butterfly IQ on 31 individuals.
The smaller subset of this dataset is called butterfly_mini_dataset. Each of the classes is acquired on a different part of the body.

The 9 types of ultrasound images are:
- Morison's pouch
- Bladder
- PLAX view of the heart
- 4 chambers of the heart
- 2 chambers of the heart
- IVC
- Carotid artery
- Lungs
- Thyroid

The folder containing the data has already split the data into a training and test set.
Each set contains enumerated folders representing different patients. 
Each patient contains at most 9 folders corresponding to the class/type of ultrasound images.
The following is a diagram representing the folder structure containing the dataset.

```
butterfly_dataset
├── training
│   ├── 1
│	│   └── morisons_pouch
│	│	│   └── img001.png
│	│	│   └── img002.png
│	│	│   └── img003.png
│	│	│   └── ....
│	│   └── bladder
│	│   └── plax
│	│   └── 4ch
│	│   └── 2ch
│	│   └── ...
│   ├── 2
│   └── ...
├── test
│   ├── 26
│   ├── 27
│   └── ...
```

### Reference and starting point

We provide a code that can be used as a reference, or as a starting point for the challenges.
You are not obligated to use the code or the approach taken there.
This starting point example shows how to train the well-known InceptionV1 model and how then use it to classify ultrasound images.
A utility function to download the datasets is also provided.

#### Installing and running the example

We assume you have git installed on your machine and python 3.5. If you don't, hack your way through the installation of these two popular tools.

The first thing you want to do is to clone this repository. In order to do this, invoke the following commands:

```
git clone https://github.com/ButterflyNetwork/YaleHackathon2018.git
cd YaleHackathon2018
```

To verify that you actually have python 3 available from within YaleHackathon2018 folder, simply invoke the command:

```
python --version
``` 
You should expect to see a version 3.x.x. We recommend you use 3.5, but the code probably will work with any version of python 3.

To install the libraries used in the example, simply invoke the following command from within the `YaleHackathon2018` folder.

```
pip install -r requirements.txt
```

Now you are ready to run the example.
The example exposes 3 main methods:
1. download_dataset
2. train
3. evaluate

To download the mini dataset you can invoke the command:

```
python hackathon_example.py download_dataset
```

To train the model you can invoke the following command for example:

```
python hackathon_example.py train --input_file=butterfly_mini_dataset/training/training.csv  --export_dir=models --number_of_epochs=4
```

After training you can evaluate the saved model on the test set by invoking the following command for example:
```
python hackathon_example.py evaluate --input_file=butterfly_mini_dataset/test/test.csv  --export_dir=models
```
