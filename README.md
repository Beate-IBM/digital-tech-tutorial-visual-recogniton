IBM Digital Tech Tutorial: Watson Visual Recognition
Build your own art expert with Visual Recognition

## Introduction
This hands on tutorial uses Watson Studio and Watson Visual Recognition to identify the artist of your favorite paintings.
![](/screenshots/intro-1.png)

## Learning objectives
After completing this tutorial you will be able to:
* Create a Visual Recognition model in Watson Studio running on IBM Cloud
* Capture images of paintings by artists such as Rubens, Renoir, van Gogh and Macke and zip them into a class (provided)
* Train a model to identify the artist of a painting
* Score the identified artist

## Prerequisites
This tutorial can be completed using an IBM Cloud Lite account.
1. Sign up for an [IBM Cloud account](https://cloud.ibm.com/registration).
2. Fill in the required information and press the „Create Account" button.
3. After you submit your registration, you will receive an e-mail from the IBM Cloud team with details about your account. In this e-mail, you will need to click the link provided to confirm your registration.
4. Now you should be able to log into [IBM Cloud](https://cloud.ibm.com/login).

## Hands on Lab - Overview

### Step 1 - Capture Images
We have created four zip files of paintings. You will use these pictures to identify the corresponding artist: Rubens, Renoir, van Gogh and Macke. These images will be used as your training set.

### Step 2 - Watson Studio
You will create a Watson Studio account and create a Visual Recognition project.

### Step 3 - Build a Visual Recognition model
You will create a Watson Visual Recognition model to identify images in several classes.

### Step 3 - Test the model
You will use sample pictures to confirm your model.

### Step 4 - Implement your model in your application
Embed your model into an application using code snippets.

## Setup Watson Studio with a new project
Watson Studio provides a suite of tools and a collaborative environment for data scientists, developers and domain experts.

### Create a Watson Studio service instance

* Open a Web browser and navigate to https://cloud.ibm.com

* Click the **Create resource** button in the upper right.
![](/screenshots/dashboard-1.png)

* In the left menu select **AI** and click on the the **Watson Studio** service tile
![](/screenshots/watson-studio-0.png)
* Select **Dallas** as region
![](/screenshots/watson-studio-1.png)
![](/screenshots/watson-studio-2.png)
* Click the **Create** button in the lower right.
* After the Watson Studio service is created, click on **Get Started** or visit Watson Studio at https://dataplatform.cloud.ibm.com/
![](/screenshots/watson-studio-getstarted.png)

### Create a new Watson Studio project
Projects are your workspace to organize your resources, such as assets like data, collaborators, and analytic tools like notebooks and models.

* Click on **Create a project**

![](/screenshots/createaproject.png)

* Select the **Create an empty project** tile

![](/screenshots/watson-studio-3.png)

* Give your project a name: **My Visual Recognition Project**
* Click on **Add** to define a Cloud Object Storage instance
![](/screenshots/object-storage-1.png)

* Create Cloud Object Storage: You will store images and training data in a Cloud Object Storage bucket
* Select the **Lite** plan 
* Click on the **Create** button and then **Confirm** to create a Cloud Object Storage instance.
* Watson Studio will spin for a few seconds while **Preparing Watson Studio** project. A new instance of Cloud Object Storage will be created.
* Click on **Refresh** on the New Project tab.
* Click on **Create** to create the new project
![](/screenshots/vr-project-1.png)
* Click on **Add to project** and select **Visual Recognition model** on the **Choose asset type** popup.
![](/screenshots/vr-project-2.png)
* Your project needs to be associated with a Watson Visual Recognition Service instance
* Click on the **here** link in the popup to Associate a Watson Visual Recognition service.
![](/screenshots/vr-project-3.png)

### Create a Watson Visual Recognition Service 
* Select the **Lite** plan 
* Select Region Dallas
* Scroll to the bottom an click on the **Create** button

* Select **Classify Images** on the **Custom Models** page

![](/screenshots/vr-project-5.png)

You are ready to set up your Project with Watson Visual Recognition. 


### Create a Visual Recognition Model
* The **Default Custom Model** name is not descriptive so let's rename it
* Click on the **pencil** icon to edit the name

*picture*

* Rename the model to **Painters**

*picture*

* Click on th **+** symbol to add a class

*picture*

* Name this class **Macke**
* Click the **Create** button

*pciture*

Add the other classes clicking on the **+** symbol again

*picture*

Upload zip files to your Watson Studio project
* Four zip files have been prepared which contain paitings by the artists
* Download the zip files here:
* macke.zip
* vangogh.zip
* renoir.zip
* rubens.zip

* Click on the **Browse** button
* An operating system native File Dialog will open
* Multi-select the four zip files **macke.zip, rubens.zip, renoir.zip, vangogh.zip**
* Upload these zip files to your Watson Studio project

*picture*

*picture*

* Drag the zip files to Custom Classes

    Grab the **renoir.zip** from the right navigation and drag it to the Coffee Bag class

*picture*
The images in the zip file will be added to the **Renoir** class

*picture*

* Repeat this for the other artists.
* This custom classifier does not contain a Negative zip file. It is recommended but not required
 
 * Train your Watson VIsual Recognition Custom Classifier

 * Click on the **Train Model** buuton
 * Wait a few (10-60) minutes for the model to train on the images

 *picture*

 * Once the model has been trained, click on the **Click here** link or the **Trained** link to view and test your model.

## Review and Test 
* Click on the **Test** tab

*Picture*

Test Watson Visual Recognition Custom Classifier with sample images

    Visit the Test Data directory and download the testdata.zip file. This zip file contains PNG and JPG images
    Unlike the training datasets, you will need to unzip the images onto your local hard drive
    Inspect a few of the breakfast images using a local image viewing utility or file browser
    These images were not part of the training set and will be used to validate the visual recognition model
    Return to the Test tab in the Watson Studio Flooding project
    There are two techniques to upload the images into the Test page
        Drag the individual images from your local file browser into the Test page
        Click on the browse link to open a file selection dialog

*picture*


    The trained custom classifier model will analyze the images
    Inspect the Confidence scores returned by the Watson Visual Recognition Custom Classifier

*picture*

## Implement Watson Visual Recognition custom model in your Applications

    You can incorporate this Watson Visual Recognition Custom Classifier model into your applications using a variety of programming languages - Java, Node, Python, Ruby, Core ML
    Click on the Implementation tab to review the Code snippets

    *picture*

Use the code snippets below to classify images against your model. For reference, the full API specification is available here

In the IBM Cloud Dashboard, search for and open your instance of Watson Visual Recognition and navigate into the Service Credentials section. Copy your apikey for use in the curl examples below.

    API endpoint

    https://gateway.watsonplatform.net/visual-recognition/api

    Authentication

    curl -u "apikey:{apikey}" "https://gateway.watsonplatform.net/visual-recognition/api/{method}"

    Classify an image (GET)

    curl -u "apikey:{apikey}" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg&version=2018-03-19&classifier_ids=CoffeeorDonuts_418020421"

    Classify an image (POST)

    curl -X POST -u "apikey:{apikey}"-F "images_file=@fruitbowl.jpg" -F "threshold=0.6" -F "classifier_ids=CoffeeorDonuts_418020421" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"

Congratulations

You have completed the Coffee or Donuts Visual Recognition Lab and have identified Coffee Bags, Coffee Mugs and yummy donuts.







